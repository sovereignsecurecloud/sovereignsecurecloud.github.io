---
sidebar_label: Block Storage
---

# Block Storage

SovereignSecure Cloud provides highly available and persistent **Block Storage** volumes, managed through the OpenStack Cinder service and backed by our robust Ceph SDS infrastructure.

Block storage acts like a physical hard drive that you can attach to your Compute Instances. It provides raw, block-level storage that can be formatted with a file system (like EXT4, XFS, or NTFS) and is ideal for applications that require low-latency, high-performance data access.

## Key Features

* **Persistence:** Unlike ephemeral instance storage, block storage volumes persist independently of the instance lifecycle. If you delete an instance, you can choose to retain the attached block volume and its data.
* **High Availability:** Because volumes are backed by Ceph, your data is inherently replicated across multiple physical disks and nodes. Hardware failures are handled transparently without data loss.
* **Bootable Volumes:** You can create an image-backed volume and use it as the root disk to boot a new instance.
* **Scalability:** You can easily increase the size of an existing block storage volume (Volume Resizing) as your storage needs grow without needing to migrate data.
* **Portability:** Volumes can be detached from one instance and reattached to another, allowing for easy data portability and disaster recovery.

## Volume Snapshots

A volume snapshot is a point-in-time, read-only copy of your block storage volume. 

* **Backups:** Snapshots are essential for creating reliable backups of your databases or critical file systems before performing system upgrades or risky operations.
* **Cloning:** You can create new, identical block storage volumes directly from a snapshot, making it easy to replicate environments for testing or scaling.

## Common Use Cases

Block storage is the recommended storage type for:

* Relational and NoSQL Databases (MySQL, PostgreSQL, MongoDB, etc.)
* Operating System boot disks
* Enterprise applications requiring POSIX-compliant file systems
* High-I/O workloads requiring dedicated performance

## Managing Volumes

You can create, attach, detach, and delete Block Storage volumes directly from the Cloud Management Platform (CMP) under the **Storage > Volumes** section, or programmatically via the OpenStack CLI and Terraform.