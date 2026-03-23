---
sidebar_label: Images
sidebar_position: 4
---

# Images

In der SovereignSecure Cloud ist ein **Image** eine Vorlage für eine virtuelle Maschine, die ein vorkonfiguriertes Betriebssystem und möglicherweise weitere Software enthält. Images werden als Basis für die Bereitstellung neuer Compute-Instanzen verwendet.

Unser Image-Dienst wird von OpenStack Glance angetrieben und ist vollständig in die Cloud Management Platform (CMP) integriert.

## Image-Typen

Sie können bei der Bereitstellung einer neuen Instanz aus mehreren Arten von Images wählen:

*   **Öffentliche Images:** Standardmäßige, sichere und vollständig gepatchte Betriebssystem-Images, die von den Administratoren der SovereignSecure Cloud bereitgestellt und verwaltet werden. Diese umfassen typischerweise beliebte Linux-Distributionen (Ubuntu, CentOS, RHEL) und Windows Server-Umgebungen.
*   **Private Images (Benutzerdefinierte Images):** Images, die Sie selbst erstellen. Diese werden oft erstellt, indem ein Snapshot von einer bestehenden, vorkonfigurierten Instanz aufgenommen wird. Private Images sind nur für Benutzer innerhalb Ihres Projekts sichtbar.
*   **Freigegebene Images:** Images, die explizit zwischen verschiedenen Projekten oder Organisationen freigegeben (geteilt) wurden.

## Unterstützte Image-Formate

Wenn Sie Ihr eigenes benutzerdefiniertes Image hochladen, unterstützt die SovereignSecure Cloud mehrere Standardformate für Festplatten virtueller Maschinen. Das gängigste und am meisten empfohlene Format ist **QCOW2**, da es dynamische Größenanpassung und Snapshot-Unterstützung bietet.

Weitere unterstützte Formate sind:

*   `qcow2` (QEMU copy-on-write)
*   `raw` (Unstrukturiertes Festplatten-Image)
*   `iso` (Optisches Festplatten-Image)

!!! tip "Cloud-Init und Cloudbase-Init"
    Wenn Sie Ihre eigenen benutzerdefinierten Images mitbringen, empfehlen wir dringend, **cloud-init** (für Linux) oder **Cloudbase-Init** (für Windows) vor der Aufnahme des Images zu installieren. Dadurch wird sichergestellt, dass Ihre Instanzen beim Booten SSH-Schlüssel, Netzwerkkonfigurationen und Benutzerskripte ordnungsgemäß empfangen.

## Erstellen eines benutzerdefinierten Images

Sie können ein benutzerdefiniertes Image aus dem Root-Blockspeicher einer vorhandenen, laufenden Instanz erstellen, um deren genauen Status zu erfassen.

1.  Navigieren Sie in der Cloud-Konsole zu **Compute > Instanzen**.
2.  Wählen Sie die Instanz aus, die Sie erfassen möchten.
3.  Es wird dringend empfohlen, die Instanz zuerst zu **stoppen**, um die Datenintegrität sicherzustellen.
4.  Wählen Sie im Menü "Aktionen" die Option **Image erstellen**.
5.  Geben Sie einen Namen und eine Beschreibung für Ihr neues Image ein.

Sobald dies abgeschlossen ist, ist das neue Image in Ihrem Repository unter **Compute > Images** verfügbar und kann verwendet werden, um identische Klon-Instanzen zu starten.