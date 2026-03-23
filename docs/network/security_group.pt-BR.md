---
sidebar_label: Grupos de Segurança
---

# Grupos de Segurança

Na SovereignSecure Cloud, um **Grupo de Segurança** atua como um firewall virtual stateful (que mantém o estado) que controla o tráfego de rede de entrada (ingress) e saída (egress) para as suas Instâncias de Computação. 

Com a tecnologia da nossa camada SDN OVN, as regras do grupo de segurança são distribuídas e aplicadas diretamente no nível da porta do hypervisor, garantindo uma rede de confiança zero (zero-trust) e impedindo o movimento lateral, mesmo entre instâncias na mesma sub-rede.

## Conceitos Principais

* **Negação Padrão (Ingress):** Por padrão, quando você cria um novo grupo de segurança, ele não contém regras de entrada. Isso significa que todo o tráfego de entrada para a instância é bloqueado até que você o permita explicitamente.
* **Permissão Padrão (Egress):** Por padrão, novos grupos de segurança incluem uma regra que permite todo o tráfego de saída, permitindo que as instâncias acessem a internet ou outros recursos.
* **Stateful:** Grupos de segurança são stateful. Se você permitir uma solicitação de entrada (ex.: HTTP na porta 443), o tráfego de retorno para essa conexão específica será permitido automaticamente, independentemente de suas regras de saída.
* **Múltiplos Grupos:** Você pode atribuir vários grupos de segurança a uma única instância. As permissões resultantes são a união de todas as regras dos grupos atribuídos.

## Anatomia de uma Regra

Quando você cria uma regra dentro de um grupo de segurança, você define:

* **Direção:** 
    * `Ingress` (Tráfego de entrada destinado à instância)
    * `Egress` (Tráfego de saída originado na instância)
* **EtherType:** `IPv4` ou `IPv6`.
* **Protocolo IP:** `TCP`, `UDP` ou `ICMP`.
* **Intervalo de Portas:** A porta específica ou o intervalo de portas a serem abertas (ex.: `22` para SSH, `80` para HTTP).
* **Remoto:** Define a origem (para Ingress) ou destino (para Egress) do tráfego. Isso pode ser:
    * **Bloco CIDR:** Um intervalo de endereços IP (ex.: `0.0.0.0/0` para toda a internet, ou `192.168.1.0/24` para uma sub-rede específica).
    * **Outro Grupo de Segurança:** Você pode permitir dinamicamente o tráfego de qualquer instância pertencente a outro grupo de segurança específico, o que é altamente útil para arquiteturas em camadas (ex.: permitir que seu grupo `Database` aceite tráfego apenas do seu grupo `Web Servers`).

## Melhores Práticas para uma Nuvem Soberana

* **Princípio do Menor Privilégio:** Nunca use `0.0.0.0/0` (permitir tudo) a menos que seja absolutamente necessário para serviços web voltados para o público. Restrinja portas administrativas como `22` (SSH) ou `3389` (RDP) aos intervalos de IP da sua VPN corporativa específica ou gateways Teleport.
* **Arquiteturas em Camadas:** Use referência a Grupos de Segurança em vez de IPs estáticos. Crie grupos separados como `frontend-sg`, `backend-sg` e `db-sg`. Permita que o `db-sg` aceite apenas a porta 3306 do `backend-sg`.

## Gerenciando Grupos de Segurança

Você pode gerenciar grupos de segurança por meio da Plataforma de Gerenciamento de Nuvem (CMP):

1. Navegue até **Redes > Grupos de Segurança**.
2. Clique em **Criar Grupo de Segurança** e forneça um nome descritivo (ex.: `web-server-ports`).
3. Selecione o novo grupo e clique em **Gerenciar Regras**.
4. Clique em **Adicionar Regra** para especificar o protocolo, a porta e o intervalo de IP remoto.

Para aplicar o grupo de segurança a uma instância:

* **Durante a Criação:** Selecione o grupo de segurança na aba Rede ao iniciar uma nova instância.
* **Pós-Criação:** Navegue até **Computação > Instâncias**, selecione sua instância e escolha **Editar Grupos de Segurança** no menu Ações.