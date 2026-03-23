---
sidebar_label: Armazenamento em Bloco
---

# Armazenamento em Bloco

A SovereignSecure Cloud fornece volumes de **Armazenamento em Bloco** altamente disponíveis e persistentes, gerenciados através do serviço OpenStack Cinder e apoiados pela nossa robusta infraestrutura Ceph SDS.

O armazenamento em bloco atua como um disco rígido físico que você pode anexar às suas Instâncias de Computação. Ele fornece armazenamento bruto em nível de bloco que pode ser formatado com um sistema de arquivos (como EXT4, XFS ou NTFS) e é ideal para aplicativos que exigem acesso a dados de baixa latência e alto desempenho.

## Principais Recursos

* **Persistência:** Ao contrário do armazenamento de instância efêmero, os volumes de armazenamento em bloco persistem independentemente do ciclo de vida da instância. Se você excluir uma instância, poderá optar por reter o volume de bloco anexado e seus dados.
* **Alta Disponibilidade:** Como os volumes são apoiados pelo Ceph, seus dados são inerentemente replicados em vários discos físicos e nós. As falhas de hardware são tratadas de forma transparente sem perda de dados.
* **Volumes Inicializáveis:** Você pode criar um volume com base em uma imagem e usá-lo como o disco raiz para inicializar uma nova instância.
* **Escalabilidade:** Você pode aumentar facilmente o tamanho de um volume de armazenamento em bloco existente (Redimensionamento de Volume) à medida que suas necessidades de armazenamento crescem, sem precisar migrar os dados.
* **Portabilidade:** Os volumes podem ser desanexados de uma instância e reanexados a outra, permitindo fácil portabilidade de dados e recuperação de desastres.

## Snapshots de Volume

Um snapshot de volume é uma cópia somente leitura e pontual (point-in-time) do seu volume de armazenamento em bloco. 

* **Backups:** Os snapshots são essenciais para criar backups confiáveis de seus bancos de dados ou sistemas de arquivos críticos antes de realizar atualizações de sistema ou operações arriscadas.
* **Clonagem:** Você pode criar novos volumes de armazenamento em bloco idênticos diretamente de um snapshot, facilitando a replicação de ambientes para teste ou escalonamento.

## Casos de Uso Comuns

O armazenamento em bloco é o tipo de armazenamento recomendado para:

* Bancos de dados relacionais e NoSQL (MySQL, PostgreSQL, MongoDB, etc.)
* Discos de inicialização do sistema operacional
* Aplicativos corporativos que exigem sistemas de arquivos compatíveis com POSIX
* Cargas de trabalho de alta E/S que exigem desempenho dedicado

## Gerenciando Volumes

Você pode criar, anexar, desanexar e excluir volumes de Armazenamento em Bloco diretamente da Plataforma de Gerenciamento de Nuvem (CMP) na seção **Armazenamento > Volumes** (Storage > Volumes), ou programaticamente por meio da CLI do OpenStack e do Terraform.