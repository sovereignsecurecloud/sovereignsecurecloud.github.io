---
sidebar_label: Visão Geral
sidebar_position: 1
---

# Visão Geral de Instâncias

Uma **Instância** na SovereignSecure Cloud é uma máquina virtual (VM) escalável que fornece capacidade de computação sob demanda. Cada instância é composta por CPUs virtuais, memória e armazenamento de bloco raiz, permitindo que você implante e execute seus aplicativos e cargas de trabalho em um ambiente seguro e isolado.

Nosso serviço de instâncias utiliza a tecnologia do OpenStack Nova, oferecendo recursos de servidor virtual robustos e flexíveis que se integram perfeitamente a outros serviços da SovereignSecure Cloud.

## Principais Recursos

*   **Escalabilidade:** Escale facilmente seus recursos de computação para cima ou para baixo, alterando os flavors da instância para atender às demandas de sua carga de trabalho.
*   **Flexibilidade:** Escolha entre uma ampla variedade de imagens de sistemas operacionais, incluindo distribuições Linux populares e Windows Server.
*   **Integração de Rede:** Conecte instâncias às suas Nuvens Privadas Virtuais (VPCs) e sub-redes, permitindo uma comunicação de rede segura e privada.
*   **Segurança:** Utilize Grupos de Segurança para definir regras granulares de firewall, protegendo suas instâncias contra acesso não autorizado.
*   **Armazenamento Persistente:** As instâncias podem ser provisionadas com armazenamento de bloco persistente para o disco raiz, e volumes adicionais podem ser anexados para dados de aplicativos.
*   **API e Automação:** O suporte completo à API permite controle programático e automação do provisionamento e gerenciamento de instâncias.

## Componentes

Toda instância é construída usando os seguintes componentes principais:

*   **Flavor (Tamanho/Perfil):** Define a capacidade de computação (vCPUs e RAM) alocada à instância.
    *   Exemplos: `t1.micro`, `m1.small`, `c1.medium`
*   **Imagem:** O modelo de sistema operacional (ex.: Ubuntu, RHEL, Windows Server) usado como base para o disco raiz da sua instância.
*   **Armazenamento:**
    *   **Disco Raiz:** O volume primário de Armazenamento de Bloco onde o sistema operacional está instalado.
    *   **Volumes Adicionais:** Volumes persistentes de Armazenamento de Bloco que podem ser anexados a instâncias para dados de aplicativos, fornecendo durabilidade e flexibilidade.
*   **Rede:**
    *   **Interfaces de Rede Virtuais (Portas):** Conectam instâncias às sub-redes VPC definidas.
    *   **IP Flutuante:** Um endereço IP público opcional que pode ser associado a uma instância para acesso direto à Internet.
*   **Grupos de Segurança:** Firewalls virtuais que controlam o tráfego de rede de entrada e saída para as suas instâncias.
*   **Par de Chaves:** Usado para acesso SSH seguro a instâncias Linux.

## Ciclo de Vida da Instância

As instâncias normalmente seguem um ciclo de vida que inclui:

*   **Criação:** Provisionamento de uma nova instância a partir de uma imagem e flavor.
*   **Em Execução:** O estado ativo em que seus aplicativos estão operacionais.
*   **Parar/Iniciar:** Interromper ou retomar temporariamente uma instância.
*   **Redimensionamento:** Alterar o flavor da instância para ajustar seus recursos de computação.
*   **Criação de Snapshot:** Criar uma imagem a partir de uma instância em execução ou parada.
*   **Exclusão:** Encerrar permanentemente uma instância e seus recursos associados.

## Primeiros Passos

Para aprender a criar e gerenciar suas instâncias passo a passo, consulte o Guia do Usuário da Instância.