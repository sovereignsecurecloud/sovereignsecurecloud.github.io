---
sidebar_label: Übersicht
sidebar_position: 1
---

# Netzwerk Übersicht

Willkommen bei der Netzwerkdokumentation der SovereignSecure Cloud. Unsere Netzwerkdienste bieten die grundlegende Konnektivität, Isolierung und Sicherheit, die für den Aufbau robuster und konformer Cloud-Architekturen erforderlich sind.

Basierend auf einem modernen Software-Defined Networking (SDN)-Stack, der SONiC und OVN nutzt und nativ in OpenStack Neutron integriert ist, bieten wir eine hochgradig skalierbare und sichere Netzwerk-Fabric.

## Zentrale Netzwerkdienste

Erkunden Sie die folgenden Abschnitte, um zu erfahren, wie Sie Ihre Netzwerkressourcen entwerfen und verwalten:

* **[SDN-Architektur](sdn.md):** Verstehen Sie die zugrunde liegenden Software-Defined Networking-Technologien (SONiC & OVN), die unsere sichere und skalierbare Fabric antreiben.
* **[VPC & Subnetze](vpc.md):** Erfahren Sie, wie Sie isolierte Virtual Private Clouds (VPCs) erstellen und diese in Subnetze unterteilen, um Ihre Ressourcen zu organisieren.
* **[Router & Floating IPs](routers_fips.md):** Entdecken Sie, wie Sie Datenverkehr zwischen Ihren internen Subnetzen weiterleiten und den externen Zugriff mit Floating IPs verwalten.
* **[Sicherheitsgruppen](security_group.md):** Implementieren Sie Zero-Trust-Sicherheit durch die Konfiguration zustandsbehafteter, verteilter Firewall-Regeln auf Instanzebene.
* **[Load Balancer](load_balancer.md):** Verteilen Sie eingehenden Datenverkehr über mehrere Instanzen, um Hochverfügbarkeit und Anwendungsresilienz zu gewährleisten.
* **[VPN & Direct Connect](vpn_direct_connect.md):** Verbinden Sie Ihre lokalen Rechenzentren sicher mit Ihrer isolierten Cloud-Umgebung.

## Netzwerkisolierung & Souveränität

Standardmäßig sind alle Mandanten-VPCs auf Layer 2 und Layer 3 streng voneinander isoliert. Sie behalten die vollständige Kontrolle über den eingehenden und ausgehenden Datenverkehr und stellen so sicher, dass Ihre Netzwerkarchitektur perfekt mit strengen Richtlinien zur Datensouveränität und Sicherheits-Compliance übereinstimmt.