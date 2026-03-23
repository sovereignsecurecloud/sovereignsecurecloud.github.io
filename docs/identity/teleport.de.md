---
sidebar_label: Teleport PAM
---

# Privileged Access Management (PAM) mit Teleport

In einer Sovereign Cloud ist die Sicherung und Prüfung (Auditing) des administrativen Zugriffs auf die Infrastruktur von größter Bedeutung. Die SovereignSecure Cloud nutzt **Teleport** für ein umfassendes Privileged Access Management (PAM).

## Zero-Trust-Zugriff

Teleport ersetzt veraltete statische SSH-Schlüssel und VPNs durch identitätsbasierten Zero-Trust-Zugriff.

* **Zertifikatsbasierte Authentifizierung:** Anstatt statische `id_rsa`-Schlüssel zu verwalten, stellt Teleport kurzlebige, identitätsgebundene Zertifikate aus, die an Ihr Keycloak-SSO-Login gebunden sind.
* **Einheitlicher Zugriff:** Greifen Sie über ein einziges Gateway sicher auf SSH-Server, Kubernetes-Cluster, Datenbanken und interne Webanwendungen zu.

## Auditing und Compliance

Um die strengen Standards für Souveränität und Einhaltung gesetzlicher Vorschriften (Compliance) zu erfüllen, bietet Teleport Folgendes:

* **Sitzungsaufzeichnung (Session Recording):** Jede interaktive SSH- und Kubernetes-`exec`-Sitzung wird aufgezeichnet und kann für Sicherheitsprüfungen (Audits) wiedergegeben werden.
* **Detaillierte Audit-Protokolle:** Ein umfassendes Protokoll aller Zugriffsereignisse, ausgeführten Befehle und Dateiübertragungen, das direkt in unser SIEM (Wazuh) exportiert werden kann.
* **Just-In-Time-Zugriff:** Administratoren können temporäre, erweiterte Berechtigungen für bestimmte Infrastrukturelemente nur bei Bedarf für Notfall-Szenarien (Break-Glass) anfordern.