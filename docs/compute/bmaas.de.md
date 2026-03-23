---
sidebar_label: Bare Metal (BMaaS)
---

# Bare Metal as a Service (BMaaS)

Die SovereignSecure Cloud bietet **Bare Metal as a Service (BMaaS)**, angetrieben von **OpenStack Ironic**. BMaaS ermöglicht es Ihnen, dedizierte physische Server mit derselben automatisierten, API-gesteuerten Einfachheit wie virtuelle Maschinen bereitzustellen und zu verwalten.

## Vorteile von Bare Metal

Während virtuelle Maschinen für die meisten Workloads ideal sind, erfordern bestimmte Anwendungsfälle rohe Hardware:

* **Kein Hypervisor-Overhead:** Erreichen Sie 100 % der Rechen-, Speicher- und E/A-Leistung der Hardware ohne die Abstraktionskosten eines Hypervisors.
* **Isolierung auf Hardwareebene:** Perfekt für die strengsten Sicherheits- und Compliance-Regime, die eine mandantenfähige Hardwarefreigabe (Multi-Tenant) verbieten.
* **Spezielle Hardwareanforderungen:** Direkter Zugriff auf spezielle Hardwarefunktionen, Low-Level-CPU-Befehlssätze oder bestimmte PCI-Geräte.
* **Verschachtelte Virtualisierung (Nested Virtualization):** Bringen Sie Ihren eigenen Hypervisor (BYOH) mit. Sie können Ihren eigenen Virtualisierungs-Stack (wie Proxmox oder VMware) direkt auf unseren Bare-Metal-Instanzen ausführen.

## Wie es funktioniert

Über die Cloud Management Platform (CMP) oder die OpenStack-CLI können Sie ein Bare-Metal-Flavor anstelle eines Standard-VM-Flavors auswählen. 

1. Der Dienst **Ironic** löscht die physische Festplatte der Zielmaschine sicher.
2. Der Server wird über das Netzwerk (PXE) gestartet und das von Ihnen gewählte Betriebssystem-Image wird direkt auf das physische Laufwerk geflasht (geschrieben).
3. Die Maschine wird mit Ihrer VPC verbunden und arbeitet sicher innerhalb Ihrer privaten SDN-Schicht.