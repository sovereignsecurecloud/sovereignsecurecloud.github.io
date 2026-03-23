---
sidebar_label: Cluster bereitstellen
---

# Bereitstellen von Kubernetes-Clustern

Die SovereignSecure Cloud bietet mehrere Möglichkeiten, Ihre Kubernetes-Cluster bereitzustellen und zu verwalten, unabhängig davon, ob Sie einen visuellen, UI-gesteuerten Ansatz oder einen vollständig automatisierten Workflow über Infrastructure as Code (IaC) bevorzugen.

## Bereitstellungsmethoden

### 1. Cloud Management Platform (CMP)

Der einfachste Weg für den Einstieg ist die Nutzung der Self-Service-Kataloge innerhalb der CMP. 

* **KaaS (Managed Kubernetes):** Navigieren Sie zum **Servicekatalog** und wählen Sie den Blueprint **Kubernetes Cluster**. Sie werden aufgefordert, die Kubernetes-Version, die Anzahl der Control-Plane-Knoten (für Hochverfügbarkeit) und die Größe/Anzahl Ihrer Worker-Knoten auszuwählen. Die CMP orchestriert die zugrunde liegende Cluster API (CAPI)-Bereitstellung für Sie.
* **K3s (Leichtgewichtig):** Wählen Sie den Blueprint **K3s Edge Cluster**. Dadurch wird schnell eine schlanke Instanz mit einem vorkonfigurierten Betriebssystem-Image bereitgestellt und eine Single-Node- oder Multi-Node-K3s-Umgebung initialisiert.

### 2. Infrastructure as Code (Terraform / OpenTofu)

Für Produktionsumgebungen und CI/CD-Integration empfehlen wir dringend, Ihre Cluster als Code zu definieren.

* **Verwendung der Cluster API:** Sie können den Kubernetes-Provider verwenden, um Standard-CAPI-YAML-Definitionen direkt auf unseren Management-Cluster anzuwenden. Dadurch werden Ihre Workload-Cluster auf OpenStack automatisch erzeugt (gespawnt).
* **Verwendung des OpenStack-Providers:** Sie können den standardmäßigen Terraform-OpenStack-Provider verwenden, um Compute-Instanzen, Netzwerke und Load Balancer bereitzustellen, und dann `cloud-init`-Benutzerskripte (User Scripts) verwenden, um Ihre eigenen K3s- oder Standard-Kubernetes-Distributionen zu bootstrappen.

## Zugriff auf Ihren Cluster

Sobald Ihr Cluster bereitgestellt ist, müssen Sie Ihre `kubeconfig`-Datei abrufen, um über die `kubectl`-CLI damit zu interagieren.

### Über CMP
Wenn Sie den Cluster über den CMP-Servicekatalog bereitgestellt haben, navigieren Sie zur Detailseite Ihres bereitgestellten Service. Dort finden Sie einen sicheren Download-Link oder einen Textblock, der Ihre `kubeconfig` enthält.

### Über CLI / CAPI
Wenn Sie den Cluster über die Cluster API verwalten, wird die `kubeconfig` als Standard-Kubernetes-Secret im Management-Cluster gespeichert. Sie können es wie folgt extrahieren:

```bash
kubectl --namespace default get secret <cluster-name>-kubeconfig \
   -o jsonpath={.data.value} | base64 --decode > sovereign-kubeconfig
```