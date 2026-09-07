# 06 – Fileserver FS01

## Ziel

Als nächster Bestandteil der Unternehmensumgebung wurde ein zweiter
Windows-Server für die spätere Bereitstellung von Datei- und
Freigabediensten eingerichtet.

Der Server erhielt den Namen:

`FS01`

---

## Virtuelle Maschine

Für FS01 wurde eine weitere virtuelle Maschine mit VMware Workstation erstellt.

### Konfiguration

| Einstellung | Wert |
|---|---|
| Betriebssystem | Windows Server 2022 |
| Servername | FS01 |
| Arbeitsspeicher | 4 GB |
| Prozessoren | 2 |
| Systemlaufwerk | 60 GB |
| Netzwerk | VMware NAT |

Nach der Installation wurde der Computername auf `FS01` geändert.

---

## Statische Netzwerkkonfiguration

Da FS01 später als zentraler Fileserver eingesetzt wird, wurde ebenfalls eine
statische IPv4-Adresse vergeben.

| Netzwerkeinstellung | Wert |
|---|---|
| IPv4-Adresse | 192.168.10.20 |
| Subnetzmaske | 255.255.255.0 (/24) |
| Standardgateway | 192.168.10.1 |
| DNS-Server | 192.168.10.10 |

Als DNS-Server verwendet FS01 den Domain Controller `SRV-DC01`.

Dadurch kann FS01 die interne Domäne `schmitz.local` und die benötigten
Active-Directory-Dienste auflösen.

---

## Verbindung zum Domain Controller

Vor dem Domänenbeitritt wurde die Verbindung zwischen FS01 und SRV-DC01
überprüft.

Beispielsweise wurde die IPv4-Adresse des Domain Controllers getestet:

`ping 192.168.10.10`

Die Verbindung war erfolgreich.

Zusätzlich konnte der Domain Controller über seinen Hostnamen erreicht werden:

`SRV-DC01`

---

## Domänenbeitritt

FS01 wurde anschließend der bestehenden Active-Directory-Domäne

`schmitz.local`

hinzugefügt.

Für den Beitritt wurden Domänenadministrator-Anmeldedaten verwendet.

Nach erfolgreicher Authentifizierung bestätigte Windows den Beitritt mit:

`Willkommen in der Domäne schmitz.local`

Anschließend wurde der Server neu gestartet.

---

## Warum wird FS01 der Domäne hinzugefügt?

Durch die Mitgliedschaft in der Domäne kann FS01 zentrale
Active-Directory-Funktionen verwenden.

Dazu gehören unter anderem:

- Domänenbenutzer
- Sicherheitsgruppen
- zentrale Authentifizierung
- Gruppenrichtlinien
- zentrale Berechtigungsverwaltung

Dadurch können später beispielsweise Datei- und Ordnerberechtigungen anhand
von Active-Directory-Gruppen vergeben werden.

---

## Geplante Aufgabe von FS01

FS01 soll im weiteren Verlauf als zentraler Fileserver verwendet werden.

Geplant sind unter anderem:

- Abteilungsfreigaben
- NTFS-Berechtigungen
- SMB-Freigaben
- Berechtigungen über Sicherheitsgruppen
- Umsetzung eines AGDLP-Berechtigungskonzepts

---

## Ergebnis

FS01 wurde erfolgreich installiert, mit einer statischen IPv4-Adresse
konfiguriert und der Domäne `schmitz.local` hinzugefügt.

Damit ist der Server für die weitere Einrichtung als Fileserver vorbereitet.
