# How to Install, Configure, and Verify a Managed Internal Ingress Controller in AKS

This manual provides a step-by-step guide for setting up a **managed internal ingress controller** in Azure Kubernetes Service (AKS) using the Application Routing addon. An internal ingress controller exposes services using a private IP address within your virtual network (VNET), making it ideal for private applications.

## Table of Contents
1.  [Prerequisites](#1-prerequisites)
2.  [Install the Internal Managed Ingress Controller](#2-install-the-internal-managed-ingress-controller)
3.  [Deploy a Sample Application](#3-deploy-a-sample-application)
4.  [Configure the Internal Ingress Resource](#4-configure-the-internal-ingress-resource)
5.  [Configure Private DNS for Resolution](#5-configure-private-dns-for-resolution)
6.  [Verify the Ingress Controller](#6-verify-the-ingress-controller)
7.  [Cleanup Resources](#7-cleanup-resources)

---

### 1. Prerequisites

*   An existing AKS cluster.
*   Azure CLI installed and configured.
*   `kubectl` installed and configured to connect to your AKS cluster.
*   A Virtual Network (VNET) that your AKS cluster is connected to.

### 2. Install the Internal Managed Ingress Controller

The managed ingress controller is enabled via the **Application Routing addon**. To make it internal, we configure it to create an Azure Internal Load Balancer.

1.  **Enable the Application Routing Addon:**

    Use the `az aks approuting enable` command. This command will set up all the necessary NGINX ingress controller resources inside your cluster.

    ```bash
    # Replace with your resource group and cluster name
    RESOURCE_GROUP="myResourceGroup"
    CLUSTER_NAME="myAKSCluster"

    az aks approuting enable \
        --resource-group $RESOURCE_GROUP \
        --name $CLUSTER_NAME
    ```

2.  **Update the Ingress Controller Service to be Internal:**

    By default, the addon creates a public-facing load balancer. We need to patch the controller's service to make it internal.

    ```bash
    kubectl patch svc -n app-routing-system nginx-ingress-controller \
        --patch '{"spec": {"type": "LoadBalancer"}, "metadata": {"annotations": {"service.beta.kubernetes.io/azure-load-balancer-internal": "true"}}}'
    ```

    This command adds the annotation that provisions an **Azure Internal Load Balancer**.

### 3. Deploy a Sample Application

Deploy a simple application to test the ingress configuration. We will use the `aks-helloworld` sample.

```bash
# Deploy the application
kubectl apply -f - <<EOF
apiVersion: apps/v1
kind: Deployment
metadata:
  name: aks-helloworld
spec:
  replicas: 1
  selector:
    matchLabels:
      app: aks-helloworld
  template:
    metadata:
      labels:
        app: aks-helloworld
    spec:
      containers:
      - name: aks-helloworld
        image: mcr.microsoft.com/azuredocs/aks-helloworld:v1
        ports:
        - containerPort: 80
        env:
        - name: TITLE
          value: "Welcome to AKS Ingress (Internal)"
---
apiVersion: v1
kind: Service
metadata:
  name: aks-helloworld
spec:
  type: ClusterIP
  ports:
  - port: 80
  selector:
    app: aks-helloworld
EOF
```

### 4. Configure the Internal Ingress Resource

Create an `Ingress` resource to route traffic from the internal load balancer to the sample application.

1.  **Get the Internal IP Address:**

    Wait a few minutes for the internal load balancer to be provisioned, then get its private IP address.

    ```bash
    # Wait until the EXTERNAL-IP is assigned
    kubectl get service -n app-routing-system nginx-ingress-controller --watch

    # Once assigned, get the IP and store it
    INTERNAL_IP=$(kubectl get service -n app-routing-system nginx-ingress-controller -o jsonpath='{.status.loadBalancer.ingress[0].ip}')
    echo "Internal Ingress IP: $INTERNAL_IP"
    ```

2.  **Create the Ingress Manifest:**

    Define the routing rule. We'll use the hostname `store.internal.example.com`.

    ```bash
    kubectl apply -f - <<EOF
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: aks-helloworld-ingress-internal
    spec:
      ingressClassName: webapprouting.kubernetes.azure.com
      rules:
      - host: store.internal.example.com
        http:
          paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: aks-helloworld
                port:
                  number: 80
    EOF
    ```

### 5. Configure Private DNS for Resolution

To resolve `store.internal.example.com` within your VNET, you must set up an Azure Private DNS Zone.

1.  **Create an Azure Private DNS Zone:**

    ```bash
    # VNET and Private DNS Zone details
    VNET_NAME="myVNET"
    PRIVATE_DNS_ZONE="internal.example.com"

    az network private-dns zone create \
        --resource-group $RESOURCE_GROUP \
        --name $PRIVATE_DNS_ZONE
    ```

2.  **Link the DNS Zone to your VNET:**

    ```bash
    az network private-dns link vnet create \
        --resource-group $RESOURCE_GROUP \
        --zone-name $PRIVATE_DNS_ZONE \
        --name "${VNET_NAME}-link" \
        --virtual-network $VNET_NAME \
        --registration-enabled false
    ```

3.  **Create an 'A' Record:**

    Create a DNS `A` record that maps `store.internal.example.com` to the internal load balancer's private IP.

    ```bash
    az network private-dns record-set a add-record \
        --resource-group $RESOURCE_GROUP \
        --zone-name $PRIVATE_DNS_ZONE \
        --record-set-name "store" \
        --ipv4-address $INTERNAL_IP
    ```

### 6. Verify the Ingress Controller

To verify the setup, run a temporary pod within the cluster. This pod can resolve the private DNS and access the internal endpoint.

```bash
# Run a temporary pod for testing
kubectl run -it --rm --image=mcr.microsoft.com/cbl-mariner/base/core:2.0 curl-test -- bash

# Inside the pod's shell, run the following commands:
# 1. Install curl
tdnf install curl -y

# 2. Test the endpoint
curl http://store.internal.example.com

# You should see the "Welcome to AKS Ingress (Internal)" message.
# 3. Exit the pod
exit
```

Alternatively, you can use `curl --resolve` from a jumpbox or VM inside the same VNET.

### 7. Cleanup Resources

Remove all the resources created during this tutorial to avoid incurring costs.

```bash
# 1. Delete the Ingress resource
kubectl delete ingress aks-helloworld-ingress-internal

# 2. Delete the sample application and service
kubectl delete deployment aks-helloworld
kubectl delete service aks-helloworld

# 3. Remove the Private DNS Zone
az network private-dns zone delete \
    --resource-group $RESOURCE_GROUP \
    --name $PRIVATE_DNS_ZONE \
    --yes

# 4. (Optional) Disable the Application Routing addon
az aks approuting disable \
    --resource-group $RESOURCE_GROUP \
    --name $CLUSTER_NAME
