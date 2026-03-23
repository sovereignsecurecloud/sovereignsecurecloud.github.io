---
sidebar_label: Visão Geral
sidebar_position: 1
---

# Visão Geral da API

A SovereignSecure Cloud fornece acesso abrangente à API, permitindo que desenvolvedores e administradores de sistemas automatizem o provisionamento, a configuração e o gerenciamento da infraestrutura. 

Nosso ambiente utiliza duas camadas principais de APIs, dependendo de suas necessidades de automação:

1. **API da Plataforma de Gerenciamento de Nuvem (CMP) SovereignSecure**
2. **APIs de Infraestrutura Nativas do OpenStack**

## API da Plataforma de Gerenciamento de Nuvem (CMP)

A API do CMP é baseada no ManageIQ e é o ponto de entrada recomendado para usuários que buscam gerenciar o ciclo de vida de sua nuvem, solicitações de provisionamento, cotas e relatórios organizacionais. Ela fornece uma interface RESTful para a ferramenta de gerenciamento unificada.

- **Endpoint:** `https://portal.sovereignsecurecloud.com/api`
- **Autenticação:** Autenticação Básica (Basic Auth) ou baseada em Token
- **Melhor para:** Provisionamento de autoatendimento, catálogos de serviços, dados de chargeback/showback e gerenciamento organizacional multilocatário.

## APIs Nativas do OpenStack

Para automação profunda de infraestrutura, a SovereignSecure Cloud expõe APIs nativas padrão do OpenStack. Isso permite que você use ferramentas familiares como Terraform, OpenTofu, Ansible e a CLI padrão do OpenStack.

- **Identidade (Keystone):** Autenticação e descoberta de catálogo.
- **Computação (Nova):** Gerenciamento do ciclo de vida de instâncias.
- **Redes (Neutron):** VPCs, sub-redes, roteadores e IPs flutuantes.
- **Armazenamento de Bloco (Cinder):** Volumes e Snapshots.
- **Serviço de Imagem (Glance):** Imagens de SO e snapshots personalizados.