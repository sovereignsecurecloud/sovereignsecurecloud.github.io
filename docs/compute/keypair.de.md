---
sidebar_label: Schlüsselpaare
sidebar_position: 5
---

# Schlüsselpaare (Key Pairs)

Ein **Schlüsselpaar** ist eine sichere Authentifizierungsmethode, mit der Sie auf Ihre Instanzen in der SovereignSecure Cloud zugreifen können. Anstatt sich auf herkömmliche Passwörter zu verlassen, die anfällig für Brute-Force-Angriffe sein können, verwenden Schlüsselpaare die Public-Key-Kryptographie (SSH), um sicherzustellen, dass nur autorisierte Benutzer eine Verbindung zu Rechenressourcen herstellen können.

Ein Schlüsselpaar besteht aus zwei Teilen:

*   **Öffentlicher Schlüssel (Public Key):** Wird in Ihrem SovereignSecure Cloud-Projekt gespeichert und bei der Bereitstellung automatisch in Ihre Instanz injiziert (bei Linux normalerweise in `~/.ssh/authorized_keys`).
*   **Privater Schlüssel (Private Key):** Wird sicher auf Ihrem lokalen Rechner aufbewahrt und von Ihrem SSH-Client verwendet, um Ihre Identität nachzuweisen.

## Ein neues Schlüsselpaar erstellen

Sie können ein neues Schlüsselpaar direkt über die Cloud-Konsole generieren:

1. Navigieren Sie in der Cloud-Konsole zu **Compute > Schlüsselpaare**.
2. Klicken Sie auf **Schlüsselpaar erstellen**.
3. Geben Sie einen aussagekräftigen **Namen** für Ihr Schlüsselpaar ein.
4. Wählen Sie den **Schlüsseltyp** (SSH ist Standard).
5. Klicken Sie auf **Erstellen**.
6. **Wichtig:** Ihr Browser lädt den privaten Schlüssel (typischerweise eine `.pem`-Datei) automatisch herunter. Dies ist das *einzige* Mal, dass Sie diesen privaten Schlüssel herunterladen können. Bewahren Sie ihn an einem sicheren Ort auf Ihrem lokalen Rechner auf.

## Ein vorhandenes Schlüsselpaar importieren

Wenn Sie bereits ein eigenes SSH-Schlüsselpaar haben, das über `ssh-keygen` (Linux/macOS) oder PuTTYgen (Windows) generiert wurde, können Sie den öffentlichen Schlüssel in die Plattform importieren.

1. Navigieren Sie zu **Compute > Schlüsselpaare**.
2. Klicken Sie auf **Schlüsselpaar importieren**.
3. Geben Sie einen **Namen** ein, um dieses Schlüsselpaar zu identifizieren.
4. Fügen Sie den Inhalt Ihres **öffentlichen Schlüssels** (z. B. den Inhalt Ihrer Datei `id_rsa.pub` oder `id_ed25519.pub`) in das vorgesehene Textfeld ein.
5. Klicken Sie auf **Importieren**.

## Verbindung mit Ihrer Instanz herstellen

Sobald Ihre Instanz ausgeführt wird und ihr eine Floating IP zugewiesen wurde, können Sie sich mit Ihrem privaten Schlüssel damit verbinden.

### Linux / macOS

Öffnen Sie Ihr Terminal und verwenden Sie den Befehl `ssh`, wobei Sie den Pfad zu Ihrer privaten Schlüsseldatei mit dem Flag `-i` angeben:

```bash
chmod 400 mein-privater-schluessel.pem  # Stellen Sie sicher, dass der Schlüssel streng sichere Berechtigungen hat
ssh -i /pfad/zu/mein-privater-schluessel.pem benutzername@<Instanz-Floating-IP>
```

*(Hinweis: Der Standard-`benutzername` hängt vom verwendeten Image ab, z. B. `ubuntu`, `centos`, `cloud-user` oder `debian`)*.

### Windows (PuTTY)

1. Öffnen Sie **PuTTY**.
2. Geben Sie im Feld **Host Name (or IP address)** die Floating IP-Adresse der Instanz ein.
3. Navigieren Sie im linken Menü zu **Connection > SSH > Auth > Credentials**.
4. Klicken Sie auf **Browse** und wählen Sie Ihre private Schlüsseldatei aus (PuTTY benötigt das Format `.ppk`. Wenn Sie eine `.pem`-Datei heruntergeladen haben, verwenden Sie PuTTYgen zur Konvertierung).
5. Klicken Sie auf **Open**, um die Verbindung herzustellen.