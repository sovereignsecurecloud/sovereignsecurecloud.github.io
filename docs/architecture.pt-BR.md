# Arquitetura da Plataforma SovereignSecure Cloud

<figure markdown="span">
  ![Image title](assets/az.png){ width="600"}
  <figcaption>Arquitetura de Implantação</figcaption>
</figure>

A plataforma SovereignSecure Cloud é projetada para oferecer um ambiente de nuvem seguro, compatível e de alto desempenho. Nossa arquitetura é construída sobre uma base robusta de tecnologias de código aberto, principalmente OpenStack, e projetada com soberania de dados e autonomia operacional em seu núcleo. Este documento descreve as principais camadas arquitetônicas e componentes que constituem a SovereignSecure Cloud.

---

## Princípios Arquitetônicos Centrais

Nossa plataforma é projetada com base nos seguintes princípios:

*   **Modularidade:** Os componentes são fracamente acoplados, permitindo escalabilidade e atualizações independentes.
*   **Escalabilidade:** Projetada para escalar horizontalmente para atender à crescente demanda por recursos de computação, armazenamento e rede.
*   **Segurança por Design:** Cada camada incorpora medidas de segurança, desde o hardware físico até as políticas definidas por software.
*   **Base de Código Aberto:** O aproveitamento do OpenStack e de outros projetos de código aberto garante transparência, auditabilidade e evita o aprisionamento tecnológico (vendor lock-in).
*   **Alta Disponibilidade:** Serviços críticos são implantados de forma redundante em várias zonas de disponibilidade para garantir a operação contínua.

---

## Camadas Arquitetônicas

A arquitetura da SovereignSecure Cloud pode ser amplamente categorizada em três camadas principais:

### 1. Infraestrutura Física (Underlay)

Esta camada compreende os componentes de hardware fundamentais que fornecem as capacidades brutas de computação, armazenamento e rede. É a espinha dorsal física sobre a qual toda a nuvem definida por software é construída.

#### Requisitos Genéricos de Nó
Servidores de nível empresarial padrão formam a base de nossos nós de nuvem. Embora as configurações específicas variem por função, os requisitos gerais incluem:

### Switches de Rede
A infraestrutura de rede geralmente depende de switches de alto desempenho que suportam protocolos modernos:

*   **Switch de Gerenciamento:** 1 GbE ou 10 GbE para gerenciamento fora de banda (IPMI/BMC).
*   **Switches de Dados/Leaf:** Switches de 25 GbE ou 100 GbE (por exemplo, Celestica, Edgecore ou Dell) executando **SONiC** ou outros sistemas operacionais de rede abertos.

---

### 2. Infraestrutura Definida por Software (SDI) - O Fabric da Nuvem

Esta camada virtualiza e orquestra os recursos físicos, apresentando-os como uma nuvem unificada e programável. O OpenStack serve como a plataforma central de Infraestrutura como Serviço (IaaS), gerenciando e expondo esses recursos via APIs.

#### Plano de Gerenciamento
O plano de gerenciamento é responsável pela orquestração geral, implantação e gerenciamento do ciclo de vida da própria infraestrutura da nuvem.

*   **Nós Gerenciadores:** Esses nós executam serviços essenciais para as operações da nuvem, incluindo:
    *   **Ansible:** Para gerenciamento automatizado de configuração e implantação.
    *   **Docker Registry:** Para armazenar e distribuir imagens de contêineres para serviços internos.
    *   **Netbox:** Para Gerenciamento de Endereços IP (IPAM) e Gerenciamento de Infraestrutura de Data Center (DCIM).
    *   **Ferramentas de Observabilidade e Segurança:** Para monitoramento, registro e gerenciamento de eventos de segurança da plataforma de nuvem.

#### Plano de Controle
O plano de controle fornece as APIs e serviços centrais com os quais os usuários interagem para provisionar e gerenciar seus recursos de nuvem.

*   **Nós de Controle:** Esses nós hospedam serviços críticos do OpenStack:
    *   **APIs do OpenStack (Keystone, Nova, Neutron, Cinder, Glance, etc.):** Os pontos de entrada para todas as operações da nuvem.
    *   **Bancos de Dados (por exemplo, MariaDB, PostgreSQL):** Armazenam o estado e a configuração da nuvem.
    *   **Filas de Mensagens (por exemplo, RabbitMQ):** Facilitam a comunicação entre vários serviços do OpenStack.
    *   **Especificações:** Normalmente exigem CPU de 16+ Cores, 128 GB - 256 GB de RAM e RAID 1 NVMe para sistema/bancos de dados.

#### Plano de Computação
O plano de computação é onde as cargas de trabalho do usuário (máquinas virtuais) são executadas.

*   **Nós de Computação:** Esses nós executam o serviço OpenStack Nova, hospedando máquinas virtuais (VMs).
    *   **Especificações:** Apresentam CPUs com alta contagem de núcleos para densidade de VM, 256 GB - 1 TB+ de RAM dependendo da carga de trabalho e NICs Dual-Port 25/100 GbE.

#### Plano de Armazenamento
O plano de armazenamento fornece armazenamento persistente e altamente disponível para todos os recursos da nuvem.

*   **Nós de Armazenamento (Ceph OSDs):** Esses nós formam o backend de armazenamento distribuído, alimentado por Ceph. Eles fornecem armazenamento em bloco (OpenStack Cinder), armazenamento de objetos (compatível com S3) e sistemas de arquivos compartilhados (CephFS).
    *   **Especificações:** Normalmente CPU de 8-16 Cores, 64 GB - 128 GB de RAM (~1 GB de RAM por 1 TB de armazenamento OSD) e 4-12+ NVMe ou SAS/SATA SSDs para dados, com NVMe dedicado para WAL/DB.

#### Plano de Rede
O plano de rede fornece recursos de rede virtual, permitindo comunicação isolada e segura para recursos de locatários.

*   **Nós de Rede:** Esses nós gerenciam os componentes de rede definidos por software (SDN), incluindo:
    *   **OpenStack Neutron:** O serviço de rede principal para criar redes virtuais, sub-redes, roteadores e grupos de segurança.
    *   **OVN (Open Virtual Network):** Fornece a rede de sobreposição virtual, permitindo roteamento distribuído e aplicação de grupos de segurança no nível do hipervisor.

---

### 3. Camada de Plataforma como Serviço (PaaS)

Construída sobre a camada SDI, a camada PaaS oferece serviços de nível superior que abstraem o gerenciamento da infraestrutura, permitindo que os usuários se concentrem no desenvolvimento de aplicativos.

*   **Orquestração de Contêineres (KaaS):** Serviços Kubernetes gerenciados para implantar e escalar aplicativos conteinerizados.
*   **Database as a Service (DBaaS):** Ofertas de bancos de dados relacionais e NoSQL totalmente gerenciados.
*   Outros serviços especializados como plataformas de AI/ML, filas de mensagens, etc.

---

## 3. Configurações de Função Específicas

### Nós de Controle
*   **CPU:** 16+ Cores.
*   **RAM:** 128 GB - 256 GB.
*   **Disco:** RAID 1 NVMe para sistema/bancos de dados.

### Nós de Computação
*   **CPU:** Alta contagem de núcleos para densidade de VM.
*   **RAM:** 256 GB - 1 TB+ dependendo dos requisitos da carga de trabalho.
*   **NIC:** Dual-Port 25/100 GbE.

### Nós de Armazenamento (Ceph)
*   **CPU:** 8-16 Cores.
*   **RAM:** 64 GB - 128 GB (Regra geral: ~1 GB de RAM por 1 TB de armazenamento OSD).
*   **Disco:** 4-12+ NVMe ou SAS/SATA SSDs para dados; NVMe dedicado para WAL/DB.

---

## 4. Resumo da Pilha de Software

| Camada | Componente Recomendado |
| :--- | :--- |
| **Sistema Operacional** | Ubuntu 24.04 LTS |
| **IaaS** | OpenStack |
| **SDS (Armazenamento)** | Ceph |
| **SDN (Rede)** | SONiC & OVN |
| **Kubernetes** | K3s |
| **Gerenciamento de Identidade** | Keycloak |

> **Nota:** As marcas, modelos e configurações listadas são exemplos. Não existe uma única melhor especificação para cada caso de uso. No entanto, é importante considerar o hardware subjacente ao projetar uma infraestrutura de nuvem.