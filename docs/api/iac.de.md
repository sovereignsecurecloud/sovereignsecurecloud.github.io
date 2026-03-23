---
sidebar_label: Infrastructure as Code (IaC)
sidebar_position: 3
---

# Infrastructure as Code (IaC)

SovereignSecure Cloud unterstützt nativ Workflows für Infrastructure as Code (IaC), sodass Sie Ihre Cloud-Ressourcen mithilfe maschinenlesbarer Definitionsdateien verwalten und bereitstellen können. Dieser Ansatz gewährleistet Konsistenz, Wiederholbarkeit und Versionskontrolle für Ihre Infrastruktur.

Unsere Plattform ist über den Standard-OpenStack-Anbieter vollständig kompatibel mit beliebten IaC-Tools wie **Terraform** und **OpenTofu**.

## Voraussetzungen

1.  **Terraform oder OpenTofu installieren:** Laden Sie das CLI-Tool für Ihr Betriebssystem herunter und installieren Sie es.
2.  **Authentifizierungsdetails:** Stellen Sie sicher, dass Ihre Datei `clouds.yaml` konfiguriert ist oder dass Sie Ihre `openrc.sh`-Datei gesourct haben, wie im Leitfaden zur CLI-Konfiguration beschrieben.

## Den Provider konfigurieren

Um mit der Verwaltung von SovereignSecure Cloud-Ressourcen zu beginnen, müssen Sie den OpenStack-Provider in Ihren Konfigurationsdateien (z. B. `main.tf`) einrichten.

```hcl
terraform {
  required_version = ">= 1.0.0"
  required_providers {
    openstack = {
      source  = "terraform-provider-openstack/openstack"
      version = "~> 1.50.0"
    }
  }
}

# Wenn Sie clouds.yaml verwenden, geben Sie den Cloud-Namen an:
provider "openstack" {
  cloud = "openstack"
}
```

## Beispiel: Bereitstellung einer Instanz

Hier ist ein einfaches Beispiel für die Bereitstellung einer Compute-Instanz mit Terraform/OpenTofu:

```hcl
resource "openstack_compute_instance_v2" "my_instance" {
  name            = "terraform-instance"
  image_name      = "Ubuntu 22.04 LTS"
  flavor_name     = "t1.micro"
  key_pair        = "my-ssh-key"
  security_groups = ["default"]
  
  network {
    name = "my-internal-network"
  }
}
```