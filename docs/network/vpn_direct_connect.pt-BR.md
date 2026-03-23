---
sidebar_label: VPN e Conexão Direta
---

# VPN e Conexão Direta

Cargas de trabalho corporativas frequentemente exigem conectividade privada e segura que contorne a internet pública. A SovereignSecure Cloud fornece gateways de rede seguros para conectar seus data centers locais (on-premises) ou filiais diretamente às suas Nuvens Privadas Virtuais (VPCs) isoladas.

## VPN as a Service (VPNaaS)

Nossa oferta VPNaaS, nativa do OpenStack Neutron, permite que você estabeleça túneis **VPN Site-to-Site IPsec** seguros e criptografados pela internet.

* **Túneis Criptografados:** Usa protocolos de criptografia padrão da indústria (AES-256, IKEv2) para proteger dados em trânsito.
* **Integração Perfeita:** As instâncias dentro da sua VPC na nuvem podem se comunicar com seus servidores locais usando seus endereços IP privados, como se estivessem na mesma rede local.
* **Autoatendimento:** Conexões VPNaaS podem ser totalmente configuradas e gerenciadas diretamente através do CMP em **Redes > VPN** (Network > VPN).

## Interconexão Dedicada (Conexão Direta)

Para organizações que exigem o mais alto nível de segurança, largura de banda massiva e desempenho consistente de baixa latência, oferecemos Interconexões Dedicadas.

* **Fibra Física:** Provisione uma conexão cruzada (cross-connect) física dedicada de sua rede corporativa ou instalação de colocation diretamente em nossa malha (fabric) física de rede SONiC.
* **Roteamento BGP:** Suporta roteamento dinâmico via BGP, compartilhando rotas automaticamente entre seus roteadores locais e suas VPCs na nuvem.

*Para solicitar uma Interconexão Dedicada, abra um ticket no Portal de Suporte para coordenar com nossa equipe de operações de data center.*