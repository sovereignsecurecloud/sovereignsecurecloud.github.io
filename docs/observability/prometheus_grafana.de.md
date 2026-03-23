---
sidebar_label: Prometheus & Grafana
sidebar_position: 2
---

# Protokollierung, Überwachung & Telemetrie

Die SovereignSecure Cloud verlässt sich auf die branchenübliche Kombination aus **Prometheus** und **Grafana** für die Erfassung und Visualisierung von Metriken.

## Prometheus (Telemetrie & Alarmierung)

Prometheus ist eine Zeitreihendatenbank und ein Überwachungssystem.

* **Metrikerfassung:** Es sammelt (scrapt) kontinuierlich Telemetriedaten von OpenStack-Diensten, Ceph-Speicherknoten, SDN-Netzwerk-Switches und Kubernetes-Clustern.
* **Alertmanager:** Wertet eingehende Metriken anhand vordefinierter Schwellenwerte aus und leitet Warnmeldungen (per E-Mail, Slack oder Webhooks) an die Betriebsteams weiter, bevor sich Probleme auf die Cloud-Verfügbarkeit auswirken.

## Grafana (Visualisierung)

Grafana bietet die visuelle Benutzeroberfläche für die von Prometheus gesammelten Metriken.

* **Dashboards:** Wir stellen kuratierte Dashboards zur Verfügung, die einen zentralen Überblick (Single Pane of Glass) über den Zustand der souveränen Cloud-Infrastruktur bieten.
* **Tenant Showback:** Grafana ist tief in die CMP integriert, um Mandanten (Tenants) historische Diagramme ihrer spezifischen Rechen- und Netzwerkauslastung bereitzustellen.