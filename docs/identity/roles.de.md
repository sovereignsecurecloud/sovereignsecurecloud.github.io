---
sidebar_label: Rollen & Richtlinien
---

# Rollen & Richtlinien

Die SovereignSecure Cloud erzwingt eine strenge Zugriffskontrolle durch **rollenbasierte Zugriffskontrolle (Role-Based Access Control, RBAC)**. Indem Sie Benutzern innerhalb bestimmter Projekte Rollen zuweisen, können Sie granular vorschreiben, welche Aktionen sie ausführen dürfen, und so die Einhaltung des Prinzips der geringsten Privilegien sicherstellen.

## Standardrollen

Um die Zugriffsverwaltung zu vereinfachen, stellt die SovereignSecure Cloud eine Reihe vordefinierter Standardrollen bereit. Wenn Sie einem Projekt einen Benutzer hinzufügen, müssen Sie ihm eine oder mehrere dieser Rollen zuweisen:

* **Admin:** Gewährt vollen administrativen Zugriff im Rahmen des Projekts. Administratoren können jede Ressource (Compute, Storage, Netzwerk usw.) bereitstellen, ändern und löschen sowie Projektmitgliedschaften und -kontingente verwalten.
* **Member (Mitglied):** Die Standard-Operator-Rolle. Mitglieder können Ressourcen innerhalb des Projekts erstellen, verwalten und löschen, um ihre täglichen Aufgaben auszuführen. Sie können jedoch keine Konfigurationen auf Projektebene ändern oder den Zugriff anderer Benutzer verwalten.
* **Reader (Leser):** Gewährt reinen Lesezugriff. Leser können Instanzen, Netzwerke und Speichervolumes auflisten und deren Details anzeigen, jedoch keine Ressourcen erstellen, ändern oder löschen. Diese Rolle wird dringend für Sicherheitsprüfer (Auditors), Compliance-Beauftragte oder Dienstkonten zur automatisierten Überwachung empfohlen.

## Richtlinien (Policies)

Im Hintergrund werden Rollen mithilfe von **Richtlinien** bestimmten Aktionen zugeordnet. 

Eine Richtlinie ist eine Reihe von Regeln, die von den zugrunde liegenden Cloud-Diensten (z. B. Nova für Compute, Neutron für Netzwerke) jedes Mal ausgewertet werden, wenn eine API-Anfrage gestellt wird. Beispielsweise könnte eine Richtlinienregel vorschreiben, dass die API-Aktion `compute:create_instance` nur zulässig ist, wenn der anfragende Benutzer die Rolle `admin` oder `member` im Zielprojekt innehat.

Da die SovereignSecure Cloud eine "Secure-by-Default"-Haltung (Sicherheit als Standard) priorisiert, sind die Standardinfrastrukturrichtlinien streng abgeriegelt, um unbefugten lateralen Zugriff oder die Offenlegung von Ressourcen zu verhindern.

## Rollen zuweisen

Rollenzuweisungen sind streng auf die Projektebene beschränkt. Die Rolle eines Benutzers in einem Projekt gewährt ihm keinerlei Berechtigungen in einem anderen Projekt, es sei denn, diese wurden ausdrücklich zugewiesen.

So weisen Sie die Rolle eines Benutzers zu oder ändern sie:

1. Melden Sie sich bei der Cloud Management Platform (CMP) an.
2. Navigieren Sie zu **Identität > Projekte**.
3. Wählen Sie das entsprechende Projekt aus und gehen Sie zur Registerkarte **Mitglieder**.
4. Klicken Sie auf **Mitglied hinzufügen**, um einem neuen Unternehmensbenutzer Zugriff zu gewähren, oder klicken Sie auf das **Bearbeiten**-Symbol neben einem vorhandenen Benutzer, um dessen aktuelle Rollenzuweisung zu ändern.

!!! tip "Auditing (Prüfung)"
    Alle Rollenzuweisungen und -änderungen werden protokolliert und können in die SIEM-Plattform (Wazuh) exportiert werden, um Compliance- und souveräne Audit-Anforderungen zu erfüllen.