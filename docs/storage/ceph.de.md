---
sidebar_label: Ceph SDS
---

# Software Defined Storage (SDS) mit Ceph

Die SovereignSecure Cloud nutzt **Ceph**, um ein einheitliches, hochgradig skalierbares Software-Defined Storage (SDS)-Backend bereitzustellen. Ceph verwandelt Standard-Hardware in einen enorm skalierbaren, äußerst zuverlässigen Speichercluster.

## Einheitliche Speicherarchitektur

Ceph bietet als einziges System Schnittstellen für mehrere Speichertypen aus einem einzigen verteilten Cluster:

* **Blockspeicher (RBD):** Ceph stellt das Backend für OpenStack Cinder bereit. Wenn Sie ein zusätzliches Volume erstellen und an eine Instanz anhängen, wird dieses von einem hochverfügbaren Ceph RADOS Block Device unterstützt.
* **Objektspeicher (RGW):** Ceph bietet über das RADOS Gateway eine S3-kompatible API, mit der Sie unstrukturierte Daten (wie Backups, Bilder und statische Assets) zuverlässig über HTTP speichern und abrufen können.
* **Dateispeicher (CephFS):** Bietet ein POSIX-kompatibles, gemeinsam genutztes Dateisystem, das von mehreren Instanzen gleichzeitig gemountet werden kann.

## Zuverlässigkeit & Souveränität

* **Datenreplikation:** Ceph repliziert Daten von Natur aus über mehrere physische Knoten und Racks (Verfügbarkeitszonen) hinweg. Fällt ein Laufwerk oder ein ganzer Server aus, heilt sich Ceph automatisch und verteilt die Daten ohne Ausfallzeiten neu.
* **Selbstheilung (Self-Healing):** Der CRUSH-Algorithmus ermöglicht es dem Speichercluster, Daten automatisch weiterzuleiten, das Rebalancing zu verwalten und sich von Fehlern zu erholen.
* **Datensouveränität:** Da Ceph vollständig in unseren Onshore-, Sovereign-Rechenzentren läuft, sind Ihre Daten geografisch garantiert und vollständig vor dem Zugriff ausländischer Gerichtsbarkeiten geschützt.

## Best Practices

* **Volume-Snapshots:** Nutzen Sie sofortige Ceph-Snapshots, um den Status Ihrer Instanzen zu sichern, bevor Sie größere Änderungen vornehmen.
* **Speicherebenen (Storage Tiers):** Achten Sie bei der Bereitstellung Ihrer Volumes auf verschiedene Speicherebenen (z. B. NVMe/SSD vs. HDD), um Leistungsanforderungen und Kosten in Einklang zu bringen.