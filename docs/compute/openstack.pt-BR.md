---
sidebar_label: OpenStack IaaS
---

# Infraestrutura como Serviço (IaaS) com OpenStack

A SovereignSecure Cloud utiliza o **OpenStack** como sua plataforma principal de Infraestrutura como Serviço (IaaS). O OpenStack é um sistema operacional em nuvem de código aberto que controla grandes pools de recursos de computação, armazenamento e rede em todo um data center, todos gerenciados e provisionados por meio de APIs com mecanismos de autenticação comuns.

## Por que OpenStack para uma Nuvem Soberana?

Para manter uma verdadeira soberania de dados, você deve ter controle total sobre a pilha de infraestrutura subjacente. O OpenStack fornece:

* **Sem Dependência de Fornecedor (No Vendor Lock-in):** Construído inteiramente com tecnologias de código aberto, garantindo que sua infraestrutura não fique presa a softwares proprietários do tipo caixa-preta.
* **Base de Código Auditável:** A transparência do código aberto permite auditorias de segurança rigorosas exigidas por estruturas soberanas e de conformidade.
* **Escalabilidade Massiva:** Comprovado em escala pelos maiores provedores de telecomunicações e instalações de pesquisa do mundo.
* **Multilocação e Isolamento (Multi-Tenancy):** Aplicação estrita de limites entre diferentes projetos e locatários (tenants) para garantir a privacidade dos dados.

## Componentes Principais do OpenStack

Nosso ambiente integra vários serviços essenciais do OpenStack para oferecer uma experiência de nuvem perfeita:

* **Nova (Computação):** Provisiona e gerencia os ciclos de vida de instâncias de computação (Máquinas Virtuais).
* **Glance (Serviço de Imagem):** Descobre, registra e recupera imagens de máquinas virtuais.
* **Cinder (Armazenamento em Bloco):** Fornece volumes de armazenamento em bloco persistente para instâncias de computação.