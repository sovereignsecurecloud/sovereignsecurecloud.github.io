---
sidebar_label: Übersicht
sidebar_position: 1
---

# Instanzen Übersicht

Eine **Instanz** in der SovereignSecure Cloud ist eine skalierbare virtuelle Maschine (VM), die On-Demand-Rechenkapazität bietet. Jede Instanz besteht aus virtuellen CPUs, Arbeitsspeicher und Root-Blockspeicher, sodass Sie Ihre Anwendungen und Workloads in einer sicheren und isolierten Umgebung bereitstellen und ausführen können.

Unser Instanzdienst wird von OpenStack Nova angetrieben und bietet robuste und flexible virtuelle Serverfunktionen, die sich nahtlos in andere SovereignSecure Cloud-Dienste integrieren lassen.

## Hauptmerkmale

*   **Skalierbarkeit:** Skalieren Sie Ihre Rechenressourcen ganz einfach nach oben oder unten, indem Sie Instanz-Flavors (Profile/Größen) ändern, um sie an die Anforderungen Ihrer Workloads anzupassen.
*   **Flexibilität:** Wählen Sie aus einer Vielzahl von Betriebssystem-Images, einschließlich beliebter Linux-Distributionen und Windows Server.
*   **Netzwerkintegration:** Verbinden Sie Instanzen mit Ihren Virtual Private Clouds (VPCs) und Subnetzen, um eine sichere und private Netzwerkkommunikation zu ermöglichen.
*   **Sicherheit:** Verwenden Sie Sicherheitsgruppen, um granulare Firewall-Regeln zu definieren und Ihre Instanzen vor unbefugtem Zugriff zu schützen.
*   **Persistenter Speicher:** Instanzen können mit persistentem Blockspeicher für ihr Root-Laufwerk bereitgestellt werden, und zusätzliche Volumes können für Anwendungsdaten angehängt werden.
*   **API & Automatisierung:** Vollständige API-Unterstützung ermöglicht die programmatische Steuerung und Automatisierung der Instanzbereitstellung und -verwaltung.

## Komponenten

Jede Instanz wird aus den folgenden Kernkomponenten erstellt:

*   **Flavor:** Definiert die Rechenkapazität (vCPUs und RAM), die der Instanz zugewiesen wird.
    *   Beispiele: `t1.micro`, `m1.small`, `c1.medium`
*   **Image:** Die Betriebssystemvorlage (z. B. Ubuntu, RHEL, Windows Server), die als Basis für das Root-Laufwerk Ihrer Instanz verwendet wird.
*   **Speicher (Storage):**
    *   **Root-Laufwerk:** Das primäre Block-Storage-Volume, auf dem das Betriebssystem installiert ist.
    *   **Zusätzliche Volumes:** Persistente Block-Storage-Volumes, die für Anwendungsdaten an Instanzen angehängt werden können und Haltbarkeit und Flexibilität bieten.
*   **Netzwerk:**
    *   **Virtuelle Netzwerkschnittstellen (Ports):** Verbinden Instanzen mit Ihren definierten VPC-Subnetzen.
    *   **Floating IP:** Eine optionale öffentliche IP-Adresse, die einer Instanz für direkten Internetzugriff zugewiesen werden kann.
*   **Sicherheitsgruppen (Security Groups):** Virtuelle Firewalls, die den ein- und ausgehenden Netzwerkverkehr zu und von Ihren Instanzen steuern.
*   **Schlüsselpaar (Key Pair):** Wird für den sicheren SSH-Zugriff auf Linux-Instanzen verwendet.

## Lebenszyklus einer Instanz

Instanzen folgen typischerweise einem Lebenszyklus, der Folgendes umfasst:

*   **Erstellung:** Bereitstellung einer neuen Instanz aus einem Image und einem Flavor.
*   **Ausführung (Running):** Der aktive Zustand, in dem Ihre Anwendungen betriebsbereit sind.
*   **Stoppen/Starten:** Vorübergehendes Anhalten oder Fortsetzen einer Instanz.
*   **Größenänderung (Resizing):** Ändern des Flavors der Instanz, um ihre Rechenressourcen anzupassen.
*   **Snapshot-Erstellung:** Erstellen eines Images von einer laufenden oder gestoppten Instanz.
*   **Löschung:** Dauerhaftes Beenden einer Instanz und der zugehörigen Ressourcen.

## Erste Schritte

Um zu erfahren, wie Sie Ihre Instanzen Schritt für Schritt erstellen und verwalten, lesen Sie bitte das Benutzerhandbuch für Instanzen.