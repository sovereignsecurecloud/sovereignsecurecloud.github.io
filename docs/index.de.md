# Willkommen bei der SovereignSecure Cloud &trade; Dokumentation

Willkommen bei der SovereignSecure Cloud, Ihrer vertrauenswürdigen Plattform für sichere, konforme und hochleistungsfähige Cloud-Dienste. Aufgebaut auf einem OpenStack-Fundament und erweitert durch ManageIQ für umfassendes Cloud-Management, befähigen wir Organisationen, die volle Kontrolle über ihre Daten und Abläufe in einer souveränen digitalen Umgebung zu behalten.

## Unser Engagement für Souveränität

Die SovereignSecure Cloud wurde entwickelt, um die strengen Anforderungen der Datensouveränität zu erfüllen und sicherzustellen, dass Ihre Daten innerhalb bestimmter geografischer und rechtlicher Zuständigkeiten bleiben. Wir erreichen dies durch:

*   **Datenresidenz:** Ihre Daten werden ausschließlich in festgelegten Regionen gespeichert und verarbeitet, unter Einhaltung lokaler Vorschriften.
*   **Betriebliche Autonomie:** Unsere Infrastruktur und unser Betrieb werden von lokalen Teams verwaltet, was Transparenz und Kontrolle gewährleistet.
*   **Open-Source-Fundament:** Die Nutzung von OpenStack und anderen Open-Source-Technologien minimiert den Vendor-Lock-in und bietet einen transparenten, auditierbaren Stack.
*   **Robuste Sicherheit & Compliance:** Wir implementieren fortschrittliche Sicherheitsmaßnahmen und unterhalten Zertifizierungen, um Ihre sensiblen Workloads zu schützen.

## Erkunden Sie die Dokumentation

Verwenden Sie die Navigation auf der linken Seite, um unsere umfassenden Leitfäden zu erkunden:

```mermaid
graph TD
    subgraph SovereignCloud[<b>SovereignSecure Cloud &trade;</b>]
        direction TB
        
        subgraph DataControl[<b>Datenkontrolle & Souveränität</b>]
            DC[Datenresidenzgesetze]
            DP[Datenschutz]
            DG[Data Governance]
        end
        
        subgraph Security[<b>Sicherheit & Compliance</b>]
            IS[Infrastruktursicherheit]
            EN[Verschlüsselung]
            CS[Zertifizierungen & Standards]
        end
        
        subgraph Deployment[<b>Bereitstellungsmodelle</b>]
            PB[Öffentliche Sovereign Cloud]
            PR[Private Sovereign Cloud]
            HY[Hybride Sovereign Cloud]
        end
        
        subgraph Providers[<b>Kernkomponenten</b>]
            OS[Lokaler Betrieb]
            LC[Cloud-Anbieter]
            OP[Open-Source-Technologien]
        end
        
        DataControl -->|Gewährleistet| Security
        Security -->|Unterstützt| Deployment
        Deployment -->|Nutzt| Providers
        Providers -->|Erhält| DataControl
    end
    
    Government[Staatliche Vorschriften] -.-> DataControl
    Enterprise[Unternehmensanforderungen] -.-> Security
    Users[Endbenutzer-Datenschutz] -.-> Deployment
```

## Hauptbereiche

<div class="grid cards" markdown>

-   :material-rocket-launch:{ .lg .middle } __Erste Schritte__

    ---

    Eine Schritt-für-Schritt-Anleitung für neue Benutzer, um sich schnell einzuarbeiten und erste Ressourcen bereitzustellen.

    [:octicons-arrow-right-24: Schnellstart](quickstart/index.md)

-   :material-monitor-dashboard:{ .lg .middle } __Cloud-Management (CMP)__

    ---

    Erfahren Sie, wie Sie das ManageIQ-Portal für Self-Service-Bereitstellungen, Kataloge und Berichte verwenden.

    [:octicons-arrow-right-24: CMP Übersicht](cmp/index.md)

-   :material-server-network:{ .lg .middle } __Kerndienste__

    ---

    Tauchen Sie tief in unsere Compute-, Storage- und Netzwerkangebote ein, einschließlich GPU-Instanzen.

    [:octicons-arrow-right-24: Dienste erkunden](compute/index.md)

-   :material-api:{ .lg .middle } __API & Automatisierung__

    ---

    Integrieren Sie unsere Plattform mithilfe nativer OpenStack-APIs und IaC-Tools wie Terraform.

    [:octicons-arrow-right-24: API Übersicht](api/index.md)

</div>