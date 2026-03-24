---
sidebar_label: IAM Overview
sidebar_position: 1
---

# Identity & Security Overview

Welcome to the SovereignSecure Cloud Identity & Security documentation. In a sovereign environment, controlling access and maintaining a strict, auditable security posture is the highest priority. 

Our platform adopts a zero-trust architecture, ensuring that every user, system, and automated process is continuously authenticated and authorized before granting access to cloud resources.

## Core Identity & Security Services

Explore the following sections to learn how to manage access and monitor your secure environment:

* **[Keycloak IAM](keycloak.md):** Learn about our central Identity and Access Management broker, providing Single Sign-On (SSO) and identity federation.
* **[Users & Projects](projects.md):** Understand how cloud resources are logically grouped into Projects (tenants) and how to manage the users operating within them.
* **[Roles & Policies](roles.md):** Discover how Role-Based Access Control (RBAC) enforces the principle of least privilege across your infrastructure.
* **[Teleport PAM](teleport.md):** Secure and audit your privileged administrative access to Compute Instances and Kubernetes clusters using our zero-trust access gateway.
* **[SIEM](siem.md):** Monitor your infrastructure's security posture, detect threats, and ensure compliance using our integrated Security Information and Event Management platform.

## Sovereignty and Compliance

By strictly coupling your organizational identity boundaries to our access management tools, you retain complete sovereignty over who can view, modify, or destroy your data. Detailed audit logs are automatically generated and routed to the SIEM to satisfy strict local compliance frameworks.