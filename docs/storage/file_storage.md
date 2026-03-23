---
sidebar_label: Shared File Storage
---

# Shared File Storage

In addition to Block and Object storage, SovereignSecure Cloud offers **Shared File Storage** managed via OpenStack Manila and backed by CephFS.

Shared File Storage provides standard, POSIX-compliant file systems that can be mounted simultaneously by multiple Compute Instances. This is essential for enterprise applications that expect a traditional NAS (Network Attached Storage) environment.

## Key Features

* **Concurrent Access:** Unlike Block Storage (Cinder) which is typically attached to a single instance at a time, Shared File Storage allows dozens or hundreds of VMs to read and write to the same files concurrently.
* **Scalability:** File shares can grow seamlessly as your data requirements expand, without needing to partition or format underlying physical disks manually.
* **Supported Protocols:** We natively support both **NFS** (Network File System) for Linux workloads and **CIFS/SMB** for Windows instances.

## Common Use Cases

* **Web Server Clusters:** Hosting shared website assets (images, CSS, code) across a fleet of load-balanced web servers.
* **Content Management Systems (CMS):** Storing uploaded media for applications like WordPress or Drupal.
* **Enterprise Applications:** Legacy software that requires concurrent read/write operations to a shared network drive.

File shares can be created and managed via the **Storage > File Shares** section in the Cloud Management Platform (CMP).