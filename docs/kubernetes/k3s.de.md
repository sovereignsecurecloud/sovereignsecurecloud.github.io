---
sidebar_label: K3s Kubernetes
---

# Kubernetes mit K3s

Für Workloads, die eine schlanke, hocheffiziente Container-Orchestrierungsplattform erfordern, bietet die SovereignSecure Cloud Unterstützung für **K3s**.

## Was ist K3s?

K3s ist eine hochverfügbare, zertifizierte Kubernetes-Distribution, die für Produktions-Workloads in ressourcenbeschränkten, Edge- oder IoT-Umgebungen entwickelt wurde. Sie packt alle Kubernetes-Komponenten in ein einziges Binary.

## Hauptvorteile

* **Leichtgewichtig (Lightweight):** Hat im Vergleich zu Standard-Kubernetes einen sehr kleinen Speicherbedarf (Memory Footprint), wodurch mehr Ressourcen für Ihre eigentlichen Anwendungen zur Verfügung stehen.
* **Schnelle Bereitstellung:** Cluster booten unglaublich schnell, was sie ideal für kurzlebige (ephemere) CI/CD-Pipelines oder schnelle Skalierung macht.
* **Sicher als Standard (Secure by Default):** Mit Blick auf die Sicherheit entwickelt und bietet durch reduzierte Abhängigkeiten eine verringerte Angriffsfläche.

## Bereitstellung

K3s-Cluster können über unsere CMP-Servicekataloge sehr schnell hochgefahren oder über Infrastructure as Code (Terraform) auf SovereignSecure-Compute-Instanzen verwaltet werden.