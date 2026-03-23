---
sidebar_label: Implantando Clusters
---

# Implantando Clusters Kubernetes

A SovereignSecure Cloud oferece várias maneiras de provisionar e gerenciar seus clusters Kubernetes, quer você prefira uma abordagem visual baseada em UI ou um fluxo de trabalho de Infraestrutura como Código (IaC) totalmente automatizado.

## Métodos de Implantação

### 1. Plataforma de Gerenciamento de Nuvem (CMP)

A maneira mais fácil de começar é usando os catálogos de autoatendimento dentro do CMP.

* **KaaS (Kubernetes Gerenciado):** Navegue até o **Catálogo de Serviços** (Service Catalog) e selecione o blueprint **Kubernetes Cluster**. Você será solicitado a selecionar a versão do Kubernetes, o número de nós do plano de controle (control plane) para Alta Disponibilidade e o tamanho/contagem de seus nós de trabalho (worker nodes). O CMP orquestrará a implantação da Cluster API (CAPI) subjacente em seu nome.
* **K3s (Leve):** Selecione o blueprint **K3s Edge Cluster**. Isso provisionará rapidamente uma instância leve usando uma imagem de SO pré-configurada e inicializará um ambiente K3s de nó único ou multinó.

### 2. Infraestrutura como Código (Terraform / OpenTofu)

Para ambientes de produção e integração de CI/CD, é altamente recomendável definir seus clusters como código.

* **Usando Cluster API:** Você pode usar o provedor Kubernetes para aplicar definições YAML CAPI padrão diretamente em nosso cluster de gerenciamento, o que irá gerar (spawn) automaticamente seus clusters de carga de trabalho no OpenStack.
* **Usando o Provedor OpenStack:** Você pode usar o provedor padrão OpenStack do Terraform para provisionar instâncias de computação, redes e balanceadores de carga e, em seguida, usar scripts de usuário `cloud-init` para inicializar (bootstrap) suas próprias distribuições K3s ou Kubernetes padrão.

## Acessando Seu Cluster

Uma vez que seu cluster esteja provisionado, você precisa recuperar seu arquivo `kubeconfig` para interagir com ele usando a CLI `kubectl`.

### Via CMP
Se você provisionou o cluster por meio do Catálogo de Serviços do CMP, navegue até a página de detalhes do serviço implantado. Você encontrará um link de download seguro ou um bloco de texto contendo o seu `kubeconfig`.

### Via CLI / CAPI
Se você estiver gerenciando o cluster por meio da Cluster API, o `kubeconfig` será armazenado como um Secret padrão do Kubernetes no cluster de gerenciamento. Você pode extraí-lo usando:

```bash
kubectl --namespace default get secret <nome-do-cluster>-kubeconfig \
   -o jsonpath={.data.value} | base64 --decode > sovereign-kubeconfig
```