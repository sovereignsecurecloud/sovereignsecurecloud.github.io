---
sidebar_label: Servicekataloge
sidebar_position: 2
---

# Servicekataloge

Der Servicekatalog ist eine Kernfunktion der SovereignSecure Cloud Management Platform (CMP), angetrieben von ManageIQ. Er bietet ein Self-Service-Portal, in dem Benutzer vordefinierte und genehmigte Cloud-Dienste durchsuchen, bestellen und verwalten können. Dies rationalisiert den Bereitstellungsprozess, stellt die Einhaltung von Richtlinien sicher und verringert den Bedarf an direkten IT-Eingriffen.

## Was sind Servicekataloge?

Servicekataloge präsentieren eine kuratierte Liste von IT-Diensten, die Ihr Unternehmen zur Verfügung gestellt hat. Diese Dienste können von einfachen virtuellen Maschinen bis hin zu komplexen mehrschichtigen Anwendungen oder Kubernetes-Clustern reichen, die alle mit vorab genehmigten Konfigurationen und Richtlinien gepackt sind.

**Zu den wichtigsten Vorteilen gehören:**

*   **Self-Service:** Benutzer können Ressourcen bei Bedarf bereitstellen, ohne auf manuelle Genehmigungen oder Konfigurationen warten zu müssen.
*   **Standardisierung:** Stellt sicher, dass alle bereitgestellten Ressourcen den Unternehmensstandards, Sicherheitsrichtlinien und Best Practices entsprechen.
*   **Governance & Compliance:** Integriert sich in Quotenverwaltung und Genehmigungsworkflows, um die Kontrolle über Ressourcenverbrauch und -ausgaben zu behalten.
*   **Reduzierter betrieblicher Aufwand:** Automatisiert sich wiederholende Bereitstellungsaufgaben und entlastet das IT-Personal für strategischere Initiativen.

## Durchsuchen des Servicekatalogs

1.  **Melden Sie sich** bei der SovereignSecure Cloud-Konsole **an**.
2.  Klicken Sie im Haupt-Dashboard auf die Kachel **"Servicekatalog"** oder navigieren Sie über das Menü zu **Cloud Management (CMP) > Servicekataloge**.
3.  Sie sehen eine Liste der verfügbaren Serviceelemente, oft gruppiert nach Kategorien (z. B. "Compute", "Datenbanken", "Container", "Anwendungen").
4.  Klicken Sie auf ein Serviceelement, um dessen Details anzuzeigen, einschließlich einer Beschreibung, der geschätzten Kosten (falls zutreffend) und Konfigurationsoptionen.

## Einen Service bestellen

Sobald Sie den benötigten Service gefunden haben, ist der Bestellvorgang unkompliziert:

1.  **Wählen Sie das gewünschte Serviceelement** aus dem Katalog **aus**.
2.  Ein **Bereitstellungsformular** wird angezeigt, das nach Möglichkeit mit Standardwerten vorausgefüllt ist.
3.  **Füllen Sie die Pflichtfelder aus:**
    *   **Servicename:** Ein eindeutiger, beschreibender Name für Ihre neue Serviceinstanz.
    *   **Projekt/Abteilung:** Wählen Sie das Projekt oder die Abteilung aus, der dieser Service in Rechnung gestellt werden soll.
    *   **Konfigurationsoptionen:** Je nach Service können Sie VM-Größe (Flavor), Betriebssystem-Image, Speicherkapazität, Netzwerkeinstellungen oder anwendungsspezifische Parameter auswählen.
    *   **Genehmigungsnotizen (Optional):** Geben Sie zusätzliche Informationen für das Genehmigungsteam an, falls ein Genehmigungs-Workflow eingerichtet ist.
4.  **Überprüfen Sie** Ihre Auswahl und die geschätzten Kosten.
5.  Klicken Sie auf **"Bestellen"** oder **"Anfrage senden"**.

## Verfolgung Ihrer Serviceanfrage

Nachdem Sie eine Bestellung aufgegeben haben, können Sie deren Status verfolgen:

1.  Navigieren Sie zu **Cloud Management (CMP) > Meine Services**.
2.  Hier sehen Sie eine Liste aller von Ihnen bestellten Services mit ihrem aktuellen Status (z. B. "Genehmigung ausstehend", "Wird bereitgestellt", "Aktiv", "Fehlgeschlagen").
3.  Sie können auf einen Service klicken, um dessen detaillierten Status und Protokolle anzuzeigen und Aktionen wie "Stoppen", "Starten" oder "Zurückziehen" durchzuführen (sofern zulässig).