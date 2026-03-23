---
sidebar_label: Ceph SDS
---

# Software Defined Storage (SDS) with Ceph

SovereignSecure Cloud utilizes **Ceph** to provide a unified, highly scalable Software-Defined Storage (SDS) backend. Ceph transforms standard hardware into an enormously scalable, highly reliable storage cluster.

## Unified Storage Architecture

Ceph uniquely provides interfaces for multiple storage types from a single distributed cluster:

* **Block Storage (RBD):** Ceph provides the backend for OpenStack Cinder. When you create and attach an additional volume to an instance, it is backed by a highly available Ceph RADOS Block Device.
* **Object Storage (RGW):** Ceph provides an S3-compatible API via the RADOS Gateway, allowing you to store and retrieve unstructured data (like backups, images, and static assets) reliably over HTTP.
* **File Storage (CephFS):** Provides a POSIX-compliant shared file system that can be mounted simultaneously by multiple instances.

## Reliability & Sovereignty

* **Data Replication:** Ceph inherently replicates data across multiple physical nodes and racks (Availability Zones). If a drive or an entire server fails, Ceph automatically heals and redistributes the data without downtime.
* **Self-Healing:** The CRUSH algorithm empowers the storage cluster to automatically route data, manage re-balancing, and recover from faults.
* **Data Sovereignty:** Because Ceph runs entirely within our onshore, sovereign data centers, your data is geographically guaranteed and completely free from foreign jurisdiction access.

## Best Practices

* **Volume Snapshots:** Leverage instantaneous Ceph snapshots to back up the state of your instances before making major changes.
* **Storage Tiers:** Be aware of different storage tiers (e.g., NVMe/SSD vs HDD) when provisioning your volumes to balance performance requirements against cost.