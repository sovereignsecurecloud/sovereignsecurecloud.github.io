---
sidebar_label: Router & Floating IPs
---

# Router & Floating IPs

Während eine Virtual Private Cloud (VPC) isolierte Layer-2-Netzwerksegmente (Subnetze) bietet, benötigen Sie **Router**, um die Layer-3-Kommunikation zwischen diesen Subnetzen und der Außenwelt zu ermöglichen. Um Ihre Ressourcen dem öffentlichen Internet zugänglich zu machen, verwenden Sie **Floating IPs**.

## Virtuelle Router

In der SovereignSecure Cloud funktioniert ein virtueller Router ähnlich wie ein physischer Router in einem herkömmlichen Rechenzentrum. Angetrieben von unserer verteilten OVN SDN-Ebene erfolgt das Routing oft direkt am Hypervisor-Edge, was eine hocheffiziente Paketübermittlung ermöglicht.

### Wichtige Funktionen

* **Subnetz-Routing:** Verbinden Sie mehrere private Subnetze innerhalb derselben VPC, sodass Instanzen in verschiedenen Subnetzen miteinander kommunizieren können.
* **Externes Gateway (SNAT):** Indem ein Router an das externe Netzwerk (Internet) angeschlossen wird, erhalten Instanzen innerhalb Ihrer privaten Subnetze ausgehenden Internetzugriff (Source NAT). Dadurch können Instanzen Updates herunterladen oder auf externe APIs zugreifen, ohne direkt von außen erreichbar zu sein.

## Floating IPs (FIPs)

Eine **Floating IP** ist eine öffentlich routbare IP-Adresse, die Sie dynamisch mit einer Compute-Instanz oder einem Load Balancer verknüpfen und von diesen trennen können.

### Wie es funktioniert

* **Statische öffentliche Präsenz:** Instanzen haben typischerweise nur private IP-Adressen (z. B. `10.0.1.5`). Eine Floating IP bietet eine statische, öffentlich zugängliche IP (z. B. `203.0.113.10`).
* **1-zu-1 NAT:** Der virtuelle Router übernimmt die 1-zu-1-Netzwerkadressübersetzung (NAT) zwischen der öffentlichen Floating IP und der privaten IP der Instanz. Die Instanz selbst kennt ihre öffentliche IP nicht.
* **Hochverfügbarkeit:** Wenn eine Instanz ausfällt, können Sie ihre Floating IP sofort einer Standby-Instanz neu zuweisen, wodurch Ausfallzeiten für den öffentlichen Endpunkt Ihrer Anwendung minimiert werden.

## Konfigurationsschritte

### 1. Einen Router erstellen
1. Navigieren Sie zu **Netzwerk > Router** in der Cloud Management Platform (CMP).
2. Klicken Sie auf **Router erstellen**, geben Sie ihm einen Namen und wählen Sie das **Externe Netzwerk** aus, um ausgehenden Internetzugriff zu ermöglichen.
3. Klicken Sie nach der Erstellung auf den Router, navigieren Sie zu **Schnittstellen** und auf **Schnittstelle hinzufügen**, um Ihre internen VPC-Subnetze zu verbinden.

### 2. Eine Floating IP zuweisen und verknüpfen
1. Navigieren Sie zu **Netzwerk > Floating IPs**.
2. Klicken Sie auf **IP dem Projekt zuweisen**, um eine neue öffentliche IP aus dem Anbieterpool zu beziehen.
3. Wählen Sie die neu zugewiesene IP aus und klicken Sie auf **Verknüpfen**.
4. Wählen Sie den Instanzport (private IP) aus, dem Sie die Floating IP zuordnen möchten.

!!! tip "Sicherheit geht vor"
    Das Anhängen einer Floating IP macht Ihre Instanz öffentlich erreichbar. Stellen Sie sicher, dass Sie **Sicherheitsgruppen** richtig konfiguriert haben, um den eingehenden Datenverkehr nur auf die erforderlichen Ports zu beschränken (z. B. Port 443 für HTTPS oder Port 22 für SSH).