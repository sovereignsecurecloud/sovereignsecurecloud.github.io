---
sidebar_label: Keycloak IAM
---

# Gerenciamento de Identidade e Acesso com Keycloak

A SovereignSecure Cloud utiliza o **Keycloak** como a solução central de Gerenciamento de Identidade e Acesso (IAM). O Keycloak fornece um ponto de entrada único e seguro para todos os serviços de nuvem, painéis (dashboards) e APIs.

## Recursos

* **Logon Único (SSO):** Faça login uma vez e obtenha acesso à Plataforma de Gerenciamento de Nuvem (CMP), OpenStack Horizon, painéis do Grafana e outros serviços integrados.
* **Broker de Identidade e Federação:** Podemos integrar perfeitamente os provedores de identidade existentes da sua organização (Active Directory, LDAP, SAML 2.0, OpenID Connect) com o ambiente de nuvem.
* **Autenticação Multifator (MFA):** Aplique políticas de autenticação rigorosas usando senhas de uso único (OTP) ou chaves de segurança de hardware para proteger recursos confidenciais na nuvem.
* **Controle de Acesso Baseado em Função (RBAC):** Mapeie seus grupos organizacionais para funções específicas do OpenStack (ex.: `member`, `reader`, `admin`), garantindo o princípio do menor privilégio.

## Acessando a Nuvem

Ao acessar o CMP ou a API da SovereignSecure, você será redirecionado para o portal de autenticação do Keycloak. Depois que sua identidade for verificada, um token seguro será gerado e passado para os serviços de nuvem subjacentes.

*(Consulte a seção de API e Automação para obter instruções sobre como usar as Credenciais de Aplicativo do Keycloak para acesso à CLI/API).*