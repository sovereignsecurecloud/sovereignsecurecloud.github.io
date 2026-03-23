---
sidebar_label: OpenStack IaaS
---

# Infrastructure as a Service (IaaS) mit OpenStack

Die SovereignSecure Cloud nutzt **OpenStack** als zentrale Infrastructure as a Service (IaaS)-Plattform. OpenStack ist ein Open-Source-Cloud-Betriebssystem, das große Pools von Rechen-, Speicher- und Netzwerkressourcen in einem gesamten Rechenzentrum steuert, die alle über APIs mit gemeinsamen Authentifizierungsmechanismen verwaltet und bereitgestellt werden.

## Warum OpenStack für eine Sovereign Cloud?

Um echte Datensouveränität zu wahren, müssen Sie die vollständige Kontrolle über den zugrunde liegenden Infrastruktur-Stack haben. OpenStack bietet:

* **Kein Vendor Lock-in:** Vollständig auf Open-Source-Technologien aufgebaut, was sicherstellt, dass Ihre Infrastruktur nicht an proprietäre Black-Box-Software gebunden ist.
* **Auditierbare Codebasis:** Die Transparenz von Open Source ermöglicht strenge Sicherheitsüberprüfungen, die von Souveränitäts- und Compliance-Frameworks gefordert werden.
* **Massive Skalierbarkeit:** In großem Maßstab von den weltweit größten Telekommunikationsanbietern und Forschungseinrichtungen erprobt.
* **Multi-Tenancy & Isolierung:** Strenge Grenzdurchsetzung zwischen verschiedenen Projekten und Mandanten (Tenants), um den Datenschutz zu gewährleisten.

## Zentrale OpenStack-Komponenten

Unsere Umgebung integriert mehrere wichtige OpenStack-Dienste, um ein nahtloses Cloud-Erlebnis zu bieten:

* **Nova (Compute):** Stellt Compute-Instanzen (virtuelle Maschinen) bereit und verwaltet deren Lebenszyklen.
* **Glance (Image Service):** Entdeckt, registriert und ruft Images für virtuelle Maschinen ab.
* **Cinder (Block Storage):** Stellt persistente Block-Storage-Volumes für Compute-Instanzen bereit.