---
sidebar_label: Infraestrutura como Código (IaC)
sidebar_position: 3
---

# Infraestrutura como Código (IaC)

A SovereignSecure Cloud suporta nativamente fluxos de trabalho de Infraestrutura como Código (IaC), permitindo que você gerencie e provisione seus recursos de nuvem usando arquivos de definição legíveis por máquina. Essa abordagem garante consistência, repetibilidade e controle de versão para sua infraestrutura.

Nossa plataforma é totalmente compatível com ferramentas populares de IaC, como **Terraform** e **OpenTofu**, por meio do provedor padrão do OpenStack.

## Pré-requisitos

1.  **Instalar Terraform ou OpenTofu:** Baixe e instale a ferramenta de linha de comando (CLI) para o seu sistema operacional.
2.  **Detalhes de Autenticação:** Certifique-se de ter seu arquivo `clouds.yaml` configurado, ou de ter carregado (sourced) seu arquivo `openrc.sh` conforme descrito no guia de Configuração da CLI.

## Configurando o Provedor

Para começar a gerenciar os recursos da SovereignSecure Cloud, você precisa configurar o provedor do OpenStack em seus arquivos de configuração (ex.: `main.tf`).

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

# Se você estiver usando clouds.yaml, especifique o nome da nuvem:
provider "openstack" {
  cloud = "openstack"
}
```

## Exemplo: Provisionando uma Instância

Aqui está um exemplo básico de provisionamento de uma instância de computação usando Terraform/OpenTofu:

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