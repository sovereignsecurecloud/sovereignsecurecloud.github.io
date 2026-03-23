---
sidebar_label: Client
sidebar_position: 10
---

# Client

Der OpenStackClient sucht an den folgenden Speicherorten nach einer `clouds.yaml`-Konfigurationsdatei:

- aktuelles Verzeichnis
- `~/.config/openstack`
- `/etc/openstack`

Mit dem OpenStack-Client können Sie das in der `clouds.yaml`-Konfigurationsdatei angegebene Cloud-Profil festlegen, indem Sie den Parameter `--os-cloud <Cloud-Identifikator>` angeben.

```
openstack --os-cloud openstack network list
```

## Migration von openrc zu clouds.yaml

Wenn Sie eine `openrc`-Datei haben (oft aus dem OpenStack Horizon-Dashboard heruntergeladen), aber das strukturiertere `clouds.yaml`-Format bevorzugen, können Sie diese einfach konvertieren.

## Mit einem Editor

Beispielinhalt einer aus dem Horizon-Dashboard heruntergeladenen `openrc`-Datei.

```sh title="PROJECT-openrc.sh"
#!/usr/bin/env bash
# Um eine OpenStack-Cloud zu verwenden, müssen Sie sich beim Identitätsdienst
# namens Keystone authentifizieren, der ein **Token** und einen **Servicekatalog** zurückgibt.
# Der Katalog enthält die Endpunkte für alle Dienste, auf die der Benutzer/Mandant
# Zugriff hat - wie Compute, Image Service, Identity, Object Storage, Block
# Storage und Networking (Codenamen Nova, Glance, Keystone, Swift,
# Cinder und Neutron).
#
# *HINWEIS*: Die Verwendung der *Identity API* Version 3 bedeutet nicht zwangsläufig, dass jede andere
# OpenStack-API Version 3 ist. Zum Beispiel implementiert Ihr Cloud-Anbieter möglicherweise
# Image API v1.1, Block Storage API v2 und Compute API v2.0. OS_AUTH_URL gilt
# nur für die über Keystone bereitgestellte Identity API.
export OS_AUTH_URL=https://identity.sovereignsecurecloud.com/v3
# Mit der Einführung von Keystone haben wir uns auf den Begriff **Projekt** (project)
# als die Entität geeinigt, die die Ressourcen besitzt.
export OS_PROJECT_ID=PROJECT_ID
export OS_PROJECT_NAME="PROJECT"
export OS_USER_DOMAIN_NAME="DOMAIN"
if [ -z "$OS_USER_DOMAIN_NAME" ]; then unset OS_USER_DOMAIN_NAME; fi
export OS_PROJECT_DOMAIN_ID="DOMAIN_ID"
if [ -z "$OS_PROJECT_DOMAIN_ID" ]; then unset OS_PROJECT_DOMAIN_ID; fi
# Entfernen von v2.0-Elementen, falls festgelegt
unset OS_TENANT_ID
unset OS_TENANT_NAME
# Zusätzlich zur besitzenden Entität (Mandant/Tenant) speichert OpenStack die Entität,
# die die Aktion ausführt, als den **Benutzer** (user).
export OS_USERNAME="USERNAME"
# Bei Keystone übergeben Sie das Keystone-Passwort.
echo "Bitte geben Sie Ihr OpenStack-Passwort für das Projekt $OS_PROJECT_NAME als Benutzer $OS_USERNAME ein: "
read -sr OS_PASSWORD_INPUT
export OS_PASSWORD=$OS_PASSWORD_INPUT
# Wenn Ihre Konfiguration mehrere Regionen umfasst, legen wir diese Information hier fest.
# OS_REGION_NAME ist optional und nur in bestimmten Umgebungen gültig.
export OS_REGION_NAME="RegionOne"
# Lassen Sie eine leere Variable nicht stehen, heben Sie sie auf (unset), wenn sie leer war
if [ -z "$OS_REGION_NAME" ]; then unset OS_REGION_NAME; fi
export OS_INTERFACE=public
export OS_IDENTITY_API_VERSION=3
```

Zuerst müssen Sie eine `clouds.yaml`-Datei erstellen. Achten Sie auf die Einrückung und verwenden Sie Leerzeichen anstelle von Tabulatoren.

```yaml title="clouds.yaml"
clouds:
  openstack:
    auth:
      auth_url: <OS_AUTH_URL hier einfügen>
      password: <OS_PASSWORD hier einfügen, falls nicht festgelegt, geben Sie Ihr Passwort hier ein>
      project_domain_name: <OS_PROJECT_DOMAIN_NAME hier einfügen>
      project_name: <OS_PROJECT_NAME hier einfügen>
      user_domain_name: <OS_USER_DOMAIN_NAME hier einfügen>
      username: <OS_USERNAME hier einfügen>
   region_name: <OS_REGION_NAME hier einfügen>
   identity_api_version: <OS_IDENTITY_API_VERSION hier einfügen>
   interface: <OS_INTERFACE hier einfügen>
```

Die endgültige `clouds.yaml` für Ihre `openrc` sieht dann so aus. Hier wurde der Inhalt aus dem vorherigen `PROJECT-openrc.sh`-Beispiel verwendet.

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

## Mit einem Skript

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

Zuerst müssen Sie Ihre `openrc`-Datei sourcen, damit die `OS_`-Variablen verfügbar sind.

```
source PROJECT-openrc.sh
```

Nun können Sie das Python-Skript ausführen und eine `clouds.yaml` wird geschrieben.

```
python3 clouds.py > clouds.yaml
```

### Bash

Sie müssen die Zeile `source` zuerst auf Ihre `openrc`-Datei richten. Führen Sie dann das Bash-Skript aus. Dies erstellt die Datei `clouds.yaml` in Ihrem aktuellen Verzeichnis.

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