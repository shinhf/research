# Using Managed Ingress for Both External and Internal Traffic in AKS

This guide explains how to configure the Azure Kubernetes Service (AKS) Application Routing addon to serve traffic to both public-facing (external) and private (internal) endpoints from the same cluster. This is achieved by using the default managed NGINX ingress controller for external traffic and creating a second, customized NGINX ingress controller for internal traffic.

## Prerequisites

*   An AKS cluster with the [Application Routing addon enabled](https://learn.microsoft.com/en-us/azure/aks/app-routing).
*   Azure CLI installed and configured.
*   `kubectl` installed and configured to connect to your AKS cluster.
*   Permissions to manage Azure Private DNS Zones in your subscription.

## How It Works

The Application Routing addon, by default, deploys a public-facing ingress controller (`webapprouting.kubernetes.azure.com`). To handle internal traffic, we will:

1.  Define a new `NginxIngressController` custom resource.
2.  Annotate this new controller's service to use an Azure Internal Load Balancer.
3.  Create a distinct `ingressClassName` for the internal controller.
4.  Use an Azure Private DNS Zone to resolve internal hostnames to the private IP of the internal load balancer.
5.  Deploy applications with two separate `Ingress` resources: one for the public class and one for the internal class.

---

## Step 1: Deploy a Sample Application

First, let's deploy a sample application that we will expose both publicly and privately.

1.  **Create a namespace:**
    ```bash
    kubectl create namespace aks-store
    ```

2.  **Deploy the application:**
    ```bash
    kubectl apply -f https://raw.githubusercontent.com/Azure-Samples/aks-store-demo/main/sample-manifests/docs/app-routing/aks-store-deployments-and-services.yaml -n aks-store
    ```

---

## Step 2: Configure the External Ingress

The external ingress works out-of-the-box with the default ingress class.

1.  **Create the Ingress Resource:**
    Create a file named `external-ingress.yaml` with the following content. Replace `store.your-domain.com` with your desired public hostname.

    ```yaml
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: aks-store-external
      namespace: aks-store
    spec:
      ingressClassName: webapprouting.kubernetes.azure.com
      rules:
      - host: store.your-domain.com
        http:
          paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: store-front
                port:
                  number: 80
    ```

2.  **Apply the manifest:**
    ```bash
    kubectl apply -f external-ingress.yaml -n aks-store
    ```

---

## Step 3: Create and Configure the Internal Ingress Controller

Now, we'll create a second controller dedicated to internal traffic.

1.  **Define the Internal Controller:**
    Create a file named `internal-controller.yaml`. This manifest defines a new controller and annotates its service to be internal.

    ```yaml
    apiVersion: approuting.kubernetes.azure.com/v1alpha1
    kind: NginxIngressController
    metadata:
      name: nginx-internal
    spec:
      ingressClassName: nginx-internal
      controllerNamePrefix: nginx-internal
      loadBalancerAnnotations: 
        service.beta.kubernetes.io/azure-load-balancer-internal: "true"
    ```

2.  **Apply the manifest:**
    ```bash
    kubectl apply -f internal-controller.yaml
    ```

3.  **Verify Controller Creation:**
    Check that both controllers are available. It may take a minute for the new controller to become ready.

    ```bash
    kubectl get nginxingresscontroller
    ```

    You should see an output similar to this:
    ```
    NAME             INGRESSCLASS                         CONTROLLERNAMEPREFIX   AVAILABLE
    default          webapprouting.kubernetes.azure.com   nginx                  True
    nginx-internal   nginx-internal                       nginx-internal         True
    ```

---

## Step 4: Configure Private DNS for Internal Resolution

For internal services, you need a private DNS zone to resolve hostnames within your VNet.

1.  **Create an Azure Private DNS Zone:**
    Replace `private.your-domain.com` with your desired internal domain and provide your resource group name.

    ```bash
    az network private-dns zone create \
        --resource-group <YourResourceGroupName> \
        --name private.your-domain.com
    ```

2.  **Link the DNS Zone to your AKS VNet:**
    ```bash
    az network private-dns link vnet create \
        --resource-group <YourResourceGroupName> \
        --name MyDnsLink \
        --zone-name private.your-domain.com \
        --virtual-network <YourAksVnetName> \
        --registration-enabled false
    ```

3.  **Attach the Zone to the App Routing Addon:**
    First, get the resource ID of your private DNS zone:
    ```bash
    ZONEID=$(az network private-dns zone show --resource-group <YourResourceGroupName> --name private.your-domain.com --query "id" --output tsv)
    ```
    Then, attach it to your AKS cluster:
    ```bash
    az aks approuting zone add \
        --resource-group <YourResourceGroupName> \
        --name <YourAksClusterName> \
        --ids=${ZONEID} \
        --attach-zones
    ```

---

## Step 5: Configure the Internal Ingress

Now, create an `Ingress` resource for the internal service, using the new `nginx-internal` class.

1.  **Create the Internal Ingress Resource:**
    Create a file named `internal-ingress.yaml`. Use a hostname within the private DNS zone you created.

    ```yaml
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: aks-store-internal
      namespace: aks-store
    spec:
      ingressClassName: nginx-internal
      rules:
      - host: store.private.your-domain.com
        http:
          paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: store-front
                port:
                  number: 80
    ```

2.  **Apply the manifest:**
    ```bash
    kubectl apply -f internal-ingress.yaml -n aks-store
    ```

---

## Step 6: Verification

You now have two `Ingress` objects routing to the same service.

### Verify External Access

1.  **Get the Public IP:**
    Find the external IP address of the default ingress controller.
    ```bash
    kubectl get service -n app-routing-system nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
    ```

2.  **Test with `curl`:**
    Use the public IP and the external hostname to test connectivity.
    ```bash
    curl --resolve store.your-domain.com:80:<Public_IP_Address> http://store.your-domain.com
    ```
    You should receive the HTML content of the AKS Store application.

### Verify Internal Access

1.  **Get the Private IP:**
    Find the internal IP address of the new `nginx-internal` controller.
    ```bash
    kubectl get service -n app-routing-system nginx-internal-nginx-ingress-controller -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
    ```

2.  **Test from within the Cluster:**
    Launch a temporary pod within the cluster to test internal DNS resolution and connectivity.

    ```bash
    kubectl run -it --rm --image=mcr.microsoft.com/dotnet/sdk:8.0 dns-test -- /bin/bash
    ```

3.  **Inside the test pod, run `curl`:**
    Use the internal hostname. The private DNS zone should automatically resolve it to the internal load balancer's private IP.

    ```bash
    # Inside the dns-test pod
    curl http://store.private.your-domain.com
    ```
    You should see the HTML content of the application. Type `exit` to leave the pod.

You have successfully configured a single AKS cluster to serve traffic to both external and internal endpoints using the managed Application Routing addon.
