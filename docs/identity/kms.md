---
sidebar_label: Key Management (KMS)
---

# Key Management Service (KMS)

Safeguarding cryptographic keys and secrets is a critical pillar of maintaining data sovereignty. SovereignSecure Cloud provides a highly secure **Key Management Service (KMS)** powered by OpenStack Barbican.

## Centralized Secret Storage

The KMS acts as a secure, API-driven vault for provisioning, managing, and storing:
* Symmetric and Asymmetric encryption keys
* SSL/TLS Certificates (used by Load Balancers)
* Passwords and API tokens

## Transparent Data Encryption

The KMS natively integrates with our underlying storage services to provide transparent, at-rest encryption:

* **Encrypted Block Storage:** You can configure your Cinder volumes to be encrypted using the LUKS format. The KMS securely holds the volume's encryption key. The hypervisor retrieves the key directly from the KMS upon instance boot to decrypt the disk on the fly.
* **Encrypted Object Storage:** Server-Side Encryption (SSE) for Ceph Object Storage buckets can be managed using keys stored in the KMS, ensuring your unstructured data is encrypted before it is written to the physical drives.