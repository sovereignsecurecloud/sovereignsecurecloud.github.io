---
sidebar_label: OpenStack IaaS
---

# Infrastructure as a Service (IaaS) with OpenStack

SovereignSecure Cloud leverages **OpenStack** as its core Infrastructure as a Service (IaaS) platform. OpenStack is an open-source cloud operating system that controls large pools of compute, storage, and networking resources throughout a datacenter, all managed and provisioned through APIs with common authentication mechanisms.

## Why OpenStack for a Sovereign Cloud?

To maintain true data sovereignty, you must have complete control over the underlying infrastructure stack. OpenStack provides:

* **No Vendor Lock-in:** Built entirely on open-source technologies, ensuring your infrastructure is not tied to proprietary, black-box software.
* **Auditable Codebase:** The transparency of open-source allows for rigorous security auditing required by sovereign and compliance frameworks.
* **Massive Scalability:** Proven at scale by the world's largest telecommunications providers and research facilities.
* **Multi-Tenancy & Isolation:** Strict boundary enforcement between different projects and tenants to guarantee data privacy.

## Core OpenStack Components

Our environment integrates several key OpenStack services to deliver a seamless cloud experience:

* **Nova (Compute):** Provisions and manages the lifecycles of compute instances (Virtual Machines).
* **Glance (Image Service):** Discovers, registers, and retrieves virtual machine images.
* **Cinder (Block Storage):** Provides persistent block storage volumes for compute instances.