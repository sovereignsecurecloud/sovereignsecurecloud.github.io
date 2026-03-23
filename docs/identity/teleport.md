---
sidebar_label: Teleport PAM
---

# Privileged Access Management (PAM) with Teleport

In a sovereign cloud, securing and auditing administrative access to infrastructure is paramount. SovereignSecure Cloud utilizes **Teleport** for comprehensive Privileged Access Management (PAM).

## Zero-Trust Access

Teleport replaces legacy static SSH keys and VPNs with identity-based, zero-trust access.

* **Certificate-Based Authentication:** Instead of managing static `id_rsa` keys, Teleport issues short-lived, identity-bound certificates tied to your Keycloak SSO login.
* **Unified Access:** Securely access SSH servers, Kubernetes clusters, databases, and internal web applications through a single gateway.

## Auditing and Compliance

To meet rigorous sovereign and regulatory compliance standards, Teleport provides:

* **Session Recording:** Every interactive SSH and Kubernetes `exec` session is recorded and can be played back for security audits.
* **Detailed Audit Logs:** A comprehensive log of all access events, commands executed, and file transfers, exportable directly to our SIEM (Wazuh).
* **Just-In-Time Access:** Administrators can request temporary, elevated permissions for specific infrastructure elements only when needed for break-glass scenarios.