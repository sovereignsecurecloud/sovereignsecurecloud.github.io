---
sidebar_label: Gerenciamento de Chaves (KMS)
---

# Serviço de Gerenciamento de Chaves (KMS)

Proteger chaves criptográficas e segredos é um pilar crítico para manter a soberania dos dados. A SovereignSecure Cloud fornece um **Serviço de Gerenciamento de Chaves (KMS)** altamente seguro, com a tecnologia do OpenStack Barbican.

## Armazenamento Centralizado de Segredos

O KMS atua como um cofre seguro e orientado por API para provisionamento, gerenciamento e armazenamento de:
* Chaves de criptografia Simétricas e Assimétricas
* Certificados SSL/TLS (usados por Balanceadores de Carga)
* Senhas e tokens de API

## Criptografia Transparente de Dados

O KMS integra-se nativamente com nossos serviços de armazenamento subjacentes para fornecer criptografia transparente e em repouso (at-rest):

* **Armazenamento de Bloco Criptografado:** Você pode configurar seus volumes do Cinder para serem criptografados usando o formato LUKS. O KMS mantém a chave de criptografia do volume com segurança. O hypervisor recupera a chave diretamente do KMS na inicialização da instância para descriptografar o disco em tempo real (on the fly).
* **Armazenamento de Objetos Criptografado:** A Criptografia no Lado do Servidor (SSE) para buckets do Ceph Object Storage pode ser gerenciada usando chaves armazenadas no KMS, garantindo que seus dados não estruturados sejam criptografados antes de serem gravados nas unidades físicas.