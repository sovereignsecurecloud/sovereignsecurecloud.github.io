---
sidebar_label: Teleport PAM
---

# Gerenciamento de Acesso Privilegiado (PAM) com Teleport

Em uma nuvem soberana, proteger e auditar o acesso administrativo à infraestrutura é fundamental. A SovereignSecure Cloud utiliza o **Teleport** para um Gerenciamento de Acesso Privilegiado (PAM) abrangente.

## Acesso Zero-Trust (Confiança Zero)

O Teleport substitui as chaves SSH estáticas herdadas e VPNs por acesso de confiança zero baseado em identidade.

* **Autenticação Baseada em Certificado:** Em vez de gerenciar chaves `id_rsa` estáticas, o Teleport emite certificados de curta duração e vinculados à identidade, atrelados ao seu login de SSO do Keycloak.
* **Acesso Unificado:** Acesse de forma segura servidores SSH, clusters Kubernetes, bancos de dados e aplicativos web internos através de um único gateway.

## Auditoria e Conformidade

Para atender a rigorosos padrões de conformidade soberana e regulatória, o Teleport fornece:

* **Gravação de Sessão:** Cada sessão interativa de SSH e `exec` do Kubernetes é gravada e pode ser reproduzida para auditorias de segurança.
* **Logs de Auditoria Detalhados:** Um log abrangente de todos os eventos de acesso, comandos executados e transferências de arquivos, exportável diretamente para o nosso SIEM (Wazuh).
* **Acesso Just-In-Time:** Os administradores podem solicitar permissões temporárias e elevadas para elementos de infraestrutura específicos apenas quando necessário para cenários de emergência (break-glass).