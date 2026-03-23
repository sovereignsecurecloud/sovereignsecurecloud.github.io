---
sidebar_label: Load Balancer
---

# Load Balancer

In der SovereignSecure Cloud verteilen Load Balancer as a Service (LBaaS) den eingehenden Anwendungsdatenverkehr auf mehrere Compute-Instanzen. Dies erhöht die Verfügbarkeit, Fehlertoleranz und Skalierbarkeit Ihrer Anwendungen. Unser Load-Balancing-Dienst ist nativ in das zugrunde liegende SDN integriert und wird durch OpenStack Octavia angetrieben.

## Kernkomponenten

Um einen Load Balancer einzurichten, konfigurieren Sie mehrere miteinander verbundene Komponenten:

*   **Load Balancer:** Das Stammobjekt, das eine bestimmte IP-Adresse in Ihrem Subnetz belegt. Um es über das Internet erreichbar zu machen, können Sie ihm eine Floating IP zuweisen.
*   **Listener:** Ein Prozess, der nach Verbindungsanfragen auf einem konfigurierten Protokoll und Port sucht (z. B. HTTP auf Port 80 oder TCP auf Port 443).
*   **Pool:** Eine logische Gruppe von Backend-Compute-Instanzen (Mitglieder), die die vom Listener weitergeleiteten Anfragen bedienen.
*   **Mitglied (Member):** Eine einzelne Compute-Instanz (angegeben durch ihre private IP und ihren Port), die zu einem Pool gehört.
*   **Gesundheitsmonitor (Health Monitor):** Ein Dienst, der die Poolmitglieder regelmäßig anpingt, um sicherzustellen, dass sie fehlerfrei funktionieren. Wenn ein Mitglied bei einer Integritätsprüfung durchfällt, leitet der Load Balancer keinen Datenverkehr mehr an dieses weiter, bis es sich erholt hat.

## Hauptmerkmale

*   **Layer 4- und Layer 7-Load Balancing:** Leiten Sie den Datenverkehr basierend auf systemnahen TCP/UDP-Protokollen (Layer 4) oder HTTP/HTTPS-Headern auf Anwendungsebene (Layer 7) weiter.
*   **TLS-Offloading/Terminierung:** Zentralisieren Sie SSL/TLS-Zertifikate auf dem Load Balancer selbst und entlasten Sie Ihre Backend-Instanzen von der rechenintensiven Aufgabe der Verschlüsselung und Entschlüsselung des Datenverkehrs.
*   **Erweiterte Routing-Algorithmen:** Wählen Sie, wie der Datenverkehr auf Ihre Instanzen verteilt wird:
    *   *Round Robin:* Verteilt Anfragen gleichmäßig und sequenziell auf alle Mitglieder.
    *   *Least Connections (Wenigste Verbindungen):* Sendet neue Anfragen an das Mitglied mit den wenigsten aktiven Verbindungen.
    *   *Source IP (Quell-IP):* Leitet Anfragen von derselben Client-IP an dasselbe Backend-Mitglied weiter (Sitzungspersistenz / Session Persistence).

## Einen Load Balancer erstellen

Sie können Load Balancer über die Cloud Management Platform (CMP) bereitstellen und konfigurieren:

1.  Navigieren Sie zu **Netzwerk > Load Balancer**.
2.  Klicken Sie auf **Load Balancer erstellen**.
3.  **Grundlegende Details:** Geben Sie einen Namen ein, wählen Sie die Ziel-VPC/das Ziel-Subnetz aus, in dem sich der Load Balancer befinden soll, und weisen Sie eine IP-Adresse zu.
4.  **Listener-Konfiguration:** Geben Sie das Protokoll (z. B. HTTP) und den Port (z. B. 80) für den eingehenden Datenverkehr an.
5.  **Pool-Konfiguration:** Wählen Sie einen Load-Balancing-Algorithmus (z. B. Round Robin).
6.  **Mitglieder:** Wählen Sie die Backend-Compute-Instanzen aus, die den Datenverkehr verarbeiten sollen, und geben Sie deren Überwachungsports (Listening Ports) an.
7.  **Gesundheitsmonitor:** Definieren Sie das Protokoll der Integritätsprüfung, das Ping-Intervall und die Timeout-Schwellenwerte.

### Öffentliche Präsenz und Sicherheit

Standardmäßig ist ein neuer Load Balancer nur innerhalb seines internen Subnetzes erreichbar. 

*   **Öffentlicher Zugang:** Um den Load Balancer über das öffentliche Internet zugänglich zu machen, navigieren Sie zu **Netzwerk > Floating IPs** und weisen Sie dem VIP-Port (Virtual IP) des Load Balancers direkt eine Floating IP zu.
*   **Sicherheitsgruppen:** Stellen Sie sicher, dass die **Sicherheitsgruppen**, die an Ihre Backend-Compute-Instanzen angehängt sind, eingehenden Datenverkehr (Ingress) auf den Mitgliedsports zulassen, der von der IP-Adresse des Load Balancers stammt.