---
sidebar_label: Deploying Clusters
---

# Deploying Kubernetes Clusters

SovereignSecure Cloud offers multiple ways to provision and manage your Kubernetes clusters, whether you prefer a visual, UI-driven approach or a fully automated Infrastructure as Code (IaC) workflow.

## Deployment Methods

### 1. Cloud Management Platform (CMP)

The easiest way to get started is by using the self-service catalogs within the CMP. 

* **KaaS (Managed Kubernetes):** Navigate to the **Service Catalog** and select the **Kubernetes Cluster** blueprint. You will be prompted to select the Kubernetes version, the number of control plane nodes (for High Availability), and the size/count of your worker nodes. The CMP will orchestrate the underlying Cluster API (CAPI) deployment on your behalf.
* **K3s (Lightweight):** Select the **K3s Edge Cluster** blueprint. This will quickly provision a lightweight instance using a pre-configured OS image and initialize a single-node or multi-node K3s environment.

### 2. Infrastructure as Code (Terraform / OpenTofu)

For production environments and CI/CD integration, we highly recommend defining your clusters as code.

* **Using Cluster API:** You can use the Kubernetes provider to apply standard CAPI YAML definitions directly to our management cluster, which will automatically spawn your workload clusters on OpenStack.
* **Using the OpenStack Provider:** You can use the standard Terraform OpenStack provider to provision compute instances, networks, and load balancers, and then use `cloud-init` user scripts to bootstrap your own K3s or standard Kubernetes distributions.

## Accessing Your Cluster

Once your cluster is provisioned, you need to retrieve your `kubeconfig` file to interact with it using the `kubectl` CLI.

### Via CMP
If you provisioned the cluster via the CMP Service Catalog, navigate to your deployed service's details page. You will find a secure download link or a block of text containing your `kubeconfig`.

### Via CLI / CAPI
If you are managing the cluster via Cluster API, the `kubeconfig` is stored as a standard Kubernetes Secret in the management cluster. You can extract it using:

```bash
kubectl --namespace default get secret <cluster-name>-kubeconfig \
   -o jsonpath={.data.value} | base64 --decode > sovereign-kubeconfig
```