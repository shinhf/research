# AKS Ingress Controllers: Managed vs. Unmanaged and Internal Configuration

As a seasoned DevOps lead, understanding the nuances between managed and unmanaged ingress controllers is crucial for designing a robust, scalable, and maintainable architecture on Azure Kubernetes Service (AKS). This guide provides a detailed breakdown of the differences and explains how to configure a secure, VNET-facing (internal) ingress controller.

---

## 1. Managed vs. Unmanaged Ingress Controllers

The fundamental difference lies in **who is responsible for the lifecycle and operation of the ingress controller's components**.

* **Managed Ingress Controller:** The cloud provider (Azure) is responsible for deploying, managing, scaling, patching, and updating the ingress controller. You interact with it as a service, focusing on configuring ingress rules. The **Application Routing addon** in AKS is the primary example, providing a fully managed NGINX ingress controller.
* **Unmanaged (or Self-Hosted) Ingress Controller:** You are responsible for the entire lifecycle. This includes selecting the software (e.g., community NGINX, Traefik), deploying it, configuring it, scaling the pods, and performing all security patches and version upgrades.

### Detailed Comparison

| Feature                           | Managed Ingress Controller (e.g., AKS Application Routing addon)                                                                                                      | Unmanaged Ingress Controller (e.g., Self-hosted NGINX/Traefik)                                                                                                 |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Management Overhead**     | **Low.** Azure handles the control plane's health, availability, and updates. You only manage the `Ingress` resource definitions.                             | **High.** You are responsible for installation, configuration, scaling, security patching, and version upgrades of the controller pods.                  |
| **Configuration & Setup**   | **Simple & Streamlined.** Enabled via a simple addon command. Configuration is straightforward and opinionated for common use cases.                            | **Complex & Flexible.** Requires manual deployment (e.g., Helm chart) and in-depth configuration of the controller's settings.                           |
| **Cloud Integration**       | **Deep & Native.** Seamless, out-of-the-box integration with Azure DNS for automatic DNS record creation and Azure Key Vault for managing SSL/TLS certificates. | **Manual.** Integration with cloud services is possible but requires manual configuration (e.g., setting up `cert-manager` with a Key Vault provider). |
| **Customization & Control** | **Limited.** You have less control over the underlying ingress controller's configuration. The provider exposes a curated set of options.                       | **Total Control.** You can fine-tune every aspect of the ingress controller's configuration, use custom builds, or add third-party modules.              |
| **Support**                 | **Fully Supported by Azure.** If something goes wrong with the ingress controller itself, you can rely on Azure support.                                        | **Community or Vendor Support.** You rely on open-source community support or a commercial subscription from the ingress controller's vendor.            |
| **Updates & Security**      | **Automatic.** Azure automatically applies security patches and updates the controller to new, stable versions.                                                 | **Manual.** You are responsible for monitoring for vulnerabilities and planning and executing the upgrade process.                                       |

### Recommendation

The **managed Application Routing addon is the recommended, best-practice starting point for most workloads on AKS** due to its simplicity, security, and integration. Opt for an unmanaged solution only when you have a compelling technical reason that outweighs the significant increase in operational responsibility.

---

## 2. How to Create an Internal (VNET-Facing) Ingress Controller

An internal ingress controller is a critical pattern for securely exposing internal applications (like dashboards or APIs) without making them accessible to the public internet. This is achieved by using an **Azure Internal Load Balancer**, which is assigned a private IP address from your VNET.

The key is to apply the annotation `service.beta.kubernetes.io/azure-load-balancer-internal: "true"` to the ingress controller's service.

### Method 1: The Managed Approach (Recommended)

Using the **AKS Application Routing addon** is the simplest and most integrated method.

1. **Prerequisites:**

   * An AKS cluster with the Application Routing addon enabled.
   * An Azure Private DNS Zone (e.g., `private.contoso.com`).
   * A Virtual Network Link between your AKS VNET and the Private DNS Zone.
2. **Define an Internal NGINX Ingress Controller:** Create a YAML file to define a new `NginxIngressController` resource. The `loadBalancerAnnotations` section is the critical part.

   ```yaml
   # nginx-internal-controller.yaml
   apiVersion: approuting.kubernetes.azure.com/v1alpha1
   kind: NginxIngressController
   metadata:
     name: nginx-internal
   spec:
     ingressClassName: nginx-internal
     controllerNamePrefix: nginx-internal
     loadBalancerAnnotations: 
       # This annotation makes the controller internal
       service.beta.kubernetes.io/azure-load-balancer-internal: "true"
   ```

   Apply this with `kubectl apply -f nginx-internal-controller.yaml`.
3. **Deploy Your Ingress Resource:** When creating your `Ingress` resource, specify the `ingressClassName` to use the internal controller.

   ```yaml
   apiVersion: networking.k8s.io/v1
   kind: Ingress
   metadata:
     name: internal-dashboard
   spec:
     ingressClassName: nginx-internal # Use the internal controller
     rules:
     - host: dashboard.private.contoso.com # Hostname in your private DNS zone
       http:
         # ... backend service configuration
   ```

   The addon automatically provisions the internal load balancer and creates the `A` record in your Private DNS Zone.

### Method 2: The Unmanaged (Self-Hosted) Approach

If you manage your own ingress controller via Helm, you must configure the annotations manually.

1. **Set Annotation via Helm:** During installation, pass the annotation as a Helm value.

   ```bash
   helm install nginx-ingress ingress-nginx/ingress-nginx \
     --namespace ingress-basic \
     --set controller.service.annotations."service\.beta\.kubernetes\.io/azure-load-balancer-internal"="true"
   ```
2. **Manual DNS Management:** With this method, DNS is **not** automated. You must:

   * Find the private IP address assigned to the ingress controller's service (`kubectl get svc ...`).
   * Manually create an `A` record in your Azure Private DNS Zone pointing your hostname to this private IP.

### Final Recommendation

For deploying internal services on AKS, the **managed Application Routing addon is the superior choice**. It drastically reduces operational complexity by automating the controller's lifecycle and, most importantly, the DNS management, which is often a tedious and error-prone manual task.
