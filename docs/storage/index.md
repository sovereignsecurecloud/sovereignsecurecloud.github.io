---
sidebar_label: Overview
sidebar_position: 1
---

# Storage Overview

Welcome to the SovereignSecure Cloud Storage documentation. Our storage infrastructure is designed to provide highly available, durable, and scalable data storage solutions tailored to meet strict data sovereignty and compliance requirements.

Powered by a robust Software-Defined Storage (SDS) architecture, we offer multiple storage interfaces to accommodate a wide variety of workloads, from standard virtual machine disks to massive unstructured data archives.

## Core Storage Services

Explore the following sections to learn more about the storage capabilities available in SovereignSecure Cloud:

* **[Ceph SDS](ceph.md):** Learn about our underlying Software-Defined Storage backend powered by Ceph, which provides a highly reliable, self-healing foundation for all our storage offerings.
* **[Block Storage](block_storage.md):** High-performance persistent block volumes (managed via OpenStack Cinder) that can be attached to your Compute Instances. Ideal for operating systems, databases, and applications requiring raw block-level access.
* **[Object Storage](object_storage.md):** Highly scalable, S3-compatible storage for unstructured data such as backups, media files, machine learning datasets, and static web assets, seamlessly accessible via HTTP APIs.

## Data Sovereignty

All data stored within our environment remains onshore and completely isolated, ensuring that you maintain absolute control over your digital assets without exposure to foreign jurisdictions or proprietary vendor lock-in.