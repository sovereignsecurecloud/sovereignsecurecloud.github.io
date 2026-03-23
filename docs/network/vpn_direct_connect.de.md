---
sidebar_label: VPN & Direct Connect
---

# VPN & Direct Connect

Unternehmens-Workloads erfordern oft eine private, sichere Konnektivität, die das öffentliche Internet umgeht. Die SovereignSecure Cloud bietet sichere Netzwerk-Gateways, um Ihre lokalen Rechenzentren oder Außenstellen direkt mit Ihren isolierten Virtual Private Clouds (VPCs) zu verbinden.

## VPN as a Service (VPNaaS)

Unser in OpenStack Neutron integriertes VPNaaS-Angebot ermöglicht es Ihnen, sichere, verschlüsselte **IPsec Site-to-Site VPN**-Tunnel über das Internet einzurichten.

* **Verschlüsselte Tunnel:** Verwendet branchenübliche Verschlüsselungsprotokolle (AES-256, IKEv2), um Daten während der Übertragung zu sichern.
* **Nahtlose Integration:** Instanzen innerhalb Ihrer Cloud-VPC können mit Ihren lokalen Servern über deren private IP-Adressen kommunizieren, als befänden sie sich im selben lokalen Netzwerk.
* **Self-Service:** VPNaaS-Verbindungen können vollständig über das CMP unter **Netzwerk > VPN** konfiguriert und verwaltet werden.

## Dedizierte Zusammenschaltung (Direct Connect)

Für Organisationen, die das höchste Maß an Sicherheit, massiver Bandbreite und konsistenter Leistung mit geringer Latenz benötigen, bieten wir dedizierte Zusammenschaltungen an.

* **Physische Glasfaser:** Stellen Sie eine dedizierte physische Querverbindung (Cross-Connect) von Ihrem Unternehmensnetzwerk oder Ihrer Colocation-Einrichtung direkt in unsere physische SONiC-Netzwerk-Fabric bereit.
* **BGP-Routing:** Unterstützt dynamisches Routing über BGP und teilt automatisch Routen zwischen Ihren lokalen Routern und Ihren Cloud-VPCs.

*Um eine dedizierte Zusammenschaltung anzufordern, erstellen Sie bitte ein Ticket über das Support-Portal, um sich mit unserem Rechenzentrums-Betriebsteam abzustimmen.*