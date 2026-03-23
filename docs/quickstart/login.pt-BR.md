---
sidebar_label: Cliente
sidebar_position: 10
---

# Cliente

O [OpenStackClient](https://docs.openstack.org/python-openstackclient/latest/) procura por um arquivo de configuração `clouds.yaml` nos seguintes locais:

- diretório atual
- `~/.config/openstack`
- `/etc/openstack`

Com o cliente OpenStack, você pode especificar o perfil de nuvem configurado no arquivo `clouds.yaml` fornecendo o parâmetro `--os-cloud <identificador da nuvem>`.

```
openstack --os-cloud openstack network list
```

## Migração de openrc para clouds.yaml

Se você possui um arquivo `openrc` (frequentemente baixado do painel OpenStack Horizon), mas prefere usar o formato `clouds.yaml` mais estruturado, você pode convertê-lo facilmente.

## Com um editor

Conteúdo de exemplo de um arquivo `openrc` baixado do painel Horizon.

```sh title="PROJECT-openrc.sh"
#!/usr/bin/env bash
# Para usar uma nuvem OpenStack, você precisa se autenticar no serviço de Identidade
# chamado keystone, que retorna um **Token** e um **Catálogo de Serviços**.
# O catálogo contém os endpoints para todos os serviços aos quais o usuário/projeto
# tem acesso - como Computação, Serviço de Imagem, Identidade, Armazenamento de Objetos,
# Armazenamento em Bloco e Redes (com os codinomes nova, glance, keystone, swift,
# cinder e neutron).
#
# *NOTA*: Usar a *API de Identidade* versão 3 não significa necessariamente que qualquer
# outra API do OpenStack seja a versão 3. Por exemplo, seu provedor de nuvem pode implementar
# a API de Imagem v1.1, API de Armazenamento de Bloco v2 e API de Computação v2.0. OS_AUTH_URL é
# apenas para a API de Identidade servida pelo keystone.
export OS_AUTH_URL=https://identity.sovereignsecurecloud.com/v3
# Com a adição do Keystone, padronizamos o termo **projeto**
# como a entidade proprietária dos recursos.
export OS_PROJECT_ID=PROJECT_ID
export OS_PROJECT_NAME="PROJECT"
export OS_USER_DOMAIN_NAME="DOMAIN"
if [ -z "$OS_USER_DOMAIN_NAME" ]; then unset OS_USER_DOMAIN_NAME; fi
export OS_PROJECT_DOMAIN_ID="DOMAIN_ID"
if [ -z "$OS_PROJECT_DOMAIN_ID" ]; then unset OS_PROJECT_DOMAIN_ID; fi
# remover itens v2.0 caso estejam definidos
unset OS_TENANT_ID
unset OS_TENANT_NAME
# Além da entidade proprietária (locatário/tenant), o OpenStack armazena a entidade
# que executa a ação como o **usuário**.
export OS_USERNAME="USERNAME"
# Com o Keystone, você passa a senha do keystone.
echo "Por favor, insira sua Senha do OpenStack para o projeto $OS_PROJECT_NAME como usuário $OS_USERNAME: "
read -sr OS_PASSWORD_INPUT
export OS_PASSWORD=$OS_PASSWORD_INPUT
# Se a sua configuração tiver várias regiões, definimos essa informação aqui.
# OS_REGION_NAME é opcional e válido apenas em determinados ambientes.
export OS_REGION_NAME="RegionOne"
# Não deixe uma variável em branco, remova-a (unset) se estiver vazia
if [ -z "$OS_REGION_NAME" ]; then unset OS_REGION_NAME; fi
export OS_INTERFACE=public
export OS_IDENTITY_API_VERSION=3
```

Primeiro, você precisa criar um arquivo `clouds.yaml`. Tome cuidado com a indentação e use espaços em vez de tabulações.

```yaml title="clouds.yaml"
clouds:
  openstack:
    auth:
      auth_url: <OS_AUTH_URL aqui>
      password: <OS_PASSWORD aqui, se não estiver definido, insira sua senha aqui>
      project_domain_name: <OS_PROJECT_DOMAIN_NAME aqui>
      project_name: <OS_PROJECT_NAME aqui>
      user_domain_name: <OS_USER_DOMAIN_NAME aqui>
      username: <OS_USERNAME aqui>
   region_name: <OS_REGION_NAME aqui>
   identity_api_version: <OS_IDENTITY_API_VERSION aqui>
   interface: <OS_INTERFACE aqui>
```

O `clouds.yaml` final para o seu `openrc` ficará parecido com este. O conteúdo do exemplo anterior `PROJECT-openrc.sh` foi usado aqui.

```yaml title="clouds.yaml"
clouds:
  openstack:
    auth:
      auth_url: https://identity.sovereignsecurecloud.com/v3
      password: PASSWORD
      project_domain_name: DOMAIN
      project_name: PROJECT
      user_domain_name: DOMAIN
      username: USERNAME
   region_name: RegionOne
   identity_api_version: 3
   interface: public
```

## Com um script

### Python

```python title="clouds.py"
import os
import yaml

clouds = {
  "clouds":{
    "openstack": {
      "auth" : {
        "auth_url" : os.environ["OS_AUTH_URL"],
        "project_name": os.environ["OS_PROJECT_NAME"],
        "project_domain_name": os.environ["OS_PROJECT_DOMAIN_NAME"],
        "username": os.environ["OS_USERNAME"],
        "user_domain_name": os.environ["OS_USER_DOMAIN_NAME"],
        "password": os.environ["OS_PASSWORD"],
      },
      "region_name": os.environ["OS_REGION_NAME"],
      "identity_api_version":  os.environ["OS_IDENTITY_API_VERSION"],
      "interface": "public"
    }
  }
}

print(yaml.dump(clouds))
```

Primeiro você precisa carregar (source) o seu arquivo `openrc` para que as variáveis `OS_` fiquem disponíveis.

```
source PROJECT-openrc.sh
```

Agora você pode executar o script Python e um `clouds.yaml` será gravado.

```
python3 clouds.py > clouds.yaml
```

### Bash

Você precisa apontar a linha `source` para o seu arquivo `openrc` primeiro. Em seguida, execute o script Bash. Isso criará o arquivo `clouds.yaml` no seu diretório atual.

```
#!/bin/bash

source PROJECT-openrc.sh

PROJECT_ID=$(openstack project list | grep $OS_PROJECT_NAME | awk '{print $2}')

cat << EOF > clouds.yaml
clouds:
  openstack:
    auth:
      auth_url: $OS_AUTH_URL
      username: "$OS_USERNAME"
      password: "$OS_PASSWORD"
      project_name: "$OS_PROJECT_NAME"
      project_id: "$PROJECT_ID"
      user_domain_name: "$OS_USER_DOMAIN_NAME"
    region_name: "$OS_REGION_NAME"
    interface: "public"
    identity_api_version: $OS_IDENTITY_API_VERSION
EOF
```