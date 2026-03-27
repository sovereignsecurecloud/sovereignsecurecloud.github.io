---
sidebar_label: Visão Geral
sidebar_position: 1
---

# Plataforma de Gerenciamento de Nuvem (CMP)

Bem-vindo à documentação da Plataforma de Gerenciamento de Nuvem (CMP) da SovereignSecure. Com a tecnologia do ManageIQ, nosso CMP fornece um portal unificado de autoatendimento para gerenciar seu ambiente de nuvem soberana e multilocatária. Ele capacita os usuários a orquestrar cargas de trabalho, rastrear a utilização e governar os recursos do projeto com facilidade, tudo isso ao mesmo tempo em que adere a rigorosos princípios de soberania de dados.

## Benefícios do CMP SovereignSecure

Aproveitar nosso CMP oferece várias vantagens importantes para a sua organização:

*   **Governança Aprimorada:** Controle centralizado sobre o provisionamento de recursos, garantindo a conformidade com as políticas organizacionais e os requisitos regulatórios.
*   **Transparência de Custos:** Relatórios detalhados de chargeback (cobrança) e showback (demonstração de custos) para rastrear e atribuir os gastos com nuvem com precisão.
*   **Provisionamento de Autoatendimento:** Capacite os usuários a implantar rapidamente serviços aprovados de um catálogo selecionado, reduzindo a sobrecarga operacional.
*   **Eficiência Operacional:** Automatize tarefas rotineiras e o gerenciamento do ciclo de vida de máquinas virtuais, contêineres e outros recursos em nuvem.
*   **Prontidão Multinuvem:** Embora atualmente focado no OpenStack, o ManageIQ fornece uma base para recursos futuros de gerenciamento de várias nuvens (multi-cloud).

## Principais Capacidades

* **[Catálogos de Serviços](catalog.md):** Um portal de autoatendimento onde os usuários podem solicitar serviços de TI pré-definidos e aprovados, como Máquinas Virtuais padrão, pilhas de aplicativos em várias camadas e clusters Kubernetes.
* **[Cobrança e Relatórios](reporting.md):** Acompanhe o custo financeiro da execução de suas cargas de trabalho. Gere relatórios detalhados de showback/chargeback com base na utilização de CPU, memória, armazenamento e rede.
*   **Gerenciamento do Ciclo de Vida:** Automatize o provisionamento, a desativação e o dimensionamento de instâncias e outros recursos em nuvem, simplificando as operações e garantindo a otimização de recursos.
*   **Aplicação de Cotas e Políticas:** Defina e aplique cotas de recursos e políticas operacionais entre projetos e usuários, mantendo o controle e evitando a dispersão de recursos.

## Acessando o Console da Nuvem

1.  **Abra o seu navegador da web** e acesse a URL do Console da Nuvem SovereignSecure: `https://portal.sovereignsecurecloud.com`
2. Faça o login usando as credenciais de logon único (SSO) da sua organização ou sua conta de administrador específica do projeto.
3. A partir do painel (dashboard), você pode visualizar um resumo de suas cargas de trabalho em execução, solicitações de catálogo pendentes e alertas recentes.

## Nuvem Adicional Suportada

1. Alibaba Cloud
2. Huawei Cloud
3. Amazon Web Services (AWS)
4. Microsoft Azure
5. Google Cloud Platform (GCP)
6. Oracle Cloud
7. Tencent Cloud
8. OpenStack Cloud
9. VMware vSphere
10. Nutanix

!!! tip "Para Usuários Avançados e Automação"
    Além do Console da Nuvem gráfico, você também pode interagir com o CMP e a infraestrutura subjacente do OpenStack de forma programática. Consulte a seção de API e Automação para obter detalhes sobre o uso da API REST do ManageIQ e das CLIs nativas do OpenStack.