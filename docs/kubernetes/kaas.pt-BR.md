---
sidebar_label: KaaS (Cluster API)
---

# Kubernetes as a Service (KaaS)

A SovereignSecure Cloud fornece **Kubernetes as a Service (KaaS)** de nível corporativo utilizando a **Cluster API (CAPI)**.

## Integração com Cluster API (CAPI)

A Cluster API é um projeto do Kubernetes que traz APIs declarativas no estilo do Kubernetes para a criação, configuração e gerenciamento de clusters.

Em vez de provisionar instâncias do OpenStack e instalar o Kubernetes manualmente, a CAPI permite que você defina o estado desejado do seu cluster em um arquivo YAML.

* **Gerenciamento Declarativo:** Defina o número de nós do plano de controle (control plane), nós de trabalho (worker nodes) e versões do Kubernetes como código.
* **Automação do Ciclo de Vida:** Atualize facilmente as versões do Kubernetes, aumente ou diminua os nós de trabalho (scale up/down) ou substitua nós não saudáveis automaticamente.
* **Sinergia Nativa com o OpenStack:** Nosso provedor CAPI interage diretamente com o OpenStack Nova, Neutron e Octavia para provisionar automaticamente as VMs, balanceadores de carga e grupos de segurança necessários para o seu cluster.

## Primeiros Passos

Você pode solicitar um novo cluster Kubernetes Gerenciado diretamente pelo catálogo de autoatendimento da Plataforma de Gerenciamento de Nuvem (CMP), que orquestrará a implantação da CAPI em seu nome.