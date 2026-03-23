---
sidebar_label: Freigegebener Dateispeicher
---

# Freigegebener Dateispeicher (Shared File Storage)

Zusätzlich zum Block- und Objektspeicher bietet die SovereignSecure Cloud **freigegebenen Dateispeicher**, der über OpenStack Manila verwaltet und von CephFS unterstützt wird.

Freigegebener Dateispeicher bietet standardmäßige, POSIX-kompatible Dateisysteme, die von mehreren Compute-Instanzen gleichzeitig gemountet werden können. Dies ist unerlässlich für Unternehmensanwendungen, die eine traditionelle NAS-Umgebung (Network Attached Storage) erwarten.

## Hauptmerkmale

* **Gleichzeitiger Zugriff:** Im Gegensatz zu Blockspeicher (Cinder), der normalerweise an eine einzelne Instanz gleichzeitig angehängt wird, ermöglicht freigegebener Dateispeicher Dutzenden oder Hunderten von VMs das gleichzeitige Lesen und Schreiben derselben Dateien.
* **Skalierbarkeit:** Dateifreigaben können nahtlos mit Ihren Datenanforderungen wachsen, ohne dass die zugrunde liegenden physischen Festplatten manuell partitioniert oder formatiert werden müssen.
* **Unterstützte Protokolle:** Wir unterstützen nativ sowohl **NFS** (Network File System) für Linux-Workloads als auch **CIFS/SMB** für Windows-Instanzen.

## Häufige Anwendungsfälle

* **Webserver-Cluster:** Hosting von gemeinsam genutzten Website-Assets (Bilder, CSS, Code) über eine Flotte von Webservern mit Lastausgleich (Load Balancing).
* **Content Management Systeme (CMS):** Speichern hochgeladener Medien für Anwendungen wie WordPress oder Drupal.
* **Unternehmensanwendungen:** Legacy-Software, die gleichzeitige Lese-/Schreibvorgänge auf einem freigegebenen Netzlaufwerk erfordert.

Dateifreigaben können über den Abschnitt **Speicher > Dateifreigaben** (Storage > File Shares) in der Cloud Management Platform (CMP) erstellt und verwaltet werden.