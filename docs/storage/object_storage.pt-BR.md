---
sidebar_label: Armazenamento de Objetos
---

# Armazenamento de Objetos

A SovereignSecure Cloud fornece **Armazenamento de Objetos** altamente escalável e durável, com a tecnologia do Ceph RADOS Gateway (RGW). Nosso Armazenamento de Objetos é totalmente compatível com a API S3 da Amazon, padrão da indústria, facilitando a integração com seus aplicativos e fluxos de trabalho existentes.

Ao contrário do Armazenamento em Bloco, que é anexado a Instâncias de Computação específicas, o Armazenamento de Objetos é acessível de qualquer lugar via HTTP/HTTPS, tornando-o a solução ideal para armazenar quantidades massivas de dados não estruturados.

## Principais Recursos

* **Escalabilidade Massiva:** Armazene quantidades virtualmente ilimitadas de dados. O cluster de armazenamento Ceph subjacente lida com o dimensionamento (scale out) automaticamente sem intervenção do usuário.
* **Compatibilidade S3:** Suporta nativamente ferramentas S3 padrão, SDKs (como Boto3) e APIs REST. Você pode migrar facilmente cargas de trabalho projetadas para nuvens públicas para nosso ambiente soberano sem reescrever seu código.
* **Alta Durabilidade:** Os dados são replicados automaticamente e codificados para eliminação (erasure-coded) em vários nós físicos e racks, fornecendo durabilidade de nível corporativo contra falhas de hardware.
* **Controle de Acesso Granular:** Proteja seus buckets e objetos usando Listas de Controle de Acesso (ACLs) padrão do S3 e políticas de IAM integradas.
* **Soberania de Dados:** Todos os objetos são armazenados exclusivamente em nossos data centers soberanos e locais (onshore), garantindo a conformidade com as leis locais de residência de dados.

## Casos de Uso Comuns

O Armazenamento de Objetos é altamente versátil e recomendado para:

* **Backups e Arquivos:** Armazenamento de dumps de banco de dados, snapshots de instâncias e arquivos de conformidade de longo prazo.
* **Mídia e Conteúdo:** Hospedagem de imagens, vídeos e arquivos de mídia grandes para aplicativos web.
* **Big Data e Aprendizado de Máquina:** Servindo como um data lake massivo para análises, logs e conjuntos de dados de treinamento de IA/ML.
* **Ativos Estáticos:** Distribuição de ativos estáticos (HTML, CSS, JavaScript) para desenvolvimento web front-end.

## Primeiros Passos

### Acessando o Armazenamento de Objetos

Você pode gerenciar seu Armazenamento de Objetos diretamente através da Plataforma de Gerenciamento de Nuvem (CMP) na seção **Armazenamento > Armazenamento de Objetos** (Storage > Object Storage), onde você pode criar buckets, fazer upload de arquivos e gerenciar permissões.

### Usando Clientes S3

Para conectar-se programaticamente ou via ferramentas de CLI (como a CLI `aws`, `s3cmd` ou Cyberduck), você precisará gerar **Credenciais S3** (Access Key e Secret Key) no seu perfil de usuário no CMP.

Uma vez geradas, configure seu cliente para apontar para a URL do endpoint do Armazenamento de Objetos da SovereignSecure Cloud.