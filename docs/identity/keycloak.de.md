---
sidebar_label: Keycloak IAM
---

# Identity & Access Management mit Keycloak

Die SovereignSecure Cloud nutzt **Keycloak** als zentrale Lösung für das Identity and Access Management (IAM). Keycloak bietet einen sicheren, zentralen Einstiegspunkt für alle Cloud-Dienste, Dashboards und APIs.

## Funktionen

* **Single Sign-On (SSO):** Melden Sie sich einmal an und erhalten Sie Zugriff auf die Cloud Management Platform (CMP), OpenStack Horizon, Grafana-Dashboards und andere integrierte Dienste.
* **Identity Brokering & Federation:** Wir können die bestehenden Identitätsanbieter Ihrer Organisation (Active Directory, LDAP, SAML 2.0, OpenID Connect) nahtlos in die Cloud-Umgebung integrieren.
* **Multi-Faktor-Authentifizierung (MFA):** Setzen Sie strenge Authentifizierungsrichtlinien mithilfe von OTP (One-Time Passwords) oder Hardware-Sicherheitsschlüsseln durch, um sensible Cloud-Ressourcen zu schützen.
* **Rollenbasierte Zugriffskontrolle (RBAC):** Ordnen Sie Ihre organisatorischen Gruppen bestimmten OpenStack-Rollen zu (z. B. `member`, `reader`, `admin`), um das Prinzip der geringsten Privilegien sicherzustellen.

## Zugriff auf die Cloud

Beim Zugriff auf die SovereignSecure CMP oder API werden Sie zum Keycloak-Authentifizierungsportal weitergeleitet. Sobald Ihre Identität verifiziert ist, wird ein sicheres Token generiert und an die zugrunde liegenden Cloud-Dienste übergeben.

*(Im Abschnitt API & Automatisierung finden Sie Anweisungen zur Verwendung von Keycloak-Anwendungsanmeldeinformationen für den CLI-/API-Zugriff).*