# ISMS Control Dashboard

Ein schlankes, offline-fähiges Dashboard zur Verfolgung aller **93 ISO 27001:2022 Annex A Controls** mit direktem Mapping auf die **NIS2-Richtlinie Art. 21**. Keine Installation, kein Server, keine Internetverbindung erforderlich – einfach die HTML-Datei herunterladen und im Browser öffnen.

## Screenshot

![Dashboard Screenshot](assets/Dashboard-Screenshot.jpg)

## Verwendung

```
Datei herunterladen → Doppelklick auf dashboard.html → fertig
```

Funktioniert vollständig offline auf Firmen-PCs ohne Adminrechte. Alle Daten bleiben lokal im Browser (localStorage).

## Features

- **93 Controls** aus ISO 27001:2022 Annex A, vollständig auf Deutsch
- **NIS2 Art. 21 Mapping** – 10 Artikel mit RAG-Status und Fortschrittsanzeige
- **Status-Tracking** per Klick: Nicht umgesetzt → Teilweise → Umgesetzt
- **Kategorie-Filter**: Organisatorisch, Personell, Physisch, Technisch
- **Freitextsuche** nach Control-ID oder Name
- **Expand-Zeilen** mit 6 Feldern pro Control: Zweck/Ziel, Umsetzungsmaßnahmen, Verantwortlicher, Datum, Nachweise, Kommentar
- **CSV-Export** (Excel-kompatibel, mit BOM) und **CSV-Import** mit automatischer Spaltenerkennung
- **Excel-Sync** – `ISMS_Controls_Tracker.xlsx` und Dashboard teilen dasselbe CSV-Format
- **Dark Mode** automatisch per Systempräferenz
- **Kein Server, kein Node, kein Python** – reines HTML + CSS + Vanilla JS
- **Offline-fähig** – funktioniert ohne Internetverbindung

## Arbeitsablauf

Es gibt zwei parallele Tools, die über CSV verbunden sind:

| Tool | Zweck |
|---|---|
| `ISMS_Controls_Tracker.xlsx` | Detailliertes Arbeitsblatt – hier trägst du alles ein |
| `dashboard.html` | Visuelles Dashboard – Übersicht, Ampelstatus, NIS2-Mapping |

### Empfohlener Ablauf: Excel → Dashboard

```
1. ISMS_Controls_Tracker.xlsx öffnen
2. Felder ausfüllen:
     Status              → Nicht umgesetzt / Teilweise / Umgesetzt
     Zweck / Ziel        → Was soll dieser Control erreichen?
     Umsetzungsmaßnahmen → Wie wurde er implementiert?
     Verantwortlicher    → Name oder Rolle
     Datum Umsetzung     → TT.MM.JJJJ
     Nachweise / Referenz → Dokument, Ticket, Link
     Kommentar           → Weitere Anmerkungen

3. Excel speichern als CSV:
     Datei → Speichern unter → CSV UTF-8 (mit BOM)
     (macOS: Datei → Exportieren → CSV UTF-8)

4. dashboard.html im Browser öffnen (Doppelklick)

5. Im Dashboard: Schaltfläche "↑ CSV importieren" → CSV-Datei auswählen
   → Alle Daten sind sofort im Dashboard sichtbar
```

> **Hinweis:** Das Dashboard erkennt Excels deutsche Spaltennamen automatisch.
> Komma- und Semikolon-Trennzeichen (deutsches Excel) werden beide unterstützt.

### Umgekehrt: Dashboard → Excel

```
1. Im Dashboard Daten eingeben (Status per Klick, Details per ▼-Button)
2. Schaltfläche "↓ CSV exportieren"
3. CSV in Excel öffnen → Daten in ISMS_Controls_Tracker.xlsx einfügen
```

### Nur Dashboard (ohne Excel)

```
dashboard.html öffnen → Status per Klick setzen → Details über ▼-Button eingeben
Alle Änderungen werden automatisch im Browser gespeichert (localStorage).
```

## CSV-Export / Import

### Spalten

| Spalte (CSV) | Excel-Spalte | Beschreibung |
|---|---|---|
| `control_id` | Control ID | Schlüssel (z. B. `5.1`) |
| `control_name` | Control Name | Name des Controls |
| `kategorie` | Kategorie | Organisatorisch / Personell / Physisch / Technisch |
| `nis2_artikel` | NIS2 Artikel | Zugeordnete Art.-21-Absätze |
| `status` | Status | `Umgesetzt` / `Teilweise` / `Nicht umgesetzt` |
| `zweck` | Zweck / Ziel | Ziel des Controls |
| `massnahmen` | Umsetzungsmaßnahmen | Konkrete Umsetzung |
| `verantwortlich` | Verantwortlicher | Name / Rolle |
| `datum` | Datum Umsetzung | Datum der Umsetzung |
| `nachweise` | Nachweise / Referenz | Dokumente, Tickets, Links |
| `notizen` | Kommentar | Weitere Anmerkungen |

Die CSV-Datei enthält ein UTF-8 BOM für reibungslose Excel-Kompatibilität.

## NIS2 Art. 21 Mapping

| Artikel | Bezeichnung | Controls |
|---|---|---|
| Art. 21(2)(a) | Risikoanalyse | 5.1, 5.2, 5.3, 6.1, 8.2, 8.3 |
| Art. 21(2)(b) | Incident Handling | 5.24, 5.25, 5.26, 5.27, 5.28 |
| Art. 21(2)(c) | BCM & Disaster Recovery | 5.29, 5.30, 8.13, 8.14 |
| Art. 21(2)(d) | Lieferkettensicherheit | 5.19, 5.20, 5.21, 5.22, 5.23 |
| Art. 21(2)(e) | Sichere Entwicklung | 8.25, 8.26, 8.27, 8.28, 8.29, 8.30, 8.31, 8.32 |
| Art. 21(2)(f) | Wirksamkeitsbewertung | 5.35, 5.36, 8.8 |
| Art. 21(2)(g) | Schulung & Cyber-Hygiene | 6.3, 6.8 |
| Art. 21(2)(h) | Kryptographie | 8.24 |
| Art. 21(2)(i) | HR, Zugang & Assets | 5.9, 5.10, 5.11, 5.15, 5.16, 5.17, 5.18, 6.1, 6.2, 6.5, 8.2, 8.5 |
| Art. 21(2)(j) | MFA & Kommunikation | 5.14, 8.5, 8.20 |

## Lizenz

MIT License – frei verwendbar, auch kommerziell.
