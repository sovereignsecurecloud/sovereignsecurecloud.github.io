---
sidebar_label: VPC & Subnetze
---

# Virtual Private Cloud (VPC) & Subnetze

In der SovereignSecure Cloud ist eine **Virtual Private Cloud (VPC)** eine logisch isolierte, private Netzwerktopologie, die Ihrem Projekt gewidmet ist. Angetrieben von unserem OVN/SONiC SDN-Stack bietet sie vollständige Kontrolle über Ihre Netzwerkumgebung, einschließlich IP-Adressbereichen, Subnetzen und Routing.

## Virtual Private Clouds (VPCs)

Eine VPC dient als grundlegende Grenze für Ihre Cloud-Ressourcen. Standardmäßig können Ressourcen, die in einer VPC bereitgestellt werden, nicht mit dem externen Internet oder anderen VPCs kommunizieren, es sei denn, dies wird ausdrücklich über Router und Floating IPs konfiguriert.

**Hauptmerkmale:**
*   **Absolute Isolierung:** Jede VPC ist auf Layer 2 und Layer 3 vollständig isoliert, wodurch souveräne Grenzen zwischen verschiedenen Mandanten und Projekten sichergestellt werden.
*   **Benutzerdefinierte Topologie:** Sie können Ihren eigenen internen IP-Adressraum definieren (z. B. `10.0.0.0/16` oder `192.168.1.0/24`), ohne sich Gedanken über Überschneidungen mit anderen Mandanten machen zu müssen.

## Subnetze

Ein **Subnetz** ist ein segmentierter Teil des IP-Adressbereichs einer VPC, in dem Sie Gruppen isolierter Ressourcen platzieren können. Wenn Sie eine Compute-Instanz starten, verbinden Sie diese mit einem oder mehreren spezifischen Subnetzen.

**Subnetz-Funktionen:**
*   **CIDR-Blöcke:** Sie legen den genauen CIDR-Block (Classless Inter-Domain Routing) für jedes Subnetz fest (z. B. `10.0.1.0/24`).
*   **DHCP & DNS:** Jedes Subnetz verfügt über einen integrierten, hochverfügbaren DHCP-Server, um Ihren Instanzen automatisch IP-Adressen zuzuweisen. Interne DNS-Auflösung wird ebenfalls standardmäßig bereitgestellt, sodass Instanzen sich gegenseitig anhand ihres Hostnamens auflösen können.
*   **Gateway-IP:** Subnetze reservieren normalerweise die erste nutzbare IP-Adresse (z. B. `10.0.1.1`) als Standard-Gateway für das Routing von Datenverkehr aus dem Subnetz.

## Erstellen einer VPC und eines Subnetzes

Sie können Ihre Netzwerktopologie direkt über die Cloud Management Platform (CMP) entwerfen:

1. Navigieren Sie zu **Netzwerk > VPCs**.
2. Klicken Sie auf **VPC erstellen**.
3. Geben Sie einen Namen und eine Beschreibung für Ihre VPC ein.
4. Sobald die VPC erstellt ist, klicken Sie darauf und wählen Sie **Subnetz erstellen**.
5. Definieren Sie den Subnetznamen, die Netzwerkadresse (CIDR) und die Gateway-IP.
6. (Optional) Konfigurieren Sie spezifische DHCP-Zuweisungspools oder benutzerdefinierte DNS-Nameserver für das Subnetz.

## Nächste Schritte

Sobald Ihr isoliertes Netzwerkfundament eingerichtet ist, müssen Sie wahrscheinlich Folgendes tun:
*   Einen **Router** erstellen, um den Datenverkehr zwischen Subnetzen oder ins Internet fließen zu lassen.
*   Eine **Floating IP** anhängen, um eine Instanz öffentlich erreichbar zu machen.