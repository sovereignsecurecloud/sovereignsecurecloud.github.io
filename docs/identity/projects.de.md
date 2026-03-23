---
sidebar_label: Benutzer & Projekte
---

# Benutzer & Projekte

In der SovereignSecure Cloud werden Mandantenfähigkeit (Multi-Tenancy) und sichere Ressourcenisolierung durch den Einsatz von **Projekten** (traditionell als Tenants/Mandanten bezeichnet) und **Benutzern** erreicht.

## Was ist ein Projekt?

Ein **Projekt** ist ein logischer Container, der zum Gruppieren und Isolieren von Cloud-Ressourcen verwendet wird. Jede von Ihnen erstellte Ressource – sei es eine Compute-Instanz, eine Virtual Private Cloud (VPC), ein Block Storage Volume oder ein Kubernetes-Cluster – gehört zu einem bestimmten Projekt.

* **Ressourcenisolierung:** Benutzer können Ressourcen außerhalb der Projekte, für die ihnen explizit Zugriff gewährt wurde, weder anzeigen noch mit ihnen interagieren.
* **Kontingente und Limits:** Cloud-Ressourcengrenzen (z. B. maximale Anzahl von vCPUs, gesamter RAM oder zugewiesener Speicher) werden auf Projektebene definiert, um eine Erschöpfung der Ressourcen zu verhindern.
* **Abrechnung und Showback:** Nutzungsmetriken und finanzielle Rückbelastungen (Chargebacks) werden pro Projekt verfolgt, sodass Kosten problemlos verschiedenen Abteilungen, Workloads oder Teams innerhalb Ihrer Organisation zugeordnet werden können.

## Was ist ein Benutzer?

Ein **Benutzer** repräsentiert einen menschlichen Operator oder ein automatisiertes Dienstkonto (API-Benutzer), das zentral über **Keycloak** authentifiziert wird. 

Während ein Benutzer eine einzige, föderierte Identität über die gesamte SovereignSecure Cloud-Plattform hinweg beibehält, wird seine Berechtigung zur Ausführung von Aktionen streng durch die **Rollen** bestimmt, die ihm innerhalb bestimmter **Projekte** zugewiesen sind.

### Zuordnung von Benutzern zu Projekten

Die Beziehung zwischen Benutzern und Projekten ist eine n:m-Beziehung:
* Ein einzelner Benutzer kann Mitglied in mehreren Projekten sein.
* Einem einzelnen Projekt können mehrere Benutzer zugewiesen sein.
* Ein Benutzer kann in verschiedenen Projekten unterschiedliche Rollen innehaben. Beispielsweise könnte ein Benutzer im Projekt „Entwicklung“ ein `admin` sein, im Projekt „Produktion“ jedoch ein `reader` mit reinem Lesezugriff.

## Verwalten des Projektzugriffs

Mandantenadministratoren können den Benutzerzugriff auf ihre Projekte direkt über die Cloud Management Platform (CMP) verwalten:

1. Navigieren Sie im CMP zu **Identität > Projekte**.
2. Wählen Sie Ihr Zielprojekt aus.
3. Gehen Sie auf die Registerkarte **Mitglieder**, um die aktuelle Liste der autorisierten Benutzer anzuzeigen.
4. Klicken Sie auf **Mitglied hinzufügen**, um nach einem bestehenden Unternehmensbenutzer zu suchen.
5. Wählen Sie den Benutzer aus und weisen Sie ihm eine entsprechende Rolle zu (z. B. `member`, `reader` oder `admin`).

*(Detaillierte Informationen zu den spezifischen Berechtigungen, die mit jeder Zuweisung verbunden sind, finden Sie in der Dokumentation zu Rollen & Richtlinien).*