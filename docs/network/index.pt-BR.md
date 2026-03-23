---
sidebar_label: Visão Geral
sidebar_position: 1
---

# Visão Geral de Redes

Bem-vindo à documentação de Redes da SovereignSecure Cloud. Nossos serviços de rede fornecem a conectividade fundamental, o isolamento e a segurança necessários para construir arquiteturas de nuvem robustas e em conformidade.

Com a tecnologia de uma pilha moderna de Rede Definida por Software (SDN) utilizando SONiC e OVN, integrada nativamente com o OpenStack Neutron, oferecemos uma malha (fabric) de rede altamente escalável e segura.

## Serviços Principais de Rede

Explore as seções a seguir para aprender a arquitetar e gerenciar seus recursos de rede:

* **[Arquitetura SDN](sdn.md):** Entenda as tecnologias subjacentes de Rede Definida por Software (SONiC e OVN) que impulsionam nossa malha segura e escalável.
* **[VPC e Sub-redes](vpc.md):** Aprenda a criar Nuvens Privadas Virtuais (VPCs) isoladas e particioná-las em Sub-redes para organizar seus recursos.
* **[Roteadores e IPs Flutuantes](routers_fips.md):** Descubra como rotear o tráfego entre suas sub-redes internas e gerenciar o acesso externo usando IPs Flutuantes.
* **[Grupos de Segurança](security_group.md):** Implemente a segurança de confiança zero (zero-trust) configurando regras de firewall stateful e distribuídas no nível da instância.
* **[Balanceadores de Carga](load_balancer.md):** Distribua o tráfego de entrada em várias instâncias para garantir alta disponibilidade e resiliência do aplicativo.

## Isolamento de Rede e Soberania

Por padrão, todas as VPCs de locatários (tenants) são estritamente isoladas umas das outras na Camada 2 e na Camada 3. Você mantém controle total sobre o tráfego de entrada (ingress) e saída (egress), garantindo que sua arquitetura de rede se alinhe perfeitamente a estruturas rigorosas de soberania de dados e conformidade de segurança.