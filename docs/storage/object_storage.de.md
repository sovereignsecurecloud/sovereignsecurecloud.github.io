---
sidebar_label: Objektspeicher
---

# Objektspeicher (Object Storage)

Die SovereignSecure Cloud bietet hochgradig skalierbaren, äußerst langlebigen **Objektspeicher**, der vom Ceph RADOS Gateway (RGW) angetrieben wird. Unser Objektspeicher ist vollständig kompatibel mit der branchenüblichen Amazon S3 API, was die einfache Integration in Ihre bestehenden Anwendungen und Workflows ermöglicht.

Im Gegensatz zu Blockspeicher, der an bestimmte Compute-Instanzen angehängt ist, ist der Objektspeicher von überall über HTTP/HTTPS zugänglich, was ihn zur idealen Lösung für die Speicherung riesiger Mengen unstrukturierter Daten macht.

## Hauptmerkmale

* **Massive Skalierbarkeit:** Speichern Sie praktisch unbegrenzte Datenmengen. Der zugrunde liegende Ceph-Speichercluster übernimmt die automatische Skalierung (Scale-Out) ohne Benutzereingriff.
* **S3-Kompatibilität:** Unterstützt nativ Standard-S3-Tools, SDKs (wie Boto3) und REST-APIs. Sie können Workloads, die für Public Clouds entwickelt wurden, problemlos in unsere souveräne Umgebung migrieren, ohne Ihren Code umschreiben zu müssen.
* **Hohe Haltbarkeit (Durability):** Daten werden automatisch repliziert und per Erasure Coding über mehrere physische Knoten und Racks hinweg gesichert. Dies bietet unternehmenstaugliche Haltbarkeit gegen Hardwareausfälle.
* **Granulare Zugriffskontrolle:** Sichern Sie Ihre Buckets und Objekte mit standardmäßigen S3-Zugriffskontrolllisten (ACLs) und integrierten IAM-Richtlinien.
* **Datensouveränität:** Alle Objekte werden ausschließlich in unseren Onshore-, Sovereign-Rechenzentren gespeichert, was die Einhaltung lokaler Gesetze zur Datenresidenz garantiert.

## Häufige Anwendungsfälle

Objektspeicher ist sehr vielseitig und wird empfohlen für:

* **Backups und Archive:** Speichern von Datenbank-Dumps, Instanz-Snapshots und langfristigen Compliance-Archiven.
* **Medien und Inhalte:** Hosting von Bildern, Videos und großen Mediendateien für Webanwendungen.
* **Big Data & Machine Learning:** Dient als massiver Data Lake für Analysen, Protokolle (Logs) und KI/ML-Trainingsdatensätze.
* **Statische Assets:** Verteilung statischer Assets (HTML, CSS, JavaScript) für die Front-End-Webentwicklung.

## Erste Schritte

### Zugriff auf Objektspeicher

Sie können Ihren Objektspeicher direkt über die Cloud Management Platform (CMP) im Abschnitt **Speicher > Objektspeicher** (Storage > Object Storage) verwalten, wo Sie Buckets erstellen, Dateien hochladen und Berechtigungen verwalten können.

### Verwendung von S3-Clients

Um sich programmgesteuert oder über CLI-Tools (wie die `aws`-CLI, `s3cmd` oder Cyberduck) zu verbinden, müssen Sie **S3-Anmeldeinformationen** (Access Key und Secret Key) in Ihrem Benutzerprofil in der CMP generieren.

Konfigurieren Sie nach der Generierung Ihren Client so, dass er auf die Endpunkt-URL des SovereignSecure Cloud-Objektspeichers verweist.