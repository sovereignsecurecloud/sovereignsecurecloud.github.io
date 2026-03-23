---
sidebar_label: Catálogos de Serviços
sidebar_position: 2
---

# Catálogos de Serviços

O Catálogo de Serviços é um recurso essencial da Plataforma de Gerenciamento de Nuvem (CMP) SovereignSecure, com a tecnologia do ManageIQ. Ele fornece um portal de autoatendimento onde os usuários podem navegar, solicitar e gerenciar serviços de nuvem predefinidos e aprovados. Isso simplifica o processo de provisionamento, garante a conformidade e reduz a necessidade de intervenção direta de TI.

## O que são Catálogos de Serviços?

Os Catálogos de Serviços apresentam uma lista selecionada de serviços de TI que sua organização disponibilizou. Esses serviços podem variar desde simples máquinas virtuais até aplicativos complexos em várias camadas ou clusters Kubernetes, todos empacotados com configurações e políticas pré-aprovadas.

**Os principais benefícios incluem:**

*   **Autoatendimento:** Usuários podem provisionar recursos sob demanda sem esperar por aprovações ou configurações manuais.
*   **Padronização:** Garante que todos os recursos implantados sigam os padrões organizacionais, as políticas de segurança e as melhores práticas.
*   **Governança e Conformidade:** Integra-se ao gerenciamento de cotas e fluxos de trabalho de aprovação para manter o controle sobre o consumo de recursos e os gastos.
*   **Redução da Sobrecarga Operacional:** Automatiza tarefas repetitivas de provisionamento, liberando a equipe de TI para iniciativas mais estratégicas.

## Navegando no Catálogo de Serviços

1.  **Faça o login** no Console da Nuvem SovereignSecure.
2.  No painel (dashboard) principal, clique no bloco **"Catálogo de Serviços"** ou navegue pelo menu em **Gerenciamento de Nuvem (CMP) > Catálogos de Serviços**.
3.  Você verá uma lista de itens de serviço disponíveis, frequentemente agrupados por categoria (ex.: "Computação", "Bancos de Dados", "Contêineres", "Aplicativos").
4.  Clique em um item de serviço para ver seus detalhes, incluindo uma descrição, custo estimado (se aplicável) e opções de configuração.

## Solicitando um Serviço

Depois de encontrar o serviço de que você precisa, o processo de solicitação é simples:

1.  **Selecione o item de serviço desejado** no catálogo.
2.  Um **formulário de provisionamento** aparecerá, preenchido com valores padrão sempre que possível.
3.  **Preencha os campos obrigatórios:**
    *   **Nome do Serviço:** Um nome descritivo e único para sua nova instância de serviço.
    *   **Projeto/Departamento:** Selecione o projeto ou departamento ao qual este serviço será faturado.
    *   **Opções de Configuração:** Dependendo do serviço, você pode escolher o tamanho da VM (flavor), a imagem do sistema operacional, a capacidade de armazenamento, as configurações de rede ou os parâmetros específicos do aplicativo.
    *   **Notas de Aprovação (Opcional):** Forneça qualquer informação adicional para a equipe de aprovação, caso haja um fluxo de trabalho de aprovação em vigor.
4.  **Revise** suas seleções e o custo estimado.
5.  Clique em **"Solicitar"** ou **"Enviar Solicitação"**.

## Acompanhando a Solicitação do seu Serviço

Após enviar uma solicitação, você pode acompanhar seu status:

1.  Navegue até **Gerenciamento de Nuvem (CMP) > Meus Serviços**.
2.  Aqui, você verá uma lista de todos os serviços que solicitou, juntamente com seu status atual (ex.: "Aprovação Pendente", "Provisionando", "Ativo", "Falhou").
3.  Você pode clicar em um serviço para visualizar seu status detalhado, logs e realizar ações como "Parar", "Iniciar" ou "Desativar" (se permitido).