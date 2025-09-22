# Manual: Installing and Verifying a Managed External Ingress Controller in AKS

This guide provides a step-by-step manual for installing, configuring, and verifying a managed, external-facing ingress controller on Azure Kubernetes Service (AKS) using the Application Routing addon.

---

### Prerequisites

*   An active Azure subscription.
*   Azure CLI installed and configured.
*   `kubectl` command-line tool installed.
*   An existing AKS cluster. If you don't have one, create it first.

---

## Step 1: Install the Managed Ingress Controller (Application Routing Addon)

The easiest and recommended way to get a managed NGINX ingress controller is to enable the Application Routing addon on your AKS cluster. This command will install the controller and create a default, public-facing ingress class.

1.  **Set your cluster details (replace with your actual values):**
    ```bash
    export AKS_RESOURCE_GROUP="myResourceGroup"
    export AKS_CLUSTER_NAME="myAKSCluster"
    ```

2.  **Enable the addon using Azure CLI:**
    ```bash
    az aks approuting enable \
        --resource-group $AKS_RESOURCE_GROUP \
        --name $AKS_CLUSTER_NAME
    ```
    This process can take a few minutes. It sets up the NGINX ingress controller pods and a public Azure Load Balancer to receive external traffic.

3.  **Verify the addon is enabled:**
    ```bash
    az aks show -n $AKS_CLUSTER_NAME -g $AKS_RESOURCE_GROUP --query "networkProfile.ingressProfile.webAppRouting.enabled"
    ```
    This should return `true`.

---

## Step 2: Configure the Ingress Controller by Deploying an Application

To configure and test the ingress, you need to deploy an application and then create an `Ingress` resource to expose it.

1.  **Create a namespace for your application:**
    ```bash
    kubectl create namespace aks-store-demo
    ```

2.  **Deploy a sample application:** We will use a sample "hello world" application provided by Microsoft.
    ```bash
    kubectl apply -n aks-store-demo -f https://raw.githubusercontent.com/Azure-Samples/aks-store-demo/main/sample-manifests/docs/app-routing/aks-store-deployments-and-services.yaml
    ```
    This creates the necessary `Deployment` and `Service` resources for a demo application.

3.  **Create the Ingress Resource:** This is the core configuration step. Create a file named `ingress.yaml` with the following content. This tells the ingress controller how to route traffic to your application.

    ```yaml
    # ingress.yaml
    apiVersion: networking.k8s.io/v1
    kind: Ingress
    metadata:
      name: aks-store-ingress
      namespace: aks-store-demo
    spec:
      ingressClassName: webapprouting.kubernetes.azure.com # This is the default class for the addon
      rules:
      - host: store.example.com # A placeholder hostname
        http:
          paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: store-front # This must match the service name from the previous step
                port:
                  number: 80
    ```

4.  **Apply the Ingress resource:**
    ```bash
    kubectl apply -f ingress.yaml
    ```

---

## Step 3: Verify It's Working from the Bash Command Line

Now, we will verify that the ingress controller is correctly routing traffic from its public IP to your application.

1.  **Get the External IP Address:** Find the public IP address assigned to the NGINX ingress controller's service. It may take a minute or two for the `EXTERNAL-IP` to be assigned.

    ```bash
    kubectl get service -n app-routing-system nginx -o jsonpath='{.status.loadBalancer.ingress[0].ip}'
    ```
    This command queries the service named `nginx` in the `app-routing-system` namespace (where the addon is installed) and extracts its public IP. Copy this IP address.

2.  **Verify using `curl`:** Since we haven't set up a real DNS record for `store.example.com`, we will use `curl`'s `--resolve` flag to manually tell it where to send the request. This simulates DNS resolution and is the most effective way to test from the command line.

    *   Replace `<EXTERNAL_IP>` with the IP address you copied.
    *   Replace `store.example.com` with the host you defined in `ingress.yaml`.

    ```bash
    curl --resolve store.example.com:80:<EXTERNAL_IP> http://store.example.com
    ```

3.  **Check the Output:** If everything is configured correctly, you should see the HTML content of the demo application, which will start something like this:

    ```html
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>AKS Store Demo</title>
    ...
    ```

This successful `curl` response confirms that your managed external ingress controller is installed, configured, and correctly routing external traffic to your application.
