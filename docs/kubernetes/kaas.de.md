---
sidebar_label: KaaS (Cluster API)
---

# Kubernetes as a Service (KaaS)

Die SovereignSecure Cloud bietet unternehmenstaugliches **Kubernetes as a Service (KaaS)** unter Verwendung der **Cluster API (CAPI)**. 

## Integration der Cluster API (CAPI)

Die Cluster API ist ein Kubernetes-Projekt, das deklarative, im Kubernetes-Stil gehaltene APIs für die Erstellung, Konfiguration und Verwaltung von Clustern einführt. 

Anstatt OpenStack-Instanzen manuell bereitzustellen und Kubernetes zu installieren, ermöglicht Ihnen CAPI, den gewünschten Zustand Ihres Clusters in einer YAML-Datei zu definieren.

* **Deklaratives Management:** Definieren Sie die Anzahl der Control Plane-Knoten, Worker-Knoten und Kubernetes-Versionen als Code (as Code).
* **Automatisierung des Lebenszyklus:** Aktualisieren Sie Kubernetes-Versionen ganz einfach, skalieren Sie Worker-Knoten herauf oder herunter oder ersetzen Sie fehlerhafte Knoten automatisch.
* **Native OpenStack-Synergie:** Unser CAPI-Provider interagiert direkt mit OpenStack Nova, Neutron und Octavia, um automatisch die für Ihren Cluster erforderlichen VMs, Load Balancer und Sicherheitsgruppen bereitzustellen.

## Erste Schritte

Sie können direkt über den Self-Service-Katalog der Cloud Management Platform (CMP) einen neuen Managed Kubernetes-Cluster anfordern. Die CMP orchestriert dann die CAPI-Bereitstellung für Sie.