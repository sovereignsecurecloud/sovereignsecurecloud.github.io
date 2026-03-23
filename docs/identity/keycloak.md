---
sidebar_label: Keycloak IAM
---

# Identity & Access Management with Keycloak

SovereignSecure Cloud utilizes **Keycloak** as the central Identity and Access Management (IAM) solution. Keycloak provides a secure, single point of entry for all cloud services, dashboards, and APIs.

## Features

* **Single Sign-On (SSO):** Log in once and gain access to the Cloud Management Platform (CMP), OpenStack Horizon, Grafana dashboards, and other integrated services.
* **Identity Brokering & Federation:** We can seamlessly integrate your organization's existing identity providers (Active Directory, LDAP, SAML 2.0, OpenID Connect) with the cloud environment.
* **Multi-Factor Authentication (MFA):** Enforce strict authentication policies using OTP (One-Time Passwords) or hardware security keys to protect sensitive cloud resources.
* **Role-Based Access Control (RBAC):** Map your organizational groups to specific OpenStack roles (e.g., `member`, `reader`, `admin`), ensuring the principle of least privilege.

## Accessing the Cloud

When accessing the SovereignSecure CMP or API, you will be redirected to the Keycloak authentication portal. Once your identity is verified, a secure token is generated and passed to the underlying cloud services.

*(Refer to the API & Automation section for instructions on using Keycloak Application Credentials for CLI/API access).*