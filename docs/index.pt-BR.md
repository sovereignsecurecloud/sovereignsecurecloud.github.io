# Bem-vindo à Documentação da SovereignSecure Cloud &trade;

Bem-vindo à SovereignSecure Cloud, sua plataforma de confiança para serviços em nuvem seguros, em conformidade e de alto desempenho. Construída sobre uma base de OpenStack e aprimorada com o ManageIQ para um gerenciamento abrangente da nuvem, capacitamos as organizações a manter controle total sobre seus dados e operações dentro de um ambiente digital soberano.

## Nosso Compromisso com a Soberania

A SovereignSecure Cloud foi projetada para atender aos rigorosos requisitos de soberania de dados, garantindo que seus dados permaneçam dentro de jurisdições geográficas e legais especificadas. Alcançamos isso através de:

*   **Residência de Dados:** Seus dados são armazenados e processados exclusivamente em regiões designadas, aderindo aos regulamentos locais.
*   **Autonomia Operacional:** Nossa infraestrutura e operações são gerenciadas por equipes locais, garantindo transparência e controle.
*   **Base de Código Aberto:** O uso do OpenStack e outras tecnologias de código aberto minimiza a dependência de fornecedores e fornece uma pilha transparente e auditável.
*   **Segurança e Conformidade Robustas:** Implementamos medidas de segurança avançadas e mantemos certificações para proteger suas cargas de trabalho confidenciais.

## Explore a Documentação

Use a navegação à esquerda para explorar nossos guias abrangentes:

```mermaid
graph TD
    subgraph SovereignCloud[<b>SovereignSecure Cloud &trade;</b>]
        direction TB
        
        subgraph DataControl[<b>Controle de Dados e Soberania</b>]
            DC[Leis de Residência de Dados]
            DP[Proteção de Dados]
            DG[Governança de Dados]
        end
        
        subgraph Security[<b>Segurança e Conformidade</b>]
            IS[Segurança da Infraestrutura]
            EN[Criptografia]
            CS[Certificações e Padrões]
        end
        
        subgraph Deployment[<b>Modelos de Implantação</b>]
            PB[Nuvem Soberana Pública]
            PR[Nuvem Soberana Privada]
            HY[Nuvem Soberana Híbrida]
        end
        
        subgraph Providers[<b>Componentes Principais</b>]
            OS[Operações Locais]
            LC[Provedores de Nuvem]
            OP[Tecnologias de Código Aberto]
        end
        
        DataControl -->|Garante| Security
        Security -->|Suporta| Deployment
        Deployment -->|Aproveita| Providers
        Providers -->|Mantém| DataControl
    end
    
    Government[Regulamentos Governamentais] -.-> DataControl
    Enterprise[Requisitos Corporativos] -.-> Security
    Users[Privacidade do Usuário Final] -.-> Deployment
```

## Seções Principais

<div class="grid cards" markdown>

-   :material-rocket-launch:{ .lg .middle } __Primeiros Passos__

    ---

    Um guia passo a passo para novos usuários se integrarem rapidamente e implantarem seus primeiros recursos.

    [:octicons-arrow-right-24: Início Rápido](quickstart/index.md)

-   :material-monitor-dashboard:{ .lg .middle } __Gerenciamento de Nuvem (CMP)__

    ---

    Aprenda a usar o portal ManageIQ para provisionamento de autoatendimento, catálogos e relatórios.

    [:octicons-arrow-right-24: Visão Geral do CMP](cmp/index.md)

-   :material-server-network:{ .lg .middle } __Serviços Principais__

    ---

    Aprofunde-se em nossas ofertas de Computação, Armazenamento e Redes, incluindo instâncias de GPU.

    [:octicons-arrow-right-24: Explorar Serviços](compute/index.md)

-   :material-api:{ .lg .middle } __API e Automação__

    ---

    Integre-se à nossa plataforma usando APIs nativas do OpenStack e ferramentas de IaC como Terraform.

    [:octicons-arrow-right-24: Visão Geral da API](api/index.md)

</div>