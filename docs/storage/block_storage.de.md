---
sidebar_label: Blockspeicher
---

# Blockspeicher (Block Storage)

Die SovereignSecure Cloud bietet hochverfügbare und persistente **Blockspeicher**-Volumes, die über den OpenStack Cinder-Dienst verwaltet und von unserer robusten Ceph SDS-Infrastruktur unterstützt werden.

Blockspeicher fungiert wie eine physische Festplatte, die Sie an Ihre Compute-Instanzen anhängen können. Er bietet rohen Speicher auf Blockebene, der mit einem Dateisystem (wie EXT4, XFS oder NTFS) formatiert werden kann, und ist ideal für Anwendungen, die einen latenzarmen und leistungsstarken Datenzugriff erfordern.

## Hauptmerkmale

* **Persistenz:** Im Gegensatz zu flüchtigem Instanzspeicher (Ephemeral Storage) bleiben Blockspeicher-Volumes unabhängig vom Lebenszyklus der Instanz bestehen. Wenn Sie eine Instanz löschen, können Sie wählen, ob Sie das angehängte Block-Volume und dessen Daten behalten möchten.
* **Hochverfügbarkeit:** Da Volumes von Ceph unterstützt werden, werden Ihre Daten von Natur aus über mehrere physische Festplatten und Knoten repliziert. Hardwareausfälle werden transparent und ohne Datenverlust behandelt.
* **Bootfähige Volumes:** Sie können ein auf einem Image basierendes Volume erstellen und es als Root-Laufwerk verwenden, um eine neue Instanz zu booten.
* **Skalierbarkeit:** Sie können die Größe eines vorhandenen Blockspeicher-Volumes problemlos erhöhen (Volume Resizing), wenn Ihr Speicherbedarf wächst, ohne Daten migrieren zu müssen.
* **Portabilität:** Volumes können von einer Instanz getrennt und an eine andere angehängt werden, was eine einfache Datenportabilität und Notfallwiederherstellung (Disaster Recovery) ermöglicht.

## Volume-Snapshots

Ein Volume-Snapshot ist eine schreibgeschützte Point-in-Time-Kopie Ihres Blockspeicher-Volumes. 

* **Backups:** Snapshots sind unerlässlich, um zuverlässige Backups Ihrer Datenbanken oder kritischen Dateisysteme zu erstellen, bevor Sie System-Upgrades oder riskante Operationen durchführen.
* **Klonen:** Sie können neue, identische Blockspeicher-Volumes direkt aus einem Snapshot erstellen. Dies erleichtert die Replikation von Umgebungen für Tests oder Skalierungen.

## Häufige Anwendungsfälle

Blockspeicher ist der empfohlene Speichertyp für:

* Relationale und NoSQL-Datenbanken (MySQL, PostgreSQL, MongoDB usw.)
* Betriebssystem-Boot-Laufwerke
* Unternehmensanwendungen, die POSIX-kompatible Dateisysteme erfordern
* High-I/O-Workloads, die dedizierte Leistung erfordern

## Volumes verwalten

Sie können Blockspeicher-Volumes direkt über die Cloud Management Platform (CMP) im Abschnitt **Speicher > Volumes** (Storage > Volumes) oder programmgesteuert über die OpenStack-CLI und Terraform erstellen, anhängen, trennen und löschen.