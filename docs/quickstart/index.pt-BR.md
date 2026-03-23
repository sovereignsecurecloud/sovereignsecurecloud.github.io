---
sidebar_label: Guia de Início Rápido
sidebar_position: 1
---

# Guia de Início Rápido

Bem-vindo à SovereignSecure Cloud! Este Guia de Início Rápido foi criado para ajudar novos usuários a integrarem-se rapidamente e começarem a utilizar nossos serviços de nuvem seguros e soberanos. Seguindo estas etapas, você aprenderá como acessar o Console da Nuvem (com a tecnologia do ManageIQ), entender seu layout básico e implantar seu primeiro recurso na nuvem.

Nosso objetivo é simplificar sua experiência inicial, concentrando-nos em tarefas essenciais para que você comece a trabalhar rapidamente.

## Pré-requisitos

Antes de começar, certifique-se de ter:

*   **Conta SovereignSecure Cloud:** Sua organização deve ter fornecido credenciais de login.
*   **Acesso à Internet:** Uma conexão estável com a internet para acessar o Console da Nuvem.

## Passo 1: Acessando o Console da Nuvem

O Console da SovereignSecure Cloud é o seu hub central para gerenciar todos os seus recursos de nuvem.

1.  **Abra seu navegador da web** e acesse a URL do Console da Nuvem: `https://portal.sovereignsecurecloud.com`
2.  **Insira seu Nome de Usuário e Senha** fornecidos pelo seu administrador. Se a sua organização usa Logon Único (SSO), você pode ser redirecionado para a página de login corporativa.
3.  Clique em **Login** (Entrar).

Após o login bem-sucedido, você será direcionado para o seu painel (dashboard) personalizado.

## Passo 2: Entendendo o Painel (Dashboard)

O painel fornece uma visão geral dos seus recursos alocados, serviços ativos e quaisquer solicitações pendentes. As principais áreas que você notará incluem:

*   **Catálogo de Serviços:** Navegue e encomende serviços de nuvem predefinidos.
*   **Meus Serviços:** Visualize e gerencie os serviços que você já provisionou.
*   **Utilização de Recursos:** Monitore o uso de CPU, memória e armazenamento.
*   **Notificações e Alertas:** Mantenha-se informado sobre eventos do sistema e atualizações importantes.

## Passo 3: Iniciando Sua Primeira Máquina Virtual (VM)

Vamos implantar uma VM Linux básica usando o Catálogo de Serviços.

1.  No painel, clique em **Catálogo de Serviços** ou navegue até **Gerenciamento de Nuvem (CMP) > Catálogos de Serviços**.
2.  Navegue pelos serviços disponíveis e selecione uma **"VM Linux Básica"** ou oferta semelhante.
3.  **Preencha os detalhes necessários** no formulário de provisionamento:
    *   **Nome do Serviço:** Um nome único para sua VM (ex.: `minha-primeira-vm`).
    *   **Flavor (Tamanho):** Escolha um tamanho de instância pequeno (ex.: `t1.micro`).
    *   **Imagem:** Selecione uma imagem pública do Linux (ex.: `Ubuntu 22.04 LTS`).
    *   **Rede:** Selecione uma rede ou sub-rede padrão, se disponível.
    *   **Par de Chaves:** Escolha um par de chaves existente ou crie um novo para acesso SSH.
4.  Revise suas seleções e clique em **Order** (Solicitar) ou **Provision** (Provisionar).

Sua solicitação será enviada e o CMP começará a provisionar sua VM. Você pode acompanhar o status dela em **Meus Serviços**.

## Passo 4: Próximos Passos

Parabéns! Você iniciou com sucesso seu primeiro recurso na nuvem. Para continuar sua jornada:

*   **Conecte-se à sua Instância:** Aprenda como acessar com segurança sua VM recém-criada via SSH.
*   **Gerencie seus Recursos:** Explore todos os recursos da Plataforma de Gerenciamento de Nuvem.
*   **Explore os Serviços Principais:** Aprofunde-se nas opções de Computação, Armazenamento e Redes.
*   **Automatize com APIs:** Descubra como integrar e automatizar seus fluxos de trabalho usando nossas APIs.