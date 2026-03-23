---
sidebar_label: Prometheus e Grafana
sidebar_position: 2
---

# Registro, Monitoramento e Telemetria

A SovereignSecure Cloud depende da combinação padrão da indústria de **Prometheus** e **Grafana** para coleta e visualização de métricas.

## Prometheus (Telemetria e Alertas)

O Prometheus é um banco de dados de séries temporais e sistema de monitoramento.

* **Coleta de Métricas:** Ele coleta (scrapes) continuamente dados de telemetria dos serviços do OpenStack, nós de armazenamento Ceph, switches de rede SDN e clusters Kubernetes.
* **Alertmanager:** Avalia as métricas recebidas em relação a limites predefinidos e roteia alertas (via e-mail, Slack ou webhooks) para as equipes de operações antes que os problemas afetem a disponibilidade da nuvem.

## Grafana (Visualização)

O Grafana fornece a interface visual para as métricas coletadas pelo Prometheus.

* **Painéis (Dashboards):** Fornecemos painéis selecionados que oferecem uma visão unificada (single pane of glass) da integridade da infraestrutura de nuvem soberana.
* **Showback do Locatário (Tenant):** O Grafana é profundamente integrado ao CMP para fornecer aos locatários gráficos históricos de sua utilização específica de computação e rede.