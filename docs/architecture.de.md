# SovereignSecure Cloud Plattform Architektur

<figure markdown="span">
  ![Image title](assets/az.png){ width="600"}
  <figcaption>Bereitstellungsarchitektur</figcaption>
</figure>

Die SovereignSecure Cloud Plattform wurde entwickelt, um eine sichere, konforme und hochleistungsfähige Cloud-Umgebung bereitzustellen. Unsere Architektur basiert auf einer robusten Grundlage von Open-Source-Technologien, hauptsächlich OpenStack, und ist mit Datensouveränität und operativer Autonomie als Kernprinzipien konzipiert. Dieses Dokument beschreibt die wichtigsten Architekturschichten und Komponenten, die die SovereignSecure Cloud bilden.

---

## Kernarchitekturprinzipien

Unsere Plattform ist nach folgenden Prinzipien konzipiert:

*   **Modularität:** Komponenten sind lose gekoppelt, was eine unabhängige Skalierung und Upgrades ermöglicht.
*   **Skalierbarkeit:** Horizontal skalierbar, um den wachsenden Bedarf an Compute-, Speicher- und Netzwerkressourcen zu decken.
*   **Security-by-Design:** Jede Schicht enthält Sicherheitsmaßnahmen, von der physischen Hardware bis zu softwaredefinierten Richtlinien.
*   **Open-Source-Grundlage:** Die Nutzung von OpenStack und anderen Open-Source-Projekten gewährleistet Transparenz, Auditierbarkeit und vermeidet Vendor Lock-in.
*   **Hochverfügbarkeit:** Kritische Dienste werden redundant über mehrere Verfügbarkeitszonen hinweg bereitgestellt, um einen kontinuierlichen Betrieb zu gewährleisten.

---

## Architekturschichten

Die SovereignSecure Cloud Architektur kann grob in drei Hauptschichten unterteilt werden:

### 1. Physische Infrastruktur (Underlay)

Diese Schicht umfasst die grundlegenden Hardwarekomponenten, die die rohen Compute-, Speicher- und Netzwerkfunktionen bereitstellen. Sie ist das physische Rückgrat, auf dem die gesamte softwaredefinierte Cloud aufgebaut ist.

#### Allgemeine Knotenanforderungen
Standardmäßige Enterprise-Server bilden die Basis unserer Cloud-Knoten. Während spezifische Konfigurationen je nach Rolle variieren, umfassen die allgemeinen Anforderungen:

### Netzwerk-Switches
Die Netzwerkinfrastruktur basiert typischerweise auf Hochleistungs-Switches, die moderne Protokolle unterstützen:

*   **Management-Switch:** 1 GbE oder 10 GbE für Out-of-Band-Management (IPMI/BMC).
*   **Daten-/Leaf-Switches:** 25 GbE oder 100 GbE Switches (z. B. Celestica, Edgecore oder Dell) mit **SONiC** oder anderen offenen Netzwerkbetriebssystemen.

---

### 2. Software-Defined Infrastructure (SDI) - Der Cloud-Fabric

Diese Schicht virtualisiert und orchestriert die physischen Ressourcen und präsentiert sie als eine einheitliche, programmierbare Cloud. OpenStack dient als Kern-IaaS-Plattform, die diese Ressourcen über APIs verwaltet und bereitstellt.

#### Management-Ebene
Die Management-Ebene ist für die gesamte Orchestrierung, Bereitstellung und das Lebenszyklusmanagement der Cloud-Infrastruktur selbst verantwortlich.

*   **Manager-Knoten:** Diese Knoten führen wesentliche Dienste für den Cloud-Betrieb aus, darunter:
    *   **Ansible:** Für automatisiertes Konfigurationsmanagement und Bereitstellung.
    *   **Docker Registry:** Zum Speichern und Verteilen von Container-Images für interne Dienste.
    *   **Netbox:** Für IP Address Management (IPAM) und Data Center Infrastructure Management (DCIM).
    *   **Observability & Security Tools:** Für Überwachung, Protokollierung und Sicherheitsereignismanagement der Cloud-Plattform.

#### Kontroll-Ebene
Die Kontroll-Ebene bietet die Kern-APIs und -Dienste, mit denen Benutzer interagieren, um ihre Cloud-Ressourcen bereitzustellen und zu verwalten.

*   **Kontroll-Knoten:** Diese Knoten hosten kritische OpenStack-Dienste:
    *   **OpenStack APIs (Keystone, Nova, Neutron, Cinder, Glance, etc.):** Die Einstiegspunkte für alle Cloud-Operationen.
    *   **Datenbanken (z. B. MariaDB, PostgreSQL):** Speichern den Zustand und die Konfiguration der Cloud.
    *   **Nachrichtenwarteschlangen (z. B. RabbitMQ):** Erleichtern die Kommunikation zwischen verschiedenen OpenStack-Diensten.
    *   **Spezifikationen:** Erfordern typischerweise 16+ Cores CPU, 128 GB - 256 GB RAM und RAID 1 NVMe für System/Datenbanken.

#### Compute-Ebene
Die Compute-Ebene ist der Ort, an dem Benutzer-Workloads (virtuelle Maschinen) ausgeführt werden.

*   **Compute-Knoten:** Diese Knoten führen den OpenStack Nova-Dienst aus und hosten virtuelle Maschinen (VMs).
    *   **Spezifikationen:** Verfügen über CPUs mit hoher Kernanzahl für VM-Dichte, 256 GB - 1 TB+ RAM je nach Workload und Dual-Port 25/100 GbE NICs.

#### Speicher-Ebene
Die Speicher-Ebene bietet persistenten und hochverfügbaren Speicher für alle Cloud-Ressourcen.

*   **Speicher-Knoten (Ceph OSDs):** Diese Knoten bilden das verteilte Speicher-Backend, das von Ceph betrieben wird. Sie bieten Block-Speicher (OpenStack Cinder), Objekt-Speicher (S3-kompatibel) und gemeinsame Dateisysteme (CephFS).
    *   **Spezifikationen:** Typischerweise 8-16 Cores CPU, 64 GB - 128 GB RAM (~1 GB RAM pro 1 TB OSD-Speicher) und 4-12+ NVMe oder SAS/SATA SSDs für Daten, mit dediziertem NVMe für WAL/DB.

#### Netzwerk-Ebene
Die Netzwerk-Ebene bietet virtuelle Netzwerkfunktionen, die eine isolierte und sichere Kommunikation für Mandantenressourcen ermöglichen.

*   **Netzwerk-Knoten:** Diese Knoten verwalten die softwaredefinierten Netzwerkkomponenten (SDN), einschließlich:
    *   **OpenStack Neutron:** Der primäre Netzwerkdienst zum Erstellen virtueller Netzwerke, Subnetze, Router und Sicherheitsgruppen.
    *   **OVN (Open Virtual Network):** Bietet das virtuelle Overlay-Netzwerk, das verteiltes Routing und die Durchsetzung von Sicherheitsgruppen auf Hypervisor-Ebene ermöglicht.

---

### 3. Platform as a Service (PaaS) Schicht

Aufbauend auf der SDI-Schicht bietet die PaaS-Schicht höhere Dienste, die die Infrastrukturverwaltung abstrahieren, sodass sich Benutzer auf die Anwendungsentwicklung konzentrieren können.

*   **Container-Orchestrierung (KaaS):** Verwaltete Kubernetes-Dienste für die Bereitstellung und Skalierung von containerisierten Anwendungen.
*   **Database as a Service (DBaaS):** Vollständig verwaltete relationale und NoSQL-Datenbankangebote.
*   Weitere spezialisierte Dienste wie AI/ML-Plattformen, Nachrichtenwarteschlangen usw.

---

## 3. Spezifische Rollenkonfigurationen

### Kontroll-Knoten
*   **CPU:** 16+ Cores.
*   **RAM:** 128 GB - 256 GB.
*   **Disk:** RAID 1 NVMe für System/Datenbanken.

### Compute-Knoten
*   **CPU:** Hohe Kernanzahl für VM-Dichte.
*   **RAM:** 256 GB - 1 TB+ je nach Workload-Anforderungen.
*   **NIC:** Dual-Port 25/100 GbE.

### Speicher-Knoten (Ceph)
*   **CPU:** 8-16 Cores.
*   **RAM:** 64 GB - 128 GB (Faustregel: ~1 GB RAM pro 1 TB OSD-Speicher).
*   **Disk:** 4-12+ NVMe oder SAS/SATA SSDs für Daten; dediziertes NVMe für WAL/DB.

---

## 4. Zusammenfassung des Software-Stacks

| Schicht | Empfohlene Komponente |
| :--- | :--- |
| **Betriebssystem** | Ubuntu 24.04 LTS |
| **IaaS** | OpenStack |
| **SDS (Speicher)** | Ceph |
| **SDN (Netzwerk)** | SONiC & OVN |
| **Kubernetes** | K3s |
| **Identitätsmanagement** | Keycloak |

> **Hinweis:** Die aufgeführten Marken, Modelle und Konfigurationen sind Beispiele. Es gibt keine einzige beste Spezifikation für jeden Anwendungsfall. Es ist jedoch wichtig, die zugrunde liegende Hardware bei der Gestaltung einer Cloud-Infrastruktur zu berücksichtigen.