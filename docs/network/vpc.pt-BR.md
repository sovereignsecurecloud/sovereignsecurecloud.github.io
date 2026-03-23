---
sidebar_label: VPC e Sub-redes
---

# Nuvem Privada Virtual (VPC) e Sub-redes

Na SovereignSecure Cloud, uma **Nuvem Privada Virtual (VPC)** é uma topologia de rede privada e logicamente isolada dedicada ao seu projeto. Com a tecnologia da nossa pilha SDN OVN/SONiC, ela fornece controle total sobre o seu ambiente de rede, incluindo intervalos de endereços IP, sub-redes e roteamento.

## Nuvens Privadas Virtuais (VPCs)

Uma VPC atua como o limite fundamental para os seus recursos de nuvem. Por padrão, os recursos implantados em uma VPC não podem se comunicar com a internet externa ou com outras VPCs, a menos que sejam explicitamente configurados para isso por meio de Roteadores e IPs Flutuantes.

**Principais Características:**
*   **Isolamento Absoluto:** Cada VPC é totalmente isolada na Camada 2 e na Camada 3, garantindo limites soberanos entre diferentes locatários (tenants) e projetos.
*   **Topologia Personalizada:** Você pode definir seu próprio espaço de endereço IP interno (ex.: `10.0.0.0/16` ou `192.168.1.0/24`) sem se preocupar com a sobreposição com outros locatários.

## Sub-redes

Uma **Sub-rede** é uma porção segmentada do intervalo de endereços IP de uma VPC onde você pode colocar grupos de recursos isolados. Ao iniciar uma Instância de Computação, você a conecta a uma ou mais sub-redes específicas.

**Recursos da Sub-rede:**
*   **Blocos CIDR:** Você especifica o bloco exato de Roteamento Interdomínio Sem Classe (CIDR) para cada sub-rede (ex.: `10.0.1.0/24`).
*   **DHCP e DNS:** Cada sub-rede possui um servidor DHCP integrado e de alta disponibilidade para atribuir automaticamente endereços IP às suas instâncias. A resolução de DNS interno também é fornecida por padrão para que as instâncias possam resolver umas às outras pelo nome do host.
*   **IP de Gateway:** As sub-redes normalmente reservam o primeiro endereço IP utilizável (ex.: `10.0.1.1`) como gateway padrão para rotear o tráfego para fora da sub-rede.

## Criando uma VPC e uma Sub-rede

Você pode projetar a topologia da sua rede diretamente pela Plataforma de Gerenciamento de Nuvem (CMP):

1. Navegue até **Redes > VPCs**.
2. Clique em **Criar VPC**.
3. Forneça um nome e uma descrição para a sua VPC.
4. Depois que a VPC for criada, clique nela e selecione **Criar Sub-rede** (Create Subnet).
5. Defina o Nome da Sub-rede, Endereço de Rede (CIDR) e IP do Gateway.
6. (Opcional) Configure pools de alocação de DHCP específicos ou servidores de nomes DNS personalizados para a sub-rede.

## Próximos Passos

Uma vez que a base da sua rede isolada esteja estabelecida, você provavelmente precisará:
*   Criar um **Roteador** para permitir que o tráfego flua entre sub-redes ou para a internet.
*   Anexar um **IP Flutuante** para tornar uma instância acessível publicamente.