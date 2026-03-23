---
sidebar_label: Imagens
sidebar_position: 4
---

# Imagens

Na SovereignSecure Cloud, uma **Imagem** é um modelo de máquina virtual que contém um sistema operacional pré-configurado e, potencialmente, outros softwares. As imagens são usadas como base para provisionar novas Instâncias de Computação.

Nosso serviço de imagens utiliza a tecnologia do OpenStack Glance e é totalmente integrado à Plataforma de Gerenciamento de Nuvem (CMP).

## Tipos de Imagem

Você pode escolher entre vários tipos de imagens ao implantar uma nova instância:

*   **Imagens Públicas:** Imagens de SO padrão, seguras e totalmente corrigidas, fornecidas e mantidas pelos administradores da SovereignSecure Cloud. Geralmente, incluem distribuições Linux populares (Ubuntu, CentOS, RHEL) e ambientes Windows Server.
*   **Imagens Privadas (Imagens Personalizadas):** Imagens que você mesmo cria. Elas são frequentemente criadas tirando um snapshot de uma instância existente e pré-configurada. As imagens privadas são visíveis apenas para usuários do seu Projeto.
*   **Imagens Compartilhadas:** Imagens que foram explicitamente compartilhadas entre diferentes Projetos ou Organizações.

## Formatos de Imagem Suportados

Se você estiver fazendo upload de sua própria imagem personalizada, a SovereignSecure Cloud oferece suporte a vários formatos padrão de disco de máquina virtual. O formato mais comum e altamente recomendado é o **QCOW2**, pois oferece suporte a dimensionamento dinâmico e snapshots.

Outros formatos suportados incluem:

*   `qcow2` (QEMU copy-on-write)
*   `raw` (Imagem de disco não estruturada)
*   `iso` (Imagem de disco óptico)

!!! tip "Cloud-Init e Cloudbase-Init"
    Ao trazer suas próprias imagens personalizadas, é altamente recomendável instalar o **cloud-init** (para Linux) ou o **Cloudbase-Init** (para Windows) antes de capturar a imagem. Isso garante que suas instâncias receberão corretamente chaves SSH, configurações de rede e Scripts de Usuário durante a inicialização.

## Criando uma Imagem Personalizada

Você pode criar uma imagem personalizada a partir do armazenamento de bloco raiz de uma instância em execução existente para capturar seu estado exato.

1.  Navegue até **Computação > Instâncias** no Console da Nuvem.
2.  Selecione a instância que você deseja capturar.
3.  É altamente recomendável **Parar** (Stop) a instância primeiro para garantir a integridade dos dados.
4.  Selecione **Criar Imagem** (Create Image) no menu Ações.
5.  Forneça um nome e uma descrição para a sua nova imagem.

Uma vez concluída, a nova imagem estará disponível em seu repositório em **Computação > Imagens** e poderá ser usada para iniciar instâncias clones idênticas.