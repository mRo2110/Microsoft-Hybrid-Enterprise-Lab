# Microsoft Hybrid Enterprise Lab

Praktisches Homelab-Projekt zum Aufbau und zur Dokumentation einer
Windows-basierten Unternehmens-IT-Infrastruktur.

## Projektziel

Ziel des Projekts ist der schrittweise Aufbau einer kleinen Unternehmensumgebung
mit Windows Server, Active Directory, DNS, DHCP, Fileservern, Clients und später
Microsoft Cloud-Diensten wie Entra ID und Intune.

Das Projekt dient dazu, praktische Kenntnisse in Administration,
Netzwerkdiensten und Microsoft-Infrastrukturen aufzubauen und nachvollziehbar
zu dokumentieren.

## Aktueller Stand

Bisher wurden unter anderem folgende Komponenten umgesetzt:

- Windows Server 2022 als virtuelle Maschine eingerichtet
- SRV-DC01 grundkonfiguriert
- statische IPv4-Adresse vergeben
- Active Directory Domain Services installiert
- Domäne `schmitz.local` erstellt
- SRV-DC01 zum Domain Controller heraufgestuft
- DNS eingerichtet
- DHCP eingerichtet
- OU-Struktur erstellt
- Benutzer und Sicherheitsgruppen angelegt
- zweiter Windows Server `FS01` eingerichtet
- FS01 mit statischer IP konfiguriert
- FS01 erfolgreich der Domäne hinzugefügt

## Infrastruktur

| System | Funktion | IPv4 |
|---|---|---|
| SRV-DC01 | Domain Controller, DNS, DHCP | 192.168.10.10 |
| FS01 | zukünftiger Fileserver | 192.168.10.20 |
| Clients | Arbeitsplatzrechner | DHCP |

## Dokumentation

Die einzelnen Schritte sind ausführlich im Ordner `docs` dokumentiert.

- [01 – Virtualisierung und Grundkonfiguration](docs/01-virtualisierung-und-grundkonfiguration.md)
- [02 – Active Directory und Domain Controller](docs/02-active-directory-domain-controller.md)
- [03 – DNS-Konfiguration](docs/03-dns.md)

## Geplante Erweiterungen

- DHCP-Dokumentation
- Active-Directory-Struktur
- Fileserver und Berechtigungen
- Windows-Client
- Gruppenrichtlinien
- Microsoft Entra ID
- Microsoft Intune
- Hybrid-Umgebung

## Technologien

- VMware Workstation
- Windows Server 2022
- Active Directory Domain Services
- DNS
- DHCP
- Windows Client
- später: Microsoft Entra ID und Microsoft Intune
