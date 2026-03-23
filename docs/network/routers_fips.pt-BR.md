---
sidebar_label: Roteadores e IPs Flutuantes
---

# Roteadores e IPs Flutuantes

Embora uma Nuvem Privada Virtual (VPC) forneça segmentos de rede isolados da Camada 2 (sub-redes), você precisa de **Roteadores** para permitir a comunicação da Camada 3 entre essas sub-redes e o mundo exterior. Para expor seus recursos à internet pública, você usa **IPs Flutuantes (Floating IPs)**.

## Roteadores Virtuais

Na SovereignSecure Cloud, um Roteador Virtual funciona de forma semelhante a um roteador físico em um data center tradicional. Com a tecnologia da nossa camada SDN OVN distribuída, o roteamento geralmente acontece diretamente na borda do hypervisor, fornecendo uma entrega de pacotes altamente eficiente.

### Principais Capacidades

* **Roteamento de Sub-rede:** Conecte várias sub-redes privadas dentro da mesma VPC, permitindo que instâncias em diferentes sub-redes se comuniquem entre si.
* **Gateway Externo (SNAT):** Ao anexar um roteador à Rede Externa (Internet), as instâncias dentro de suas sub-redes privadas obtêm acesso de saída à internet (Source NAT). Isso permite que as instâncias baixem atualizações ou acessem APIs externas sem serem diretamente alcançáveis a partir do exterior.

## IPs Flutuantes (FIPs)

Um **IP Flutuante** é um endereço IP roteável publicamente que você pode associar e desassociar dinamicamente a uma Instância de Computação ou Balanceador de Carga.

### Como Funciona

* **Presença Pública Estática:** As instâncias normalmente têm apenas endereços IP privados (ex.: `10.0.1.5`). Um IP Flutuante fornece um IP público e estático (ex.: `203.0.113.10`).
* **NAT 1-para-1:** O Roteador Virtual lida com a Tradução de Endereço de Rede (NAT) 1-para-1 entre o IP Flutuante público e o IP privado da instância. A própria instância não tem conhecimento de seu IP público.
* **Alta Disponibilidade:** Se uma instância falhar, você pode remapear instantaneamente seu IP Flutuante para uma instância em espera (standby), minimizando o tempo de inatividade para o endpoint público do seu aplicativo.

## Passos de Configuração

### 1. Criar um Roteador
1. Navegue até **Redes > Roteadores** na Plataforma de Gerenciamento de Nuvem (CMP).
2. Clique em **Criar Roteador**, dê um nome a ele e selecione a **Rede Externa** para permitir o acesso de saída à internet.
3. Depois de criado, clique no roteador, navegue até **Interfaces** e clique em **Adicionar Interface** para conectar suas sub-redes VPC internas.

### 2. Alocar e Associar um IP Flutuante
1. Navegue até **Redes > IPs Flutuantes**.
2. Clique em **Alocar IP ao Projeto** para extrair um novo IP público do pool do provedor.
3. Selecione o IP recém-alocado e clique em **Associar**.
4. Escolha a porta da instância (IP privado) para a qual deseja mapear o IP Flutuante.

!!! tip "Segurança em Primeiro Lugar"
    Anexar um IP Flutuante torna sua instância acessível publicamente. Certifique-se de ter configurado corretamente os **Grupos de Segurança** para restringir o tráfego de entrada apenas às portas necessárias (ex.: porta 443 para HTTPS ou porta 22 para SSH).