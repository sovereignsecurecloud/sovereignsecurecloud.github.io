---
sidebar_label: Object Storage
---

# Object Storage

SovereignSecure Cloud provides highly scalable, highly durable **Object Storage** powered by the Ceph RADOS Gateway (RGW). Our Object Storage is fully compatible with the industry-standard Amazon S3 API, making it easy to integrate into your existing applications and workflows.

Unlike Block Storage, which is attached to specific Compute Instances, Object Storage is accessible from anywhere over HTTP/HTTPS, making it the ideal solution for storing massive amounts of unstructured data.

## Key Features

* **Massive Scalability:** Store virtually limitless amounts of data. The underlying Ceph storage cluster handles scaling out automatically without user intervention.
* **S3 Compatibility:** Natively supports standard S3 tools, SDKs (like Boto3), and REST APIs. You can easily migrate workloads designed for public clouds into our sovereign environment without rewriting your code.
* **High Durability:** Data is automatically replicated and erasure-coded across multiple physical nodes and racks, providing enterprise-grade durability against hardware failures.
* **Fine-Grained Access Control:** Secure your buckets and objects using standard S3 Access Control Lists (ACLs) and integrated IAM policies.
* **Data Sovereignty:** All objects are stored exclusively within our onshore, sovereign data centers, guaranteeing compliance with local data residency laws.

## Common Use Cases

Object Storage is highly versatile and recommended for:

* **Backups and Archives:** Storing database dumps, instance snapshots, and long-term compliance archives.
* **Media and Content:** Hosting images, videos, and large media files for web applications.
* **Big Data & Machine Learning:** Serving as a massive data lake for analytics, logs, and AI/ML training datasets.
* **Static Assets:** Distributing static assets (HTML, CSS, JavaScript) for front-end web development.

## Getting Started

### Accessing Object Storage

You can manage your Object Storage directly through the Cloud Management Platform (CMP) under the **Storage > Object Storage** section, where you can create buckets, upload files, and manage permissions.

### Using S3 Clients

To connect programmatically or via CLI tools (such as the `aws` CLI, `s3cmd`, or Cyberduck), you will need to generate **S3 Credentials** (Access Key and Secret Key) from your user profile in the CMP.

Once generated, configure your client to point to the SovereignSecure Cloud Object Storage endpoint URL.