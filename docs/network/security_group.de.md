---
sidebar_label: Sicherheitsgruppen
---

# Sicherheitsgruppen

In der SovereignSecure Cloud fungiert eine **Sicherheitsgruppe** (Security Group) als zustandsbehaftete (stateful), virtuelle Firewall, die den eingehenden (Ingress) und ausgehenden (Egress) Netzwerkverkehr für Ihre Compute-Instanzen steuert. 

Angetrieben von unserer OVN SDN-Schicht, werden Sicherheitsgruppenregeln verteilt und direkt auf Hypervisor-Port-Ebene durchgesetzt, was Zero-Trust-Netzwerke gewährleistet und laterale Bewegungen selbst zwischen Instanzen im selben Subnetz verhindert.

## Kernkonzepte

* **Standardmäßig blockiert (Ingress):** Wenn Sie eine neue Sicherheitsgruppe erstellen, enthält diese standardmäßig keine Regeln für eingehenden Datenverkehr. Das bedeutet, dass der gesamte eingehende Datenverkehr zur Instanz blockiert wird, bis Sie ihn ausdrücklich zulassen.
* **Standardmäßig zugelassen (Egress):** Standardmäßig enthalten neue Sicherheitsgruppen eine Regel, die den gesamten ausgehenden Datenverkehr zulässt, sodass Instanzen das Internet oder andere Ressourcen erreichen können.
* **Zustandsbehaftet (Stateful):** Sicherheitsgruppen sind zustandsbehaftet. Wenn Sie eine eingehende Anfrage zulassen (z. B. HTTP auf Port 443), wird der Antwortverkehr für diese spezifische Verbindung automatisch zugelassen, unabhängig von Ihren Ausgehenden-Regeln.
* **Mehrere Gruppen:** Sie können einer einzigen Instanz mehrere Sicherheitsgruppen zuweisen. Die resultierenden Berechtigungen sind die Vereinigung aller Regeln der zugewiesenen Gruppen.

## Aufbau einer Regel

Wenn Sie eine Regel innerhalb einer Sicherheitsgruppe erstellen, definieren Sie:

* **Richtung:** 
    * `Ingress` (Eingehender Datenverkehr, der für die Instanz bestimmt ist)
    * `Egress` (Ausgehender Datenverkehr, der von der Instanz ausgeht)
* **EtherType:** `IPv4` oder `IPv6`.
* **IP-Protokoll:** `TCP`, `UDP` oder `ICMP`.
* **Portbereich:** Der spezifische Port oder Portbereich, der geöffnet werden soll (z. B. `22` für SSH, `80` für HTTP).
* **Remote:** Definiert die Quelle (für Ingress) oder das Ziel (für Egress) des Datenverkehrs. Dies kann Folgendes sein:
    * **CIDR-Block:** Ein IP-Adressbereich (z. B. `0.0.0.0/0` für das gesamte Internet oder `192.168.1.0/24` für ein bestimmtes Subnetz).
    * **Andere Sicherheitsgruppe:** Sie können Datenverkehr dynamisch von jeder Instanz zulassen, die zu einer anderen spezifischen Sicherheitsgruppe gehört. Dies ist äußerst nützlich für mehrstufige Architekturen (z. B. wenn Ihre `Database`-Gruppe Datenverkehr nur von Ihrer `Web Servers`-Gruppe akzeptieren darf).

## Best Practices für eine Sovereign Cloud

* **Prinzip der geringsten Privilegien:** Verwenden Sie niemals `0.0.0.0/0` (alles zulassen), es sei denn, dies ist für öffentlich zugängliche Webdienste zwingend erforderlich. Beschränken Sie administrative Ports wie `22` (SSH) oder `3389` (RDP) auf Ihre spezifischen Unternehmens-VPN-IP-Bereiche oder Teleport-Gateways.
* **Mehrstufige Architekturen:** Verwenden Sie Sicherheitsgruppen-Referenzierungen anstelle von statischen IPs. Erstellen Sie separate Gruppen wie `frontend-sg`, `backend-sg` und `db-sg`. Erlauben Sie `db-sg`, nur Port 3306 von `backend-sg` zu akzeptieren.

## Sicherheitsgruppen verwalten

Sie können Sicherheitsgruppen über die Cloud Management Platform (CMP) verwalten:

1. Navigieren Sie zu **Netzwerk > Sicherheitsgruppen**.
2. Klicken Sie auf **Sicherheitsgruppe erstellen** und geben Sie einen aussagekräftigen Namen ein (z. B. `web-server-ports`).
3. Wählen Sie die neue Gruppe aus und klicken Sie auf **Regeln verwalten**.
4. Klicken Sie auf **Regel hinzufügen**, um Protokoll, Port und Remote-IP-Bereich anzugeben.

So wenden Sie die Sicherheitsgruppe auf eine Instanz an:

* **Während der Erstellung:** Wählen Sie beim Starten einer neuen Instanz die Sicherheitsgruppe auf der Registerkarte "Netzwerk" aus.
* **Nach der Erstellung:** Navigieren Sie zu **Compute > Instanzen**, wählen Sie Ihre Instanz aus und wählen Sie im Menü "Aktionen" die Option **Sicherheitsgruppen bearbeiten**.