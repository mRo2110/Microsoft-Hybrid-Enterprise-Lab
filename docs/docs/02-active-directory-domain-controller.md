# 02 – Active Directory und Domain Controller

## Ziel

Nach der Grundkonfiguration von SRV-DC01 sollte der Server als zentraler
Domain Controller der Laborumgebung eingesetzt werden.

Dafür wurden die Active Directory Domain Services installiert und eine neue
Active-Directory-Gesamtstruktur erstellt.

---

## Installation von Active Directory Domain Services

Auf SRV-DC01 wurde die Serverrolle

`Active Directory Domain Services (AD DS)`

installiert.

Active Directory übernimmt in der Umgebung die zentrale Verwaltung von:

- Benutzern
- Computern
- Sicherheitsgruppen
- Organisationseinheiten
- Gruppenrichtlinien

Dadurch können Benutzerkonten und Berechtigungen zentral administriert werden.

---

## Neue Gesamtstruktur

Da noch keine bestehende Active-Directory-Umgebung vorhanden war, wurde eine
neue Gesamtstruktur erstellt.

Als interne Domäne wurde verwendet:

`schmitz.local`

SRV-DC01 wurde anschließend zum ersten Domain Controller dieser Domäne
heraufgestuft.

---

## Domain Controller

Nach der Heraufstufung übernimmt SRV-DC01 die zentrale Authentifizierung der
Domänenbenutzer.

Der Server stellt unter anderem folgende Dienste bereit:

- Active Directory Domain Services
- DNS
- zentrale Benutzer- und Computerverwaltung
- Grundlage für Gruppenrichtlinien

---

## NTDS und SYSVOL

Die Active-Directory-Daten werden auf dem Domain Controller in verschiedenen
Bereichen gespeichert.

### NTDS

Die Active-Directory-Datenbank enthält unter anderem:

- Benutzerkonten
- Computerobjekte
- Gruppen
- Organisationseinheiten
- Kennwortinformationen
- weitere Verzeichnisobjekte

### SYSVOL

SYSVOL enthält Dateien, die innerhalb der Domäne verteilt werden müssen.

Dazu gehören insbesondere:

- Gruppenrichtlinien
- Anmeldeskripte
- weitere domänenweit benötigte Dateien

---

## Ergebnis

Nach der Heraufstufung war SRV-DC01 der erste Domain Controller der Domäne:

`schmitz.local`

Damit stand die zentrale Active-Directory-Infrastruktur für die weiteren
Server und Clients der Laborumgebung zur Verfügung.
