---
sidebar_label: SDN (SONiC & OVN)
---

# Software Defined Networking (SDN)

SovereignSecure Cloud setzt eine moderne Software-Defined Networking (SDN)-Architektur ein, um skalierbare, sichere und isolierte Kommunikation zu gewährleisten. Unsere Netzwerk-Fabric basiert auf der leistungsstarken Kombination von **SONiC** und **OVN**.

## Physisches Underlay: SONiC

**SONiC (Software for Open Networking in the Cloud)** ist ein auf Linux basierendes Open-Source-Netzwerkbetriebssystem, das auf Switches verschiedener Anbieter läuft. 

* **Anbieterunabhängig:** Befreit die Infrastruktur von den Einschränkungen proprietärer Netzwerk-Hardware.
* **Hohe Leistung:** Bietet das robuste, extrem schnelle physische Routing-Underlay (Layer 3), das für massiv skalierbare Clouds erforderlich ist.

## Virtuelles Overlay: OVN (Open Virtual Network)

**OVN** dient als Steuerungsebene (Control Plane) für unsere virtuellen Netzwerke und lässt sich nativ in OpenStack Neutron integrieren.

* **Virtual Private Clouds (VPC):** OVN erstellt isolierte Layer 2- und Layer 3-Topologien für Mandanten über dem physischen SONiC-Underlay unter Verwendung von GENEVE-Tunneling.
* **Verteiltes Routing:** Das Routing zwischen Subnetzen erfolgt auf Hypervisor-Ebene, wodurch Netzwerkengpässe und Tromboning reduziert werden.
* **Verteilte Sicherheitsgruppen:** Firewall-Regeln werden auf der Ebene des virtuellen Ports (OVS) implementiert, wodurch Zero-Trust-Netzwerke zwischen Instanzen auch innerhalb desselben Subnetzes gewährleistet werden.