---
sidebar_label: KaaS (Cluster API)
---

# Kubernetes as a Service (KaaS)

SovereignSecure Cloud provides enterprise-grade **Kubernetes as a Service (KaaS)** utilizing **Cluster API (CAPI)**. 

## Cluster API (CAPI) Integration

Cluster API is a Kubernetes project that brings declarative, Kubernetes-style APIs to cluster creation, configuration, and management. 

Instead of manually provisioning OpenStack instances and installing Kubernetes, CAPI allows you to define your desired cluster state in a YAML file.

* **Declarative Management:** Define the number of control plane nodes, worker nodes, and Kubernetes versions as code.
* **Lifecycle Automation:** Easily upgrade Kubernetes versions, scale worker nodes up or down, or replace unhealthy nodes automatically.
* **Native OpenStack Synergy:** Our CAPI provider interacts directly with OpenStack Nova, Neutron, and Octavia to automatically provision the VMs, load balancers, and security groups required for your cluster.

## Getting Started

You can request a new Managed Kubernetes cluster directly through the Cloud Management Platform (CMP) self-service catalog, which will orchestrate the CAPI deployment on your behalf.