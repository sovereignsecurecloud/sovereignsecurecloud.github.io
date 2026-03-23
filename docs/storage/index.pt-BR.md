---
sidebar_label: Visão Geral
sidebar_position: 1
---

# Visão Geral de Armazenamento

Bem-vindo à documentação de Armazenamento da SovereignSecure Cloud. Nossa infraestrutura de armazenamento foi projetada para fornecer soluções de armazenamento de dados altamente disponíveis, duráveis e escaláveis, adaptadas para atender a rigorosos requisitos de conformidade e soberania de dados.

Com a tecnologia de uma robusta arquitetura de Armazenamento Definido por Software (SDS), oferecemos várias interfaces de armazenamento para acomodar uma ampla variedade de cargas de trabalho, desde discos padrão de máquinas virtuais até arquivos massivos de dados não estruturados.

## Principais Serviços de Armazenamento

Explore as seções a seguir para saber mais sobre as capacidades de armazenamento disponíveis na SovereignSecure Cloud:

* **[Ceph SDS](ceph.md):** Aprenda sobre nosso back-end subjacente de Armazenamento Definido por Software com a tecnologia do Ceph, que fornece uma base altamente confiável e de autocura para todas as nossas ofertas de armazenamento.
* **[Armazenamento em Bloco](block_storage.md):** Volumes de bloco persistentes de alto desempenho (gerenciados via OpenStack Cinder) que podem ser anexados às suas Instâncias de Computação. Ideal para sistemas operacionais, bancos de dados e aplicativos que exigem acesso bruto em nível de bloco.
* **[Armazenamento de Objetos](object_storage.md):** Armazenamento altamente escalável e compatível com S3 para dados não estruturados, como backups, arquivos de mídia, conjuntos de dados de aprendizado de máquina e ativos estáticos da web, perfeitamente acessíveis por meio de APIs HTTP.
* **[Armazenamento de Arquivos Compartilhados](file_storage.md):** Fornece sistemas de arquivos padrão e compatíveis com POSIX que podem ser montados simultaneamente por várias Instâncias de Computação.

## Soberania de Dados

Todos os dados armazenados em nosso ambiente permanecem locais (onshore) e completamente isolados, garantindo que você mantenha controle absoluto sobre seus ativos digitais sem exposição a jurisdições estrangeiras ou dependência de fornecedores (vendor lock-in) proprietários.