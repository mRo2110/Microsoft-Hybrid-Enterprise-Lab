# 03 – DNS-Konfiguration

## Ziel

Für die Active-Directory-Domäne `schmitz.local` wird SRV-DC01 als interner
DNS-Server verwendet.

DNS ist ein zentraler Bestandteil von Active Directory, da Server und Clients
über DNS unter anderem Domain Controller und andere Dienste innerhalb der
Domäne finden.

---

## DNS-Server

Die DNS-Serverrolle wurde auf dem Domain Controller `SRV-DC01` eingerichtet.

| Einstellung | Wert |
|---|---|
| DNS-Server | SRV-DC01 |
| IPv4-Adresse | 192.168.10.10 |
| DNS-Zone | schmitz.local |
| Zonentyp | Active-Directory-integriert |

---

## DNS-Zone

Für die Active-Directory-Domäne wurde die Forward-Lookup-Zone

`schmitz.local`

erstellt.

Innerhalb dieser Zone befinden sich die DNS-Einträge der Domäne.

Unter anderem wurde für den Domain Controller folgender Hosteintrag erstellt:

| Hostname | Typ | IPv4-Adresse |
|---|---|---|
| SRV-DC01 | A | 192.168.10.10 |

Dadurch kann der Server innerhalb des Netzwerks über seinen Namen angesprochen
werden, anstatt ausschließlich über seine IP-Adresse.

Beispiel:

`SRV-DC01.schmitz.local`

---

## DNS und Active Directory

Active Directory verwendet DNS nicht nur für die normale Namensauflösung.

Beim Einrichten des Domain Controllers wurden zusätzlich spezielle
DNS-Einträge für Active Directory erstellt.

Dazu gehören unter anderem Einträge für:

- Domain Controller
- LDAP
- Kerberos
- Domain Services

Diese Einträge ermöglichen es Domänenmitgliedern, die benötigten
Active-Directory-Dienste automatisch zu finden.

---

## DNS-Konfiguration der Server und Clients

Domänenmitglieder verwenden den internen DNS-Server:

`192.168.10.10`

Damit können interne Namen wie

`SRV-DC01.schmitz.local`

aufgelöst und Active-Directory-Dienste gefunden werden.

Ein öffentlicher DNS-Server wie beispielsweise `8.8.8.8` wird nicht direkt
als DNS-Server für Domänenmitglieder verwendet, da dieser die interne
Active-Directory-Domäne `schmitz.local` nicht kennt.

---

## Test der Namensauflösung

Die Erreichbarkeit des Domain Controllers wurde innerhalb der Laborumgebung
getestet.

Beispielsweise kann die Namensauflösung mit folgenden Befehlen überprüft werden:

`ping SRV-DC01`

`nslookup SRV-DC01.schmitz.local`

---

## Ergebnis

SRV-DC01 stellt die interne DNS-Namensauflösung für die Domäne
`schmitz.local` bereit.

Damit können Server und spätere Clients sowohl den Domain Controller als auch
die für Active Directory erforderlichen Dienste über DNS finden.
