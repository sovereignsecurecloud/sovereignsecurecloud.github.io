---
sidebar_label: Benutzerhandbuch
sidebar_position: 2
---

# Benutzerhandbuch für Instanzen

## Instanzen erstellen
Sie können Instanzen erstellen, indem Sie entweder die folgenden Einstellungen verwenden oder Terraform/OpenTofu nutzen. Um Instanzen mit Terraform/OpenTofu zu erstellen, wählen Sie die Seite "Instanz erstellen" (Create Instance).

### OS-Einstellungen
Bestimmen Sie, wie der Root-Blockspeicher erstellt wird, der bei der Erstellung einer Instanz verwendet werden soll.

* Wählen Sie entweder **Neu erstellen und einrichten** (Create New and Set up) oder **Vorhandene Ressource verwenden** (Use Existing Resource).
* Wenn Sie "Neu erstellen und einrichten" auswählen, erstellen Sie den Root-Blockspeicher mithilfe eines Images.
* Wenn Sie "Vorhandene Ressource verwenden" auswählen, verwenden Sie einen zuvor erstellten Blockspeicher oder Snapshot.

### Image
Wählen Sie das Image aus, das das von Ihnen benötigte Betriebssystem enthält. Sie können zwischen öffentlichen Images, die von der SovereignSecure Cloud bereitgestellt werden, zuvor von Ihnen erstellten Images oder freigegebenen Images wählen.

Die verfügbaren Instanz-Flavors variieren je nach gewähltem Image. Wir empfehlen daher, bei der Erstellung einer Instanz zuerst ein Image auszuwählen.

| OS      | Größe der OS-Festplatte |  Speicher (RAM) |
| ----------- | --------------------|-----------|
| Linux       | 10GB      | 4GB     |
| Windows       | 40GB     | 4GB     |

### Root-Blockspeicher
Richten Sie den Root-Blockspeicher entsprechend den OS-Einstellungen ein.

* Wenn Sie **Neu erstellen und einrichten** auswählen, erstellen Sie den Root-Blockspeicher, indem Sie den **Typ des Blockspeichers** und die **Größe des Blockspeichers** angeben.
* Wenn Sie **Vorhandene Ressource verwenden** auswählen, geben Sie die **ursprüngliche Ressource** an, die als Root-Blockspeicher verwendet werden soll.

### Ursprüngliche Ressource
Sie können entweder einen zuvor erstellten **Blockspeicher** oder einen **Snapshot** auswählen.

Wenn Sie **Blockspeicher** auswählen, verwenden Sie den zuvor erstellten Blockspeicher als Root-Blockspeicher.
Wenn Sie **Snapshot** auswählen, wird der Root-Blockspeicher mithilfe eines zuvor erstellten Snapshots erstellt.

### Größe des Blockspeichers
Geben Sie die Größe des Root-Blockspeichers einer Instanz an.

Die Blockspeichergröße muss mindestens der vom Image benötigten Mindestgröße entsprechen.
Die Größe des Root-Blockspeichers variiert je nach Instanz-Flavor.

| Flavors      | Unterstützte Blockspeichergröße |
| ----------- | --------------------|
| g       | 10GB      |
| m       | 40GB     |

!!! note "Hinweis"
    Da Ihnen die Blockspeichergröße in Rechnung gestellt wird, ist es ineffizient, die Standard-Blockspeichergröße ohne Überlegung groß zu wählen. Wir empfehlen Ihnen, bei Bedarf zusätzlichen Blockspeicher hinzuzufügen.
    * Wenn Sie in den OS-Einstellungen für "Vorhandene Ressource verwenden" einen Blockspeicher auswählen, können Sie die Blockspeichergröße nicht ändern.
    * Wenn Sie in den OS-Einstellungen für "Vorhandene Ressource verwenden" einen Snapshot auswählen, muss die Blockspeichergröße gleich oder größer als die ursprüngliche Blockspeichergröße eingestellt werden.

### Typ des Blockspeichers
Bestimmt den Standard-Blockspeichertyp einer Instanz.

Wählen Sie entweder HDD oder SSD. Die Wahl des Blockspeichertyps wirkt sich auf Preis und Leistung aus.
Sie können den Blockspeichertyp nicht mehr ändern, sobald die Instanz erstellt ist.

!!! note "Hinweis"
    Wenn Sie in den OS-Einstellungen "Vorhandene Ressource verwenden" auswählen, können Sie den Blockspeichertyp nicht ändern.

### Verfügbarkeitszone
Wenn keine Verfügbarkeitszone angegeben ist, wird eine zufällige Zone ausgewählt. Eine Instanz kann einen Blockspeicher nur verwenden, wenn beide in derselben Verfügbarkeitszone existieren. Wenn sich der Blockspeicher, den Sie verwenden möchten, in einer bestimmten Verfügbarkeitszone befindet, wählen Sie diese Zone aus.

!!! note "Hinweis"
    * Ressourcen in einer VPC können in jeder beliebigen Verfügbarkeitszone verwendet werden.
    * Wenn Sie in den OS-Einstellungen "Vorhandene Ressource verwenden" auswählen, können Sie die Verfügbarkeitszone nicht ändern.

Weitere Informationen zu Verfügbarkeitszonen finden Sie unter "Verfügbarkeitszone" in der Instanz-Übersicht.

### Flavor
Sie können verschiedene Flavors (Profile/Größen) basierend auf den Leistungsspezifikationen der virtuellen Hardware auswählen. Die Auswahl einiger Flavors kann jedoch eingeschränkt sein, je nachdem, welche Hardwareleistung Ihr Image erfordert. Weitere Details finden Sie in der Instanz-Übersicht.

!!! note "Hinweis" 
    1 vCPU bezieht sich auf einen Sockel, der aus einem Thread und einem Kern (Core) besteht. Die Anzahl der Threads und Kerne pro Sockel ist konstant (jeweils einer).

Instanz-Flavors können in der SovereignSecure Cloud-Konsole auch nach der Instanzerstellung geändert werden, von höheren zu niedrigeren Spezifikationen und umgekehrt. Beachten Sie jedoch, dass einige Flavors nicht geändert werden können. Weitere Informationen finden Sie unter "Flavor ändern".

!!! warning "Warnung"
     Der Root-Blockspeicher einer Instanz kann nicht durch Änderung der Instanz-Flavors geändert werden.

### Anzahl der Instanzen
Sie können die Anzahl der Instanzen angeben, die Sie erstellen möchten, wenn Sie mehrere Instanzen mit demselben Image, derselben Verfügbarkeitszone, demselben Flavor, derselben Blockspeichergröße, demselben Schlüsselpaar und denselben Netzwerkeinstellungen erstellen. Die Instanznamen entsprechen dem von Ihnen angegebenen Namen, wobei am Ende Zahlen wie -1 und -2 angehängt werden. Wenn Sie beispielsweise zwei Instanzen mit dem Namen "meine-instanz" erstellen, erhalten Sie "meine-instanz-1" und "meine-instanz-2". Die maximale Anzahl von Instanzen, die Sie auf einmal erstellen können, beträgt 10.

Wenn Sie mehrere Instanzen erstellen, ohne eine Verfügbarkeitszone anzugeben, wird jede Instanz in einer zufällig ausgewählten Verfügbarkeitszone erstellt. Wenn beispielsweise zwei Instanzen ohne Angabe einer Verfügbarkeitszone erstellt werden, können sie in derselben oder in verschiedenen Zonen erstellt werden. Wenn alle Instanzen in derselben Verfügbarkeitszone erstellt werden müssen, wählen Sie eine bestimmte Zone aus.

!!! note "Hinweis" 
    Wenn Sie in den OS-Einstellungen für "Vorhandene Ressource verwenden" Blockspeicher oder in den Netzwerkeinstellungen "Vorhandene Netzwerkschnittstelle verwenden" auswählen, ist die Anzahl der Instanzen auf 1 begrenzt.

### Schlüsselpaar (Key Pair)
Verwenden Sie ein vorhandenes Schlüsselpaar oder erstellen Sie ein neues. Um ein vorhandenes Schlüsselpaar zu registrieren, siehe "Schlüsselpaar importieren (Windows)" für Windows-Benutzer und "Schlüsselpaar importieren (Mac und Linux)" für Mac- und Linux-Benutzer.

!!! note "Hinweis"
    Ein Schlüsselpaar ist eine dem Benutzerkonto zugewiesene Ressource und wird daher nicht gelöscht, wenn Sie ein Projekt löschen.

### Netzwerk
Wählen Sie ein in Ihrer VPC definiertes Subnetz aus, um eine Verbindung zu einer Instanz herzustellen. Für jedes ausgewählte Subnetz wird in der Instanz eine Netzwerkschnittstelle erstellt, um eine Verbindung zu diesem Subnetz herzustellen. Sie können die Reihenfolge der ausgewählten Subnetze ändern, um die Netzwerkschnittstellen zu ändern. In diesem Fall wird die erste Netzwerkschnittstelle (eth0) als Standard-Gateway festgelegt.

Weitere Details zum Erstellen und Verwalten von Netzwerken finden Sie in der VPC-Übersicht.

### Floating IP
Wählen Sie aus, ob Sie nach der Instanzerstellung eine Floating IP verwenden möchten. Wenn Sie diese Option aktivieren, wird eine neue Floating IP erstellt und mit der ersten Netzwerkschnittstelle verbunden. Beachten Sie, dass die erste Netzwerkschnittstelle mit einem Subnetz verbunden sein muss, in dem ein Internet-Gateway konfiguriert ist.

Floating IPs können unter Instanz > Verwaltung oder Instanz > Floating IP verwaltet werden. Weitere Details zu Floating IPs finden Sie im VPC-Konsolenhandbuch.

### Sicherheitsgruppe
Wählen Sie Sicherheitsgruppen aus, in die die Instanz aufgenommen werden soll. Eine Instanz kann in mehrere Sicherheitsgruppen aufgenommen werden. In diesem Fall gilt:

* Die Instanz kann über das Netzwerk mit allen anderen Instanzen kommunizieren, die in jeder Sicherheitsgruppe enthalten sind. Wenn Sie es mit einer Instanz mit sensiblen Daten zu tun haben, auf die andere Instanzen nicht zugreifen sollen, müssen Sie die Sicherheitsgruppen sorgfältig auswählen.
* Die Regeln aller ausgewählten Sicherheitsgruppen werden aggregiert und auf die externe Netzwerkkommunikation der Instanz angewendet.

Weitere Details zu Sicherheitsgruppen finden Sie im VPC-Konsolenhandbuch.

### Zusätzlicher Blockspeicher
Wählen Sie aus, ob Sie nach der Instanzerstellung einen zusätzlichen Blockspeicher anhängen möchten. Wenn Sie diese Option aktivieren, wird ein neuer Blockspeicher, der vom Root-Blockspeicher getrennt ist, erstellt und an die Instanz angehängt. Wie beim Root-Blockspeicher können Sie Name, Speichertyp und Größe des von Ihnen erstellten zusätzlichen Blockspeichers angeben.

Indem Sie den Root-Blockspeicher nur für das Betriebssystem verwenden und Ihre häufig verwendeten Anwendungen und Daten auf dem zusätzlichen Blockspeicher ablegen, können Sie Ihre Anwendungen und Daten mithilfe der Funktionen zum Anhängen/Trennen von Blockspeichern und für Snapshots einfach migrieren oder kopieren. Wenn ein Instanzausfall auftritt, können Sie Ihre Dienste außerdem problemlos wiederherstellen, indem Sie einfach den zusätzlichen Blockspeicher trennen und an eine andere Instanz anhängen.

Blockspeicher kann auch unter Instanz > Blockspeicher verwaltet werden. Weitere Details zum Blockspeicher finden Sie im Blockspeicher-Handbuch.

### Platzierungsrichtlinie (Placement Policy)
Sie können Platzierungsrichtlinien verwenden, um Instanzen auf verschiedenen Hypervisoren zu platzieren. Wenn Sie bei der Instanzerstellung eine Platzierungsrichtlinie festlegen, werden Instanzen, die derselben Platzierungsrichtlinie zugewiesen sind, auf verschiedenen Hypervisoren erstellt.

!!! warning "Warnung"
    Die Instanzerstellung kann in Situationen fehlschlagen, in denen eine verteilte Bereitstellung nicht möglich ist.

### Benutzerskript (User Script)
Sie können ein Skript angeben, das nach der Instanzerstellung ausgeführt werden soll. Das Benutzerskript wird nach dem anfänglichen Start der Instanz und nach Abschluss des Initialisierungsprozesses (einschließlich Netzwerkkonfiguration) ausgeführt. Benutzerskripte in der SovereignSecure Cloud werden durch automatisierte Tools wie cloud-init (Linux) und Cloudbase-init (Windows) ausgeführt, die in die offiziellen Images eingebettet sind.

!!! warning "Warnung"
    Benutzerskripte werden mit Root- (Linux) / Administrator- (Windows) Rechten ausgeführt.

#### Linux
Die erste Zeile eines Benutzerskripts muss mit `#!` beginnen.

```bash
#!/bin/bash
```
...
Damit ein Benutzerskript erfolgreich ausgeführt werden kann, müssen die Protokolldateien in der Instanz überprüft werden. Sie können die Ausgabe-/Fehlerprotokolle des Skripts unter `/var/log/cloud-init-output.log` überprüfen.

#### Windows
Windows-Images unterstützen sowohl Batch- als auch PowerShell-Formate für Benutzerskripte. Das Format wird durch einen Indikator bestimmt, der in der ersten Zeile angegeben ist.

* Batch-Skript
```batch
rem cmd
...
```

* PowerShell-Skript
```powershell
#ps1_sysnative
...
```
Um sowohl Batch als auch PowerShell in Ihrem Skript zu verwenden, verwenden Sie das folgende Format.

* EC2-Format
```
<script>
...
</script>
<powershell>
...
</powershell>
```
Protokolle von Benutzerskripten finden Sie unter 
>  *C:\Program Files\Cloudbase Solutions\Cloudbase-Init\log\cloudbase-init.*

Weitere Details zu Benutzerskripten finden Sie in den cloud-init- oder Cloudbase-init-Handbüchern.

### Zusätzliche Instanzfunktionen
#### Instanzstatus ändern
Der Status einer Instanz kann durch Stoppen, Beenden (Löschen) und Starten geändert werden.

Weitere Details zu Hypervisor-Ressourcen und Gebühren für das Stoppen, Beenden und Löschen von Instanzen finden Sie in der folgenden Tabelle.

| Klassifizierung | Instanz stoppen | Instanz beenden | Instanz löschen |
| -------------- | ------------- | ------------------ | --------------- |
| **Hypervisor-Ressource** | Ressource bleibt zugewiesen | Ressource wird zurückgegeben und beim Start der Instanz neu zugewiesen | Ressource wird entfernt |
| **Preisgestaltung für Instanz** | Preis für Stoppen angewendet | Kostenlos | Kostenlos |
| **Preisgestaltung für andere verbundene Ressourcen** | Wird berechnet | Wird berechnet | Wird berechnet |

!!! note "Hinweis"
    GPU-Instanzen können nicht beendet werden und verursachen auch im gestoppten Zustand normale (100 %) Gebühren.

#### Image erstellen
Erstellen Sie ein Image aus dem Root-Blockspeicher einer Instanz. Es wird empfohlen, Instanzen vor dem Erstellen eines Images zu stoppen, um die Datenintegrität sicherzustellen.

Obwohl es möglich ist, ein Image von einer Instanz zu erstellen, die keinen freien Speicherplatz mehr in ihrem Root-Blockspeicher hat, sind solche Images für andere Instanzen unbrauchbar, da sie nicht richtig initialisiert werden können. Stellen Sie vor dem Erstellen eines Images sicher, dass Ihre Instanz über mindestens 100 KB freien Speicherplatz verfügt.

Erstellte Images werden als private Images unter Compute > Image registriert. Sie können das registrierte Image verwenden, um eine Instanz mit einem Blockspeicher zu erstellen, der mit dem der ursprünglichen Instanz identisch ist.

!!! warning "Warnung"
    Die Größe des erstellten Images kann größer sein als die tatsächliche Nutzung des Root-Blockspeichers.

#### Floating IP zuweisen/trennen
Eine Floating IP kann unabhängig vom Status der Instanz mit einer Instanz verknüpft oder von dieser getrennt werden. Wenn Sie keine Floating IP zur Verfügung haben oder die gewünschte Floating IP nicht verfügbar ist, können Sie eine erstellen, indem Sie auf "Erstellen" klicken. Alternativ kann eine Floating IP auch unter Netzwerk > VPC > Floating IP erstellt werden.

Weitere Details zu Floating IPs finden Sie in der VPC-Übersicht.

#### Sicherheitsgruppe ändern
Die Sicherheitsgruppen einer Instanz können unabhängig vom Status der Instanz geändert werden. Geänderte Sicherheitsgruppen werden sofort angewendet.

Weitere Details zu Sicherheitsgruppen finden Sie unter Sicherheitsgruppe und in der VPC-Übersicht.

#### Netzwerk-Subnetz ändern
Das Netzwerk-Subnetz einer Instanz kann nur geändert werden, während die Instanz gestoppt ist. Wenn Sie ein Subnetz hinzufügen, wird automatisch eine Netzwerkschnittstelle auf Ihrer Instanz erstellt, die mit diesem Subnetz verbunden wird. Wenn Sie mehrere Subnetze auf einmal hinzufügen, wird die Reihenfolge der neu erstellten Netzwerkschnittstellen auf der Instanz zufällig festgelegt. Wenn Sie ein Subnetz aus einer Instanz löschen, wird automatisch die Netzwerkschnittstelle gelöscht, die zusammen mit dem Subnetz erstellt wurde.

#### Flavor ändern
Instanz-Flavors können geändert werden, sobald eine Instanz gestoppt wurde. Wenn eine Instanz ausgeführt wird, klicken Sie unter Zusätzliche Funktionen auf "Instanz stoppen", um die Instanz anzuhalten.

Sie können eine Instanz nur in ein anderes Flavor ändern, das mit ihrem aktuellen Flavor kompatibel ist.

* Instanzen mit `m2`, `c2`, `r2`, `t2`, `x1` Flavor können in `m2`, `c2`, `r2`, `t2`, `x1` Flavors geändert werden.
* Instanzen mit `m2`, `c2`, `r2`, `t2`, `x1` Flavor können NICHT in `u2` Flavors geändert werden.
* Instanzen mit `u2` Flavor können nicht in andere Flavors geändert werden, sobald sie erstellt wurden, auch nicht in solche desselben `u2` Flavors.

Wenn Sie Flavors ändern, werden Aufgaben zur Größenänderung der Instanz und zur Bestätigung der Größenänderung ausgeführt. Wenn alle Aufgaben abgeschlossen sind, ändert die VM ihren Status in "Shutoff" (Ausgeschaltet). Sie können die Instanz starten, indem Sie unter Zusätzliche Funktionen auf "Instanz starten" klicken.

!!! note "Hinweis" 
    Die Größe des Root-Blockspeichers der Instanz kann nicht geändert werden. Wenn eine Instanz zusätzlichen Blockspeicherplatz benötigt, hängen Sie einen Blockspeicher an. Weitere Informationen zum Anhängen von Blockspeicher finden Sie in der Blockspeicher-Übersicht.

Instanzen werden ab dem Moment, in dem die Änderung abgeschlossen ist, mit dem neuen Flavor berechnet.

#### OS-Details der Instanz ändern
Sie können die Betriebssysteminformationen (OS) der Instanz unabhängig vom Status der Instanz ändern. 

Klicken Sie auf der Seite Compute > Instanz auf die Instanz, deren OS-Informationen Sie ändern möchten. Klicken Sie auf der Registerkarte "Basisinformationen" im Detailbildschirm dieser Instanz auf OS > Ändern.

!!! note "Hinweis" 
    Sie können den OS-Typ nicht ändern.

#### Instanzbeschreibung ändern
Sie können die Instanzbeschreibung unabhängig vom Status der Instanz ändern. 

Klicken Sie auf der Seite Compute > Instanz auf die Instanz, deren Informationen Sie ändern möchten. Klicken Sie auf der Registerkarte "Basisinformationen" im Detailbildschirm dieser Instanz auf Beschreibung > Ändern.

#### Schlüsselpaar (Key Pair) der Instanz ändern
Sie können das Schlüsselpaar der Instanz nur ändern, wenn die Instanz aktiv ist.

Klicken Sie auf der Seite Compute > Instanz auf die Instanz, deren Schlüsselpaarinformationen Sie ändern möchten. Klicken Sie auf der Registerkarte "Basisinformationen" im Detailbildschirm dieser Instanz auf Schlüsselpaar > Ändern.

Ändern Sie das Schlüsselpaar des Instanzstandardkontos in das ausgewählte Schlüsselpaar. Das Instanzstandardkonto finden Sie auf der Registerkarte "Verbindungsinformationen" im unteren Detailbildschirm der Instanz.

!!! warning "Warnung"
    Wenn Sie ein Instanzschlüsselpaar ändern, werden alle öffentlichen Schlüsselinformationen in der Instanz gelöscht, mit Ausnahme des ausgewählten Schlüsselpaars.

!!! note "Hinweis" 
    Nur Projektmitglieder mit den ADMIN-Berechtigungen für die Basisinfrastruktur können das Instanzschlüsselpaar ändern, welches nicht geändert werden kann, wenn es sich um eine Windows-OS-Instanz handelt.

!!! note "Hinweis" 
    Wenn die zur Erstellung der Instanz verwendete Image-Version alt ist, ist die Funktion zum Ändern von Schlüsselpaaren möglicherweise nicht verfügbar.

#### Platzierungsrichtlinien (Placement Policies) verwalten
Sie können Platzierungsrichtlinien erstellen und löschen sowie eine Liste der Instanzen anzeigen, die Platzierungsrichtlinien zugewiesen sind.

Es wird nur der Platzierungsrichtlinientyp Anti-Affinity (Anti-Affinität) für verteilte Platzierung bereitgestellt.

Sie können eine Platzierungsrichtlinie auch dann löschen, wenn ihr Instanzen zugewiesen sind. In diesem Fall werden die Instanzen nicht gelöscht.

### Schlüsselpaare
#### Schlüsselpaare importieren (Windows)
Sie können puttygen verwenden, das bei der Installation des PuTTY SSH-Clients mitinstalliert wird, um ein Schlüsselpaar zu erstellen und in der SovereignSecure Cloud zu registrieren.

Stellen Sie sicher, dass PuTTY installiert ist.

Führen Sie puttygen aus.

*[Bild: PuTTYgen]*

Wählen Sie RSA (oder SSH-2 RSA in älteren Versionen von puttygen) unter "Parameters" aus. Klicken Sie unter "Actions" auf Generate. Bewegen Sie Ihre Maus kontinuierlich im leeren Bereich, um den Schlüssel zu generieren.

Nachdem der Schlüssel generiert wurde, ist der Inhalt der öffentlichen Schlüsseldatei (Public Key) wie unten gezeigt sichtbar. Fügen Sie den Inhalt des öffentlichen Schlüssels in das Feld "Öffentlicher Schlüssel" unter "Schlüsselpaar abrufen" ein, um das Schlüsselpaar zu registrieren.

*[Bild: PuTTYgen generierter Schlüssel]*

Klicken Sie unter "Actions" auf "Save private key", um den privaten Schlüssel zu speichern. Wenn Sie den privaten Schlüssel speichern, ohne eine Passphrase (Kennwort) einzugeben, wird die Meldung "Are you sure you want to save this key without a passphrase to protect it?" angezeigt. Um Ihren konvertierten privaten Schlüssel sicherer zu verwenden, legen Sie vor dem Speichern eine Passphrase fest.

!!! warning "Warnung"
    Wenn Sie sich automatisch an Ihrer Instanz anmelden möchten, sollten Sie keine Schlüssel-Passphrase festlegen. Wenn eine Passphrase verwendet wird, müssen Sie diese während der Anmeldung manuell eingeben.

Das registrierte Schlüsselpaar kann zum Erstellen von Instanzen verwendet werden, und der private Schlüssel des Schlüsselpaars muss beim Zugriff auf Instanzen verwendet werden. Weitere Details zum Zugriff auf Instanzen finden Sie in der Instanz-Übersicht.

Genau wie bei den in der SovereignSecure Cloud erstellten Schlüsselpaaren müssen auch importierte Schlüsselpaare sorgfältig verwaltet werden, da offengelegte private Schlüssel von jedem missbraucht werden können, um auf Instanzen zuzugreifen.

#### Schlüsselpaare importieren (Mac und Linux)
Schlüsselpaare, die mit ssh-keygen unter Mac oder Linux erstellt wurden, können in der SovereignSecure Cloud registriert werden. Verwenden Sie den folgenden Befehl, um ein Schlüsselpaar zu erstellen.

```
$ ssh-keygen -t rsa -f my_key.key
```

Sie können eine Passphrase für das Schlüsselpaar festlegen, auch wenn dies nicht zwingend erforderlich ist. Wenn Sie Ihr Schlüsselpaar sicherer verwenden möchten, empfehlen wir, eine Passphrase festzulegen. Die Datei, an die der angegebene Schlüsselpaarname `.pub` angehängt ist, enthält den öffentlichen Schlüssel.

```
$ cat my_key.key.pub
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCnnUAe36txQqk8J7VzbNuYKVQQ3gbNoClndHMX49OD+1Rw5xrDFLUKQqxbBDtlNMoA9tKBZNrQBpKr1kFEtvMIj1HPkH9ocb4MbuoVVjpkIhixbKMMJPDQ4JQJxaifsjR59YsZyDAp0aXZp+o+OB97P3S4AKPY2kQR0JdSr30+6Av6smf+3mZceAE4abzklfbyWT5slP1im/wfYEPO3QBEDl/0JbmTjKWPYI6QnbwnPRHS63SJ+Kd2QeYQYJCadv7X4mXnw81qEIWq/dx1SQkGDTNgR7lnN2ApFlU5EZcow69z6tiCr0hlyigwjGooMg3wTZvcSlYcVeTzZ755RArd ...
```
Fügen Sie den Inhalt des öffentlichen Schlüssels in das Feld "Öffentlicher Schlüssel" unter "Schlüsselpaar abrufen" ein, um das Schlüsselpaar zu registrieren.

Das registrierte Schlüsselpaar kann zum Erstellen von Instanzen verwendet werden, und der private Schlüssel des Schlüsselpaars muss beim Zugriff auf Instanzen verwendet werden. Weitere Details zum Zugriff auf Instanzen finden Sie unter "Zugriff auf Instanzen".

Genau wie bei den in der SovereignSecure Cloud erstellten Schlüsselpaaren müssen auch importierte Schlüsselpaare sorgfältig verwaltet werden, da offengelegte private Schlüssel von jedem missbraucht werden können, um auf Instanzen zuzugreifen.