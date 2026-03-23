---
sidebar_label: K3s Kubernetes
---

# Kubernetes with K3s

For workloads that require a lightweight, highly efficient container orchestration platform, SovereignSecure Cloud offers support for **K3s**.

## What is K3s?

K3s is a highly available, certified Kubernetes distribution designed for production workloads in resource-constrained, edge, or IoT environments. It packages all Kubernetes components into a single binary.

## Key Advantages

* **Lightweight:** Has a very small memory footprint compared to standard Kubernetes, leaving more resources available for your actual applications.
* **Fast Provisioning:** Clusters boot incredibly quickly, making it ideal for ephemeral CI/CD pipelines or rapid scaling.
* **Secure by Default:** Designed with security in mind, providing a reduced attack surface due to its stripped-down dependencies.

## Deployment

K3s clusters can be rapidly spun up using our CMP Service Catalogs or managed via Infrastructure as Code (Terraform) against SovereignSecure compute instances.