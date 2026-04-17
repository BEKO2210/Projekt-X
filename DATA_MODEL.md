# DATA_MODEL.md — Objekte, Status, Beziehungen (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 17.

---

## 1. Zweck

Dieses Dokument beschreibt die geplanten Kernobjekte des Systems und ihre Statusfelder. Es ist kein Schema für eine konkrete Datenbank, sondern ein konzeptionelles Modell.

---

## 2. Kernobjekte (geplant)

### 2.1 Nutzerprofil (`user_profile`)
- Identität (minimiert)
- Datenschutzmodus (`standard` | `streng` | `temporaer_optional`)
- Einwilligungen
- Reifegrad
- Zeitstempel

### 2.2 Projektakte (`project`)
- Projektname
- Projektziel
- Ausgangslage
- Projektstatus
- Reifegrad light
- Geschäftsidee
- Zielgruppe
- Angebot
- verknüpfte Risiken, Aufgaben, Dokumente, Entscheidungen
- Datenschutzstatus, Sicherheitsstatus, Quellenstatus
- letzte Aktualisierung

### 2.3 Aufgabe (`task`)
- Titel, Beschreibung
- Status (`offen` | `in_arbeit` | `blockiert` | `erledigt` | `verworfen`)
- Priorität
- Blockergrund
- Fälligkeit (optional)
- Verantwortung (Nutzer oder Agent-Vorschlag)
- Quellenbedarf, Fachprüfungsbedarf

### 2.4 Dokument (`document`)
- Typ (Mini-Businessplan, Finanzplan light, MVP-Plan, Datenschutz-Basischeck, Fördercheck light, Angebotsentwurf, E-Mail-Entwurf ohne Versand)
- Entwurfsstatus
- Abschnittsstatus je Abschnitt
- Quellenstatus je Aussage
- Fachprüfungsstatus
- Versionierung basic
- Exportwarnungen
- Sensibilität

### 2.5 Quelle (`source`)
- Titel, URL oder Referenz
- Quellenstatus (`quelle_geprueft` | `quelle_veraltet` | `quelle_unklar` | `quelle_fehlt`)
- Aktualitätsmarker
- Lizenzstatus
- Fachgebiet

### 2.6 Risiko (`risk`)
- Beschreibung
- Kategorie (rechtlich, finanziell, datenschutzbezogen, operational, sonstige)
- Ampel (gruen/gelb/rot)
- empfohlene Maßnahme (als Vorschlag, nicht als Beratung)

### 2.7 Entscheidung (`decision`)
- Frage
- Optionen
- Abwägung
- Datum
- Verantwortlich
- Reversibilität

### 2.8 Gate-Ergebnis (`gate_result`)
- Gate-Typ (Datenschutz, Sicherheit, Quellen, Fachprüfung, Agenten, Export, kritische Aktion, Release)
- Status (`bestanden` | `nicht_bestanden` | `ausstehend`)
- Prüfer (Mensch oder System)
- Begründung

### 2.9 Audit-Log (`audit_log`)
- Ereignistyp (Export, Löschung, Agentenlauf, Gate-Ergebnis)
- Zeit, Akteur (Nutzer oder Agentname)
- betroffene Objekte
- Datenschutzrelevanz

### 2.10 Agentenlauf (`agent_run`)
- Agent
- Kontextpaket (minimiert)
- Aufgabe
- Ergebnis
- Fehler/Warnungen
- Verweis auf Rollenvertrag-Version
- Prompt-Version

---

## 3. Statusfelder — verbindliche Skalen

### 3.1 Entwurfsstatus (Dokumente)
`leer` → `entwurf` → `ueberarbeitung` → `freigegeben_intern` → `exportiert`

### 3.2 Quellenstatus
`quelle_fehlt` | `quelle_unklar` | `quelle_veraltet` | `quelle_geprueft`

### 3.3 Fachprüfungsstatus
`nicht_erforderlich` | `erforderlich_offen` | `erforderlich_in_arbeit` | `bestaetigt` | `abgelehnt`

### 3.4 Datenschutzmodus
`standard` | `streng` | `temporaer_optional`

### 3.5 Sensibilitätsstufen
`gering` | `mittel` | `hoch` | `sehr_hoch`

### 3.6 Sicherheitsstatus (pro Funktion/Modul)
`geprueft` | `teilweise_geprueft` | `ungeprueft` | `blockiert`

---

## 4. Beziehungen (Überblick)

- `user_profile` 1..n → `project`
- `project` 1..n → `task`, `document`, `risk`, `decision`
- `document` 1..n → `source`
- jedes veränderbare Objekt 1..n → `audit_log`
- `gate_result` referenziert jede Funktion oder jeden Release-Übergang

---

## 5. Datenminimierung

- Nur Daten speichern, die für die Funktion notwendig sind.
- Sensible Daten kennzeichnen und, wenn möglich, lokal belassen.
- Nutzer kann jederzeit Projekte und Dokumente löschen.
- Export erzeugt Audit-Eintrag.

---

## 6. Offene Punkte

- Konkrete Feldtypen (String-Längen, Enums, Normalisierung).
- Wahl der Datenbank (wird in ADR entschieden).
- Verschlüsselung at-rest (in `SECURITY.md` zu detaillieren).
- Schema-Versionierung.
- Migrations-Strategie.

Diese Punkte werden in späteren Runs vertieft, nicht in Run 1.
