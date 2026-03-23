---
sidebar_label: GPU-Instanzen
sidebar_position: 3
---

# GPU-Instanzen

Die SovereignSecure Cloud bietet spezialisierte virtuelle Maschinen-Instanzen, die mit GPUs ausgestattet sind. Diese Instanzen werden für rechenintensive Workloads wie maschinelles Lernen, KI-Training, 3D-Rendering und High-Performance Computing (HPC) dringend empfohlen.

## Erstellen von GPU-Instanzen

Sie können GPU-Instanzen entweder direkt über die Cloud-Konsole oder mithilfe von Infrastructure as Code (IaC)-Tools wie Terraform und OpenTofu erstellen. 

### Auswahl eines GPU-Flavors

Bei der Bereitstellung einer GPU-Instanz müssen Sie ein Flavor auswählen, das Hardwarebeschleunigung garantiert. In unserer Umgebung werden GPU-Flavors typischerweise durch das Präfix `g` gekennzeichnet.

| Flavor-Serie | Anwendungsfall |
| ----------- | ----------- |
| **g-Serie** | Allgemeine GPU-Workloads, maschinelles Lernen und Videoverarbeitung. |

### Überlegungen zum Image

Um die GPU-Hardware vollständig nutzen zu können, müssen auf dem Betriebssystem die richtigen NVIDIA-Grid- oder Passthrough-Treiber installiert sein. 

* Wir empfehlen die Auswahl eines der vorkonfigurierten **öffentlichen Images mit GPU-Unterstützung**, die von der SovereignSecure Cloud bereitgestellt werden und auf denen die erforderlichen Treiber und CUDA-Toolkits bereits vorinstalliert sind.
* Wenn Sie Ihr eigenes Image mitbringen, sind Sie dafür verantwortlich, die entsprechenden Treiber während des Starts über ein Benutzerskript (cloud-init) zu installieren.

### OS-Einstellungen

Genau wie bei Standardinstanzen müssen Sie festlegen, wie der Root-Blockspeicher erstellt wird:

* **Neu erstellen und einrichten:** Erstellen Sie ein neues Root-Block-Storage-Volume mithilfe eines ausgewählten Images. Stellen Sie sicher, dass die Festplattengröße die Mindestanforderungen für die Installation von GPU-Treibern erfüllt (in der Regel werden 40 GB+ empfohlen).
* **Vorhandene Ressource verwenden:** Starten Sie von einem zuvor erstellten Block-Storage-Volume oder Snapshot, das bzw. der bereits Ihre GPU-Umgebungskonfiguration enthält.

### Lebenszyklus & Abrechnung von GPU-Instanzen

GPU-Ressourcen sind stark nachgefragt und werden auf Hypervisor-Ebene mithilfe von PCI-Passthrough- oder vGPU-Profilen streng zugewiesen. Bitte beachten Sie die folgenden Betriebsgrenzen:

!!! warning "Hinweis zur Abrechnung"
    Da Hardware stark reserviert ist, fallen für **GPU-Instanzen die normalen (100 %) Gebühren an, auch wenn sie gestoppt sind**. Um die Abrechnung für eine GPU-Instanz vollständig zu stoppen, müssen Sie die Instanz **beenden (löschen)**. 

!!! note "Live-Migration"
    Aufgrund der Hardwarebindung von PCI-Geräten können GPU-Instanzen **nicht** live zwischen Hypervisoren migriert werden. Wartungsereignisse auf dem zugrunde liegenden Host erfordern, dass die Instanz vollständig heruntergefahren und auf einem neuen Host gestartet wird.