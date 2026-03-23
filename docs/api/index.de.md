---
sidebar_label: Übersicht
sidebar_position: 1
---

# API-Übersicht

Die SovereignSecure Cloud bietet umfassenden API-Zugriff, der es Entwicklern und Systemadministratoren ermöglicht, die Bereitstellung, Konfiguration und Verwaltung der Infrastruktur zu automatisieren.

Unsere Umgebung nutzt zwei primäre API-Ebenen, abhängig von Ihren Automatisierungsanforderungen:

1. **SovereignSecure Cloud Management Platform (CMP) API**
2. **Native OpenStack-Infrastruktur-APIs**

## Cloud Management Platform (CMP) API

Die CMP-API basiert auf ManageIQ und ist der empfohlene Einstiegspunkt für Benutzer, die ihren Cloud-Lebenszyklus, Bereitstellungsanfragen, Kontingente und organisatorisches Reporting verwalten möchten. Sie bietet eine RESTful-Schnittstelle zum zentralen Verwaltungstool.

- **Endpunkt:** `https://portal.sovereignsecurecloud.com/api`
- **Authentifizierung:** Basic Auth oder Token-basierte Authentifizierung
- **Am besten für:** Self-Service-Bereitstellung, Servicekataloge, Chargeback/Showback-Daten und mandantenfähige Organisationsverwaltung.

## Native OpenStack-APIs

Für eine tiefgreifende Infrastrukturautomatisierung stellt die SovereignSecure Cloud standardmäßige native OpenStack-APIs zur Verfügung. Dies ermöglicht Ihnen die Verwendung vertrauter Tools wie Terraform, OpenTofu, Ansible und der Standard-OpenStack-CLI.

- **Identität (Keystone):** Authentifizierung und Katalogerkennung.
- **Compute (Nova):** Verwaltung des Instanz-Lebenszyklus.
- **Netzwerk (Neutron):** VPCs, Subnetze, Router und Floating IPs.
- **Block Storage (Cinder):** Volumes und Snapshots.
- **Image Service (Glance):** OS-Images und benutzerdefinierte Snapshots.