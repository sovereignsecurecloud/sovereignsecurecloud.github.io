---
sidebar_label: Armazenamento de Arquivos Compartilhados
---

# Armazenamento de Arquivos Compartilhados

Além do armazenamento de Bloco e de Objetos, a SovereignSecure Cloud oferece **Armazenamento de Arquivos Compartilhados** gerenciado via OpenStack Manila e apoiado pelo CephFS.

O Armazenamento de Arquivos Compartilhados fornece sistemas de arquivos padrão e compatíveis com POSIX que podem ser montados simultaneamente por várias Instâncias de Computação. Isso é essencial para aplicativos corporativos que esperam um ambiente NAS (Network Attached Storage - Armazenamento Conectado à Rede) tradicional.

## Principais Recursos

* **Acesso Simultâneo:** Ao contrário do Armazenamento em Bloco (Cinder), que normalmente é anexado a uma única instância por vez, o Armazenamento de Arquivos Compartilhados permite que dezenas ou centenas de VMs leiam e gravem nos mesmos arquivos simultaneamente.
* **Escalabilidade:** Os compartilhamentos de arquivos podem crescer perfeitamente à medida que seus requisitos de dados se expandem, sem a necessidade de particionar ou formatar discos físicos subjacentes manualmente.
* **Protocolos Suportados:** Suportamos nativamente tanto **NFS** (Sistema de Arquivos de Rede) para cargas de trabalho Linux quanto **CIFS/SMB** para instâncias Windows.

## Casos de Uso Comuns

* **Clusters de Servidores Web:** Hospedagem de ativos de sites compartilhados (imagens, CSS, código) em uma frota de servidores web com balanceamento de carga.
* **Sistemas de Gerenciamento de Conteúdo (CMS):** Armazenamento de mídia carregada para aplicativos como WordPress ou Drupal.
* **Aplicativos Corporativos:** Software legado que requer operações simultâneas de leitura/gravação em uma unidade de rede compartilhada.

Os compartilhamentos de arquivos podem ser criados e gerenciados por meio da seção **Armazenamento > Compartilhamentos de Arquivos** (Storage > File Shares) na Plataforma de Gerenciamento de Nuvem (CMP).