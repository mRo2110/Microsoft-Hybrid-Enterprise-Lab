# 05 – Active-Directory-Struktur

## Ziel

Nach der Einrichtung der Domäne `schmitz.local` wurde eine strukturierte
Active-Directory-Organisation aufgebaut.

Ziel war es, Benutzer, Computer, Server und Gruppen übersichtlich zu trennen
und eine Grundlage für spätere Gruppenrichtlinien und Berechtigungen zu schaffen.

---

## Organisationseinheiten

Folgende Organisationseinheiten wurden erstellt:

- Benutzer
  - IT
  - Vertrieb
  - Buchhaltung
  - Personal
  - Geschäftsführung
- Computer
- Server
- Gruppen
- Service Accounts
- Test

Die Struktur orientiert sich an einer typischen Unternehmensorganisation.

---

## Warum Organisationseinheiten?

Organisationseinheiten dienen dazu, Active-Directory-Objekte logisch zu
strukturieren.

Sie können später unter anderem verwendet werden für:

- Gruppenrichtlinien
- administrative Delegation
- übersichtliche Verwaltung
- Trennung nach Abteilungen oder Gerätetypen

Eine OU vergibt jedoch nicht automatisch Zugriffsrechte auf Dateien oder
andere Ressourcen.

---

## Benutzerkonto

Für Tests wurde ein Domänenbenutzer erstellt:

`mirko.schmitz`

Das Benutzerkonto wurde in der OU `IT` abgelegt.

Anmeldevarianten:

`mirko.schmitz@schmitz.local`

oder

`SCHMITZ\mirko.schmitz`

---

## Sicherheitsgruppen

Für die einzelnen Abteilungen wurden globale Sicherheitsgruppen erstellt.

Beispiele:

- `SG_IT`
- `SG_Vertrieb`
- `SG_Buchhaltung`
- `SG_Personal`
- `SG_Geschaeftsfuehrung`

Der Benutzer `mirko.schmitz` wurde der Gruppe `SG_IT` hinzugefügt.

---

## OU und Sicherheitsgruppe

Organisationseinheiten und Sicherheitsgruppen erfüllen unterschiedliche Aufgaben.

### Organisationseinheit

Eine OU dient hauptsächlich der Strukturierung und Verwaltung von Objekten.

Beispiel:

`Benutzer → IT → mirko.schmitz`

### Sicherheitsgruppe

Eine Sicherheitsgruppe wird für Berechtigungen verwendet.

Beispiel:

`mirko.schmitz → SG_IT`

Später kann `SG_IT` beispielsweise Zugriff auf eine IT-Dateifreigabe erhalten.

---

## Berechtigungskonzept

Für die spätere Dateiserver-Konfiguration ist ein Gruppenmodell nach dem
AGDLP-Prinzip vorgesehen.

AGDLP steht für:

- Accounts
- Global Groups
- Domain Local Groups
- Permissions

Ein mögliches Beispiel:

`Benutzer → SG_IT → DL_IT_RW → Ordnerberechtigung`

Dadurch werden Berechtigungen nicht direkt einzelnen Benutzern zugewiesen,
sondern über Gruppen verwaltet.

---

## Ergebnis

Die grundlegende Active-Directory-Struktur wurde erfolgreich aufgebaut.

Damit ist die Umgebung vorbereitet für:

- Gruppenrichtlinien
- Dateiserver-Berechtigungen
- weitere Benutzer
- Client-Systeme
- spätere Erweiterungen der Domänenstruktur
