---
sidebar_label: Schnellstartanleitung
sidebar_position: 1
---

# Schnellstartanleitung

Willkommen bei der SovereignSecure Cloud! Diese Schnellstartanleitung (Quick Start Guide) soll neuen Benutzern helfen, sich schnell zurechtzufinden und unsere sicheren und souveränen Cloud-Dienste zu nutzen. Wenn Sie diese Schritte befolgen, erfahren Sie, wie Sie auf die Cloud-Konsole (unterstützt von ManageIQ) zugreifen, deren grundlegenden Aufbau verstehen und Ihre erste Cloud-Ressource bereitstellen.

Unser Ziel ist es, Ihre ersten Erfahrungen zu vereinfachen, indem wir uns auf die wesentlichen Aufgaben konzentrieren, damit Sie schnell loslegen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

*   **SovereignSecure Cloud-Konto:** Ihre Organisation sollte Ihnen Anmeldeinformationen zur Verfügung gestellt haben.
*   **Internetzugang:** Eine stabile Internetverbindung für den Zugriff auf die Cloud-Konsole.

## Schritt 1: Zugriff auf die Cloud-Konsole

Die SovereignSecure Cloud-Konsole ist Ihr zentraler Knotenpunkt für die Verwaltung all Ihrer Cloud-Ressourcen.

1.  **Öffnen Sie Ihren Webbrowser** und navigieren Sie zur URL der Cloud-Konsole: `https://portal.sovereignsecurecloud.com`
2.  **Geben Sie Ihren Benutzernamen und Ihr Passwort ein**, die Ihnen von Ihrem Administrator zur Verfügung gestellt wurden. Wenn Ihr Unternehmen Single Sign-On (SSO) verwendet, werden Sie möglicherweise auf Ihre unternehmensinterne Anmeldeseite weitergeleitet.
3.  Klicken Sie auf **Login** (Anmelden).

Nach erfolgreicher Anmeldung werden Sie zu Ihrem personalisierten Dashboard weitergeleitet.

## Schritt 2: Das Dashboard verstehen

Das Dashboard bietet einen Überblick über Ihre zugewiesenen Ressourcen, aktiven Dienste und alle ausstehenden Anfragen. Zu den wichtigsten Bereichen, die Ihnen auffallen werden, gehören:

*   **Servicekatalog:** Durchsuchen und bestellen Sie vordefinierte Cloud-Dienste.
*   **Meine Dienste:** Zeigen Sie die von Ihnen bereits bereitgestellten Dienste an und verwalten Sie diese.
*   **Ressourcenauslastung:** Überwachen Sie Ihre CPU-, Speicher- (RAM) und Speicherplatznutzung (Storage).
*   **Benachrichtigungen & Alarme:** Bleiben Sie über Systemereignisse und wichtige Updates informiert.

## Schritt 3: Starten Ihrer ersten virtuellen Maschine (VM)

Lassen Sie uns eine einfache Linux-VM über den Servicekatalog bereitstellen.

1.  Klicken Sie im Dashboard auf **Servicekatalog** oder navigieren Sie zu **Cloud Management (CMP) > Servicekataloge**.
2.  Durchsuchen Sie die verfügbaren Dienste und wählen Sie eine **"Basic Linux VM"** oder ein ähnliches Angebot aus.
3.  **Füllen Sie die erforderlichen Details** im Bereitstellungsformular **aus**:
    *   **Servicename:** Ein eindeutiger Name für Ihre VM (z. B. `meine-erste-vm`).
    *   **Flavor (Größe):** Wählen Sie eine kleine Instanzgröße (z. B. `t1.micro`).
    *   **Image:** Wählen Sie ein öffentliches Linux-Image aus (z. B. `Ubuntu 22.04 LTS`).
    *   **Netzwerk:** Wählen Sie ein Standardnetzwerk oder -subnetz aus, falls verfügbar.
    *   **Schlüsselpaar (Key Pair):** Wählen Sie ein vorhandenes Schlüsselpaar oder erstellen Sie ein neues für den SSH-Zugriff.
4.  Überprüfen Sie Ihre Auswahl und klicken Sie auf **Order** (Bestellen) oder **Provision** (Bereitstellen).

Ihre Anfrage wird gesendet und die CMP beginnt mit der Bereitstellung Ihrer VM. Sie können den Status unter **Meine Dienste** verfolgen.

## Schritt 4: Nächste Schritte

Herzlichen Glückwunsch! Sie haben Ihre erste Cloud-Ressource erfolgreich gestartet. Um Ihre Reise fortzusetzen:

*   **Verbinden Sie sich mit Ihrer Instanz:** Erfahren Sie, wie Sie über SSH sicher auf Ihre neu erstellte VM zugreifen können.
*   **Verwalten Sie Ihre Ressourcen:** Entdecken Sie die vollen Funktionen der Cloud Management Platform.
*   **Entdecken Sie die Kerndienste:** Tauchen Sie tiefer in die Optionen für Compute, Storage und Networking ein.
*   **Automatisieren Sie mit APIs:** Entdecken Sie, wie Sie Ihre Workflows mithilfe unserer APIs integrieren und automatisieren können.