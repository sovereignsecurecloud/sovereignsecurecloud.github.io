---
sidebar_label: Visão Geral de IAM
sidebar_position: 1
---

# Visão Geral de Identidade e Segurança

Bem-vindo à documentação de Identidade e Segurança da SovereignSecure Cloud. Em um ambiente soberano, controlar o acesso e manter uma postura de segurança rigorosa e auditável é a maior prioridade. 

Nossa plataforma adota uma arquitetura de confiança zero (zero-trust), garantindo que cada usuário, sistema e processo automatizado seja continuamente autenticado e autorizado antes de conceder acesso aos recursos da nuvem.

## Serviços Principais de Identidade e Segurança

Explore as seções a seguir para aprender a gerenciar o acesso e monitorar seu ambiente seguro:

* **[Keycloak IAM](keycloak.md):** Aprenda sobre nosso broker central de Gerenciamento de Identidade e Acesso, que fornece Logon Único (SSO) e federação de identidade.
* **[Usuários e Projetos](projects.md):** Entenda como os recursos de nuvem são agrupados logicamente em Projetos (locatários/tenants) e como gerenciar os usuários que operam dentro deles.
* **[Funções e Políticas](roles.md):** Descubra como o Controle de Acesso Baseado em Função (RBAC) aplica o princípio do menor privilégio em toda a sua infraestrutura.
* **[Teleport PAM](teleport.md):** Proteja e audite seu acesso administrativo privilegiado a Instâncias de Computação e clusters Kubernetes usando nosso gateway de acesso zero-trust.
* **[Wazuh SIEM](wazuh.md):** Monitore a postura de segurança da sua infraestrutura, detecte ameaças e garanta a conformidade usando nossa plataforma integrada de Gerenciamento de Eventos e Informações de Segurança (SIEM).

## Soberania e Conformidade

Ao acoplar estritamente os limites de identidade da sua organização às nossas ferramentas de gerenciamento de acesso, você retém total soberania sobre quem pode visualizar, modificar ou destruir seus dados. Logs de auditoria detalhados são gerados automaticamente e roteados para o SIEM para satisfazer rigorosas estruturas de conformidade locais.