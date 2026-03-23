---
sidebar_label: Prometheus & Grafana
sidebar_position: 2
---

# Logging, Monitoring & Telemetry

SovereignSecure Cloud relies on the industry-standard combination of **Prometheus** and **Grafana** for metrics collection and visualization.

## Prometheus (Telemetry & Alerting)

Prometheus is a time-series database and monitoring system.

* **Metrics Collection:** It continuously scrapes telemetry data from OpenStack services, Ceph storage nodes, SDN network switches, and Kubernetes clusters.
* **Alertmanager:** Evaluates incoming metrics against predefined thresholds and routes alerts (via email, Slack, or webhooks) to operations teams before issues impact cloud availability.

## Grafana (Visualization)

Grafana provides the visual interface for the metrics gathered by Prometheus.

* **Dashboards:** We provide curated dashboards that offer a single pane of glass into the health of the sovereign cloud infrastructure.
* **Tenant Showback:** Grafana is deeply integrated into the CMP to provide tenants with historical graphs of their specific compute and network utilization.