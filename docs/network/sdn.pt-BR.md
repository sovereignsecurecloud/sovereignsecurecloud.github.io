---
sidebar_label: SDN (SONiC e OVN)
---

# Redes Definidas por Software (SDN)

A SovereignSecure Cloud emprega uma arquitetura moderna de Rede Definida por Software (SDN) para garantir comunicações escaláveis, seguras e isoladas. Nossa malha (fabric) de rede é construída sobre a poderosa combinação de **SONiC** e **OVN**.

## Underlay Físico: SONiC

**SONiC (Software for Open Networking in the Cloud)** é um sistema operacional de rede de código aberto baseado em Linux que roda em switches de vários fornecedores. 

* **Agnóstico de Fornecedor (Vendor Agnostic):** Liberta a infraestrutura das limitações de hardware de rede proprietário.
* **Alto Desempenho:** Fornece o underlay de roteamento físico (Camada 3) robusto e de alta velocidade necessário para a escala massiva da nuvem.

## Overlay Virtual: OVN (Open Virtual Network)

O **OVN** atua como o plano de controle para nossas redes virtuais, integrando-se nativamente ao OpenStack Neutron.

* **Nuvens Privadas Virtuais (VPC):** O OVN cria topologias isoladas de Camada 2 e Camada 3 para locatários (tenants) sobre o underlay físico do SONiC usando o tunelamento GENEVE.
* **Roteamento Distribuído:** O roteamento entre sub-redes acontece no nível do hypervisor, reduzindo gargalos de rede e o efeito trombone (tromboning).
* **Grupos de Segurança Distribuídos:** As regras de firewall são implementadas no nível da porta virtual (OVS), garantindo uma rede de confiança zero (zero-trust) entre as instâncias, mesmo dentro da mesma sub-rede.