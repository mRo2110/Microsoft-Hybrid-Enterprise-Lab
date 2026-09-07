# 04 – DHCP-Konfiguration

## Ziel

Für die spätere automatische Netzwerkkonfiguration von Clients wurde auf
`SRV-DC01` ein DHCP-Server eingerichtet.

DHCP verteilt automatisch wichtige Netzwerkeinstellungen wie:

- IPv4-Adresse
- Subnetzmaske
- Standardgateway
- DNS-Server
- DNS-Domäne

Dadurch müssen Client-Systeme nicht manuell konfiguriert werden.

---

## DHCP-Server

Die DHCP-Serverrolle wurde auf `SRV-DC01` installiert.

Anschließend wurde der DHCP-Server in Active Directory autorisiert.

### Warum ist die Autorisierung notwendig?

In einer Active-Directory-Domäne dürfen nur autorisierte DHCP-Server
IP-Adressen an Clients verteilen.

Dadurch wird verhindert, dass ein nicht freigegebener DHCP-Server
unbeabsichtigt oder absichtlich falsche Netzwerkeinstellungen verteilt.

---

## DHCP-Bereich

Für Client-Systeme wurde folgender Adressbereich eingerichtet:

| Einstellung | Wert |
|---|---|
| Bereichsname | Clients |
| Startadresse | 192.168.10.100 |
| Endadresse | 192.168.10.200 |
| Subnetzmaske | 255.255.255.0 |
| Präfix | /24 |
| Lease-Dauer | 8 Tage |

Der Bereich wurde bewusst erst ab `192.168.10.100` gestartet.

Dadurch bleibt der untere Adressbereich für Systeme mit statischen
IP-Adressen frei, zum Beispiel:

- `SRV-DC01` – 192.168.10.10
- `FS01` – 192.168.10.20

---

## DHCP-Optionen

Zusätzlich wurden folgende Optionen an die Clients verteilt:

| Option | Wert |
|---|---|
| Standardgateway | 192.168.10.1 |
| DNS-Server | 192.168.10.10 |
| DNS-Domäne | schmitz.local |

Dadurch erhalten Clients automatisch alle grundlegenden
Netzwerkeinstellungen für die Kommunikation innerhalb der Domäne.

---

## Lease-Dauer

Die Lease-Dauer wurde auf 8 Tage gesetzt.

Eine DHCP-Lease bestimmt, wie lange ein Client eine zugewiesene IP-Adresse
verwenden darf.

Der Client versucht bereits vor Ablauf der Lease, die Adresse beim
DHCP-Server zu verlängern.

Für normale Arbeitsplatzrechner ist eine längere Lease-Dauer sinnvoll,
da sich diese Geräte meist dauerhaft im gleichen Netzwerk befinden.

---

## Ergebnis

Mit dem eingerichteten DHCP-Bereich können zukünftige Client-Systeme ihre
Netzwerkkonfiguration automatisch erhalten.

Damit ist keine manuelle Vergabe von IP-Adresse, Gateway und DNS-Server
für jeden einzelnen Client notwendig.
