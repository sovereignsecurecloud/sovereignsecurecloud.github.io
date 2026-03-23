---
sidebar_label: Schlüsselverwaltung (KMS)
---

# Key Management Service (KMS)

Der Schutz kryptografischer Schlüssel und Geheimnisse ist eine entscheidende Säule zur Aufrechterhaltung der Datensouveränität. Die SovereignSecure Cloud bietet einen hochsicheren **Key Management Service (KMS)**, der von OpenStack Barbican angetrieben wird.

## Zentrale Speicherung von Geheimnissen

Der KMS fungiert als sicherer, API-gesteuerter Tresor für die Bereitstellung, Verwaltung und Speicherung von:
* Symmetrischen und asymmetrischen Verschlüsselungsschlüsseln
* SSL/TLS-Zertifikaten (verwendet von Load Balancern)
* Passwörtern und API-Token

## Transparente Datenverschlüsselung

Der KMS ist nativ in unsere zugrunde liegenden Speicherdienste integriert, um eine transparente Verschlüsselung im Ruhezustand (Data-at-Rest) zu ermöglichen:

* **Verschlüsselter Blockspeicher:** Sie können Ihre Cinder-Volumes so konfigurieren, dass sie mit dem LUKS-Format verschlüsselt werden. Der KMS bewahrt den Verschlüsselungsschlüssel des Volumes sicher auf. Der Hypervisor ruft den Schlüssel beim Start der Instanz direkt vom KMS ab, um die Festplatte "on the fly" (während des Betriebs) zu entschlüsseln.
* **Verschlüsselter Objektspeicher:** Server-Side Encryption (SSE) für Ceph Object Storage-Buckets kann mithilfe von Schlüsseln verwaltet werden, die im KMS gespeichert sind. So wird sichergestellt, dass Ihre unstrukturierten Daten verschlüsselt werden, bevor sie auf die physischen Laufwerke geschrieben werden.