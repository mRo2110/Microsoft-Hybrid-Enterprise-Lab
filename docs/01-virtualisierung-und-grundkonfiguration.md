# 01 – Virtualisierung und Grundkonfiguration

## Ziel

Als Grundlage für die Unternehmensumgebung wurde zunächst ein Windows Server
als virtuelle Maschine bereitgestellt.

Die Virtualisierung ermöglicht es, mehrere Server und Clients innerhalb einer
abgeschotteten Laborumgebung zu betreiben, ohne dafür separate physische
Hardware zu benötigen.

## Virtuelle Maschine SRV-DC01

Die virtuelle Maschine wurde mit VMware Workstation erstellt.

### Konfiguration

| Einstellung | Wert |
|---|---|
| Hypervisor | VMware Workstation |
| Betriebssystem | Windows Server 2022 |
| Servername | SRV-DC01 |
| Arbeitsspeicher | 4 GB |
| Netzwerk | VMware NAT |

Nach der Installation von Windows Server 2022 wurde der Server für seine
spätere Aufgabe als Domain Controller vorbereitet.

---

## Servername

Der Server erhielt den eindeutigen Computernamen:

`SRV-DC01`

Die Namenskonvention beschreibt gleichzeitig die Funktion des Systems:

- `SRV` = Server
- `DC` = Domain Controller
- `01` = erster Server dieser Rolle

Durch eine einheitliche Namenskonvention können Systeme innerhalb einer
größeren Infrastruktur leichter identifiziert und administriert werden.

---

## Statische IPv4-Konfiguration

Für SRV-DC01 wurde eine statische IPv4-Adresse konfiguriert.

| Netzwerkeinstellung | Wert |
|---|---|
| IPv4-Adresse | 192.168.10.10 |
| Subnetzmaske | 255.255.255.0 (/24) |
| Standardgateway | 192.168.10.1 |
| DNS-Server | 192.168.10.10 |

### Warum eine statische IP-Adresse?

Ein Domain Controller stellt zentrale Netzwerkdienste bereit und muss daher
dauerhaft unter derselben IP-Adresse erreichbar sein.

Eine dynamische Adressierung über DHCP wäre für einen solchen Server
ungeeignet, da sich seine IP-Adresse ändern könnte.

Die Adresse `192.168.10.10` wurde deshalb fest für SRV-DC01 reserviert.

---

## Ergebnis

Nach Abschluss der Grundkonfiguration stand SRV-DC01 mit einer festen
Netzwerkkonfiguration zur Verfügung.

Damit war die Grundlage für die Installation von Active Directory Domain
Services, DNS und DHCP geschaffen.
