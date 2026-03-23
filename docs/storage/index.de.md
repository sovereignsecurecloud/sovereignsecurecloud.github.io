---
sidebar_label: Übersicht
sidebar_position: 1
---

# Speicher Übersicht

Willkommen bei der Speicher-Dokumentation der SovereignSecure Cloud. Unsere Speicherinfrastruktur ist darauf ausgelegt, hochverfügbare, langlebige und skalierbare Datenspeicherlösungen bereitzustellen, die auf strenge Anforderungen an die Datensouveränität und Compliance zugeschnitten sind.

Angetrieben von einer robusten Software-Defined Storage (SDS)-Architektur bieten wir mehrere Speicherschnittstellen, um einer Vielzahl von Workloads gerecht zu werden, von standardmäßigen Festplatten für virtuelle Maschinen bis hin zu massiven unstrukturierten Datenarchiven.

## Zentrale Speicherdienste

Erkunden Sie die folgenden Abschnitte, um mehr über die in der SovereignSecure Cloud verfügbaren Speicherfunktionen zu erfahren:

* **[Ceph SDS](ceph.md):** Erfahren Sie mehr über unser zugrunde liegendes Software-Defined Storage-Backend, das von Ceph angetrieben wird und eine äußerst zuverlässige, selbstheilende Grundlage für alle unsere Speicherangebote bietet.
* **[Blockspeicher](block_storage.md):** Hochleistungsfähige persistente Block-Volumes (verwaltet über OpenStack Cinder), die an Ihre Compute-Instanzen angehängt werden können. Ideal für Betriebssysteme, Datenbanken und Anwendungen, die einen direkten Zugriff auf Blockebene erfordern.
* **[Objektspeicher](object_storage.md):** Hochgradig skalierbarer, S3-kompatibler Speicher für unstrukturierte Daten wie Backups, Mediendateien, Datensätze für maschinelles Lernen und statische Web-Assets, die nahtlos über HTTP-APIs zugänglich sind.
* **[Freigegebener Dateispeicher](file_storage.md):** Bietet standardmäßige, POSIX-kompatible Dateisysteme, die von mehreren Compute-Instanzen gleichzeitig gemountet werden können.

## Datensouveränität

Alle in unserer Umgebung gespeicherten Daten verbleiben im Inland (onshore) und sind vollständig isoliert. Dadurch wird sichergestellt, dass Sie die absolute Kontrolle über Ihre digitalen Assets behalten, ohne ausländischen Gerichtsbarkeiten oder proprietärem Vendor Lock-in ausgesetzt zu sein.