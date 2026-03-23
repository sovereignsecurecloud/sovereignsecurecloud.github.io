---
sidebar_label: Usuários e Projetos
---

# Usuários e Projetos

Na SovereignSecure Cloud, a multilocação (multi-tenancy) e o isolamento seguro de recursos são alcançados através do uso de **Projetos** (tradicionalmente chamados de Locatários/Tenants) e **Usuários**.

## O que é um Projeto?

Um **Projeto** é um contêiner lógico usado para agrupar e isolar recursos de nuvem. Todo recurso que você cria — seja uma Instância de Computação, uma Nuvem Privada Virtual (VPC), um volume de Armazenamento em Bloco ou um cluster Kubernetes — pertence a um projeto específico.

* **Isolamento de Recursos:** Os usuários não podem visualizar ou interagir com recursos fora dos projetos aos quais lhes foi explicitamente concedido acesso.
* **Cotas e Limites:** Os limites de recursos em nuvem (ex.: número máximo de vCPUs, RAM total ou armazenamento alocado) são definidos no nível do projeto para evitar o esgotamento de recursos.
* **Faturamento e Showback:** As métricas de uso e as cobranças financeiras (chargebacks) são rastreadas por projeto, facilitando a alocação de custos a diferentes departamentos, cargas de trabalho ou equipes dentro da sua organização.

## O que é um Usuário?

Um **Usuário** representa um operador humano ou uma conta de serviço automatizada (usuário de API) autenticada centralmente via **Keycloak**. 

Embora um usuário mantenha uma identidade única e federada em toda a plataforma SovereignSecure Cloud, sua autorização para realizar ações é estritamente determinada pelas **Funções** (Roles) que lhe são atribuídas dentro de **Projetos** específicos.

### Mapeamento de Usuário para Projeto

A relação entre usuários e projetos é de muitos para muitos:
* Um único usuário pode ser membro de vários projetos.
* Um único projeto pode ter vários usuários atribuídos a ele.
* Um usuário pode ter diferentes funções em diferentes projetos. Por exemplo, um usuário pode ser um `admin` no projeto de "Desenvolvimento", mas um `reader` (leitor) com permissão apenas de leitura no projeto de "Produção".

## Gerenciando o Acesso ao Projeto

Os administradores do locatário (tenant) podem gerenciar o acesso do usuário aos seus projetos diretamente pela Plataforma de Gerenciamento de Nuvem (CMP):

1. Navegue até **Identidade > Projetos** no CMP.
2. Selecione o seu projeto de destino.
3. Vá para a guia **Membros** para visualizar a lista atual de usuários autorizados.
4. Clique em **Adicionar Membro** (Add Member) para pesquisar um usuário organizacional existente.
5. Selecione o usuário e atribua-lhe uma Função apropriada (ex.: `member`, `reader` ou `admin`).

*(Para obter informações detalhadas sobre as permissões específicas associadas a cada atribuição, consulte a documentação de Funções e Políticas).*