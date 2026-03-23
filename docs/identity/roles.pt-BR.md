---
sidebar_label: Funções e Políticas
---

# Funções e Políticas

A SovereignSecure Cloud impõe um controle de acesso rigoroso por meio do **Controle de Acesso Baseado em Função (RBAC)**. Ao atribuir funções (roles) aos usuários dentro de projetos específicos, você pode ditar de forma granular quais ações eles têm permissão para executar, garantindo a adesão ao princípio do menor privilégio.

## Funções Padrão

Para simplificar o gerenciamento de acesso, a SovereignSecure Cloud fornece um conjunto de funções padrão predefinidas. Ao adicionar um usuário a um Projeto, você deve atribuir a ele uma ou mais destas funções:

* **Admin:** Concede acesso administrativo total dentro do escopo do projeto. Os administradores podem provisionar, modificar e excluir qualquer recurso (Computação, Armazenamento, Redes, etc.), bem como gerenciar as associações e cotas do projeto.
* **Member (Membro):** A função de operador padrão. Os membros podem criar, gerenciar e excluir recursos dentro do projeto para conduzir suas operações diárias, mas não podem modificar configurações no nível do projeto ou gerenciar o acesso de outros usuários.
* **Reader (Leitor):** Concede acesso apenas para visualização. Os leitores podem listar e visualizar os detalhes de instâncias, redes e volumes de armazenamento, mas não podem criar, modificar ou excluir nenhum recurso. Esta função é altamente recomendada para auditores de segurança, oficiais de conformidade ou contas de serviço de monitoramento automatizado.

## Políticas

Nos bastidores, as funções são mapeadas para ações específicas usando **Políticas**. 

Uma política é um conjunto de regras avaliadas pelos serviços de nuvem subjacentes (ex.: Nova para Computação, Neutron para Redes) toda vez que uma solicitação de API é feita. Por exemplo, uma regra de política pode ditar que a ação de API `compute:create_instance` só é permitida se o usuário solicitante possuir a função `admin` ou `member` no projeto de destino.

Como a SovereignSecure Cloud prioriza uma postura de segurança por padrão, as políticas de infraestrutura padrão são estritamente bloqueadas para evitar acesso lateral não autorizado ou exposição de recursos.

## Atribuindo Funções

As atribuições de função são estritamente definidas no nível do Projeto. A função de um usuário em um projeto não lhe concede nenhum privilégio em outro projeto, a menos que seja explicitamente atribuída.

Para atribuir ou alterar a função de um usuário:

1. Faça o login na Plataforma de Gerenciamento de Nuvem (CMP).
2. Navegue até **Identidade > Projetos**.
3. Selecione o projeto relevante e vá para a guia **Membros**.
4. Clique em **Adicionar Membro** (Add Member) para conceder acesso a um novo usuário organizacional, ou clique no ícone **Editar** (Edit) ao lado de um usuário existente para modificar sua atribuição de função atual.

!!! tip "Auditoria"
    Todas as atribuições e alterações de função são registradas e exportáveis para a plataforma SIEM (Wazuh) para satisfazer os requisitos de conformidade e auditoria soberana.