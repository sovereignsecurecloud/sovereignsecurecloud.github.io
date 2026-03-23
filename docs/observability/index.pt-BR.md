---
sidebar_label: Visão Geral
sidebar_position: 1
---

# Observabilidade e Monitoramento

Bem-vindo à documentação de Observabilidade da SovereignSecure Cloud. Ter profunda visibilidade do desempenho da infraestrutura e dos aplicativos é fundamental para manter a alta disponibilidade e a segurança.

## A Pilha de Observabilidade

Nossa nuvem utiliza uma pilha de observabilidade moderna e de código aberto, projetada para capturar métricas, logs e rastreamentos em todo o ambiente:

* **Prometheus e Grafana:** O mecanismo central para coleta de métricas de séries temporais, alertas e painéis (dashboards) visuais.

## Visibilidade do Locatário (Tenant)

Por meio da Plataforma de Gerenciamento de Nuvem (CMP), os locatários podem visualizar a utilização de recursos (CPU, memória, rede) de seus projetos específicos. Usuários avançados também podem expor métricas de aplicativos personalizados aos endpoints do Prometheus da nuvem ou implantar pilhas de monitoramento isoladas em seus próprios clusters Kubernetes.