---
sidebar_label: Ceph SDS
---

# Armazenamento Definido por Software (SDS) com Ceph

A SovereignSecure Cloud utiliza o **Ceph** para fornecer um back-end de Armazenamento Definido por Software (SDS) unificado e altamente escalável. O Ceph transforma hardware padrão em um cluster de armazenamento extremamente escalável e altamente confiável.

## Arquitetura de Armazenamento Unificada

O Ceph fornece exclusivamente interfaces para vários tipos de armazenamento a partir de um único cluster distribuído:

* **Armazenamento em Bloco (RBD):** O Ceph fornece o back-end para o OpenStack Cinder. Quando você cria e anexa um volume adicional a uma instância, ele é apoiado por um Ceph RADOS Block Device altamente disponível.
* **Armazenamento de Objetos (RGW):** O Ceph fornece uma API compatível com S3 através do RADOS Gateway, permitindo que você armazene e recupere dados não estruturados (como backups, imagens e ativos estáticos) de forma confiável via HTTP.
* **Armazenamento de Arquivos (CephFS):** Fornece um sistema de arquivos compartilhado compatível com POSIX que pode ser montado simultaneamente por várias instâncias.

## Confiabilidade e Soberania

* **Replicação de Dados:** O Ceph replica inerentemente dados em vários nós físicos e racks (Zonas de Disponibilidade). Se uma unidade ou um servidor inteiro falhar, o Ceph cicatriza e redistribui automaticamente os dados sem tempo de inatividade.
* **Autocura (Self-Healing):** O algoritmo CRUSH capacita o cluster de armazenamento a rotear dados automaticamente, gerenciar o rebalanceamento e se recuperar de falhas.
* **Soberania de Dados:** Como o Ceph roda inteiramente dentro de nossos data centers soberanos e locais (onshore), seus dados são geograficamente garantidos e completamente livres do acesso de jurisdições estrangeiras.

## Melhores Práticas

* **Snapshots de Volume:** Aproveite os snapshots instantâneos do Ceph para fazer backup do estado de suas instâncias antes de fazer grandes alterações.
* **Camadas de Armazenamento:** Esteja ciente das diferentes camadas de armazenamento (ex.: NVMe/SSD vs HDD) ao provisionar seus volumes para equilibrar os requisitos de desempenho e custo.