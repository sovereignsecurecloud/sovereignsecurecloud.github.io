---
sidebar_label: Übersicht
sidebar_position: 1
---

# Cloud Management Platform (CMP)

Willkommen bei der Dokumentation der SovereignSecure Cloud Management Platform (CMP). Angetrieben von ManageIQ bietet unsere CMP ein einheitliches Self-Service-Portal zur Verwaltung Ihrer mandantenfähigen, souveränen Cloud-Umgebung. 
Sie ermöglicht es Benutzern, Workloads zu orchestrieren, die Auslastung zu verfolgen und Projektressourcen mit Leichtigkeit zu steuern, und das alles unter Einhaltung strenger Prinzipien der Datensouveränität.

## Vorteile der SovereignSecure CMP

Die Nutzung unserer CMP bietet Ihrem Unternehmen mehrere wichtige Vorteile:

*   **Verbesserte Governance:** Zentralisierte Kontrolle über die Bereitstellung von Ressourcen, um die Einhaltung von Unternehmensrichtlinien und gesetzlichen Anforderungen sicherzustellen.
*   **Kostentransparenz:** Detaillierte Chargeback- und Showback-Berichte zur genauen Verfolgung und Zuordnung von Cloud-Ausgaben.
*   **Self-Service-Bereitstellung:** Ermöglichen Sie es Benutzern, genehmigte Dienste schnell aus einem kuratierten Katalog bereitzustellen, wodurch der betriebliche Aufwand reduziert wird.
*   **Betriebseffizienz:** Automatisieren Sie Routineaufgaben und das Lebenszyklusmanagement für virtuelle Maschinen, Container und andere Cloud-Ressourcen.
*   **Multi-Cloud-Bereitschaft:** Obwohl ManageIQ derzeit auf OpenStack ausgerichtet ist, bietet es eine Grundlage für zukünftige Multi-Cloud-Management-Funktionen.

## Kernfunktionen

* **[Servicekataloge](catalog.md):** Ein Self-Service-Portal, in dem Benutzer vordefinierte, genehmigte IT-Dienste wie standardmäßige virtuelle Maschinen, mehrschichtige Anwendungs-Stacks und Kubernetes-Cluster bestellen können.
* **[Chargeback & Reporting](reporting.md):** Verfolgen Sie die finanziellen Kosten für die Ausführung Ihrer Workloads. Generieren Sie detaillierte Showback-/Chargeback-Berichte basierend auf der CPU-, Speicher-, Speicher- und Netzwerkauslastung.
*   **Lifecycle-Management:** Automatisieren Sie die Bereitstellung, Stilllegung und Skalierung von Instanzen und anderen Cloud-Ressourcen, um Abläufe zu rationalisieren und die Ressourcenoptimierung sicherzustellen.
*   **Durchsetzung von Quoten & Richtlinien:** Definieren und erzwingen Sie Ressourcenquoten und operative Richtlinien über Projekte und Benutzer hinweg, behalten Sie die Kontrolle und verhindern Sie die Ausbreitung von Ressourcen (Resource Sprawl).

## Zugriff auf die Cloud-Konsole

1.  **Öffnen Sie Ihren Webbrowser** und navigieren Sie zur URL der SovereignSecure Cloud-Konsole: `https://portal.sovereignsecurecloud.com`
2. Melden Sie sich mit den Single Sign-On (SSO)-Anmeldeinformationen Ihres Unternehmens oder Ihrem projektspezifischen Administratorkonto an.
3. Auf dem Dashboard können Sie eine Zusammenfassung Ihrer laufenden Workloads, ausstehenden Kataloganfragen und aktuellen Benachrichtigungen einsehen.

!!! tip "Für fortgeschrittene Benutzer und Automatisierung"
    Neben der grafischen Cloud-Konsole können Sie auch programmgesteuert mit der CMP und der zugrunde liegenden OpenStack-Infrastruktur interagieren. Weitere Informationen zur Verwendung der ManageIQ-REST-API und der nativen OpenStack-CLIs finden Sie im Abschnitt API & Automatisierung.