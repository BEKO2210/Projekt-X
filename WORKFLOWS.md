# WORKFLOWS.md — MVP-Workflows (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 13 und Teil 35.

---

## 1. Grundidee

Workflows sind **deterministische, strukturierte Abläufe** — keine freien Chats. Jeder Workflow hat Einstieg, Schritte, Ausgabe, Status, Pausierbarkeit und Abbruchkriterien.

---

## 2. MVP-Workflows (geplant)

### 2.1 Startorientierung
- Ziel klären, Ausgangslage erfassen, Richtung skizzieren.
- Ergebnis: Projektentwurf mit ersten Risiken und Aufgaben.

### 2.2 Idee validieren
- Zielgruppe, Problem, Angebot, erste Annahmen.
- Ergebnis: Annahmenliste mit Risikostatus.

### 2.3 Mini-Businessplan
- Angebot, Zielgruppe, Nutzenversprechen, grober Weg.
- Ergebnis: Dokument „Mini-Businessplan" mit Abschnittsstatus.

### 2.4 MVP planen
- Kernfunktion, was weglassen, erstes Nutzen-Experiment.
- Ergebnis: Dokument „MVP-Plan".

### 2.5 Datenschutz-Basischeck
- Datenarten, externe Verarbeitung, Sensibilität.
- Ergebnis: Dokument „Datenschutz-Basischeck".

### 2.6 Finanzplan light
- Kosten, Annahmen, Szenarien, Risikoampel.
- Ergebnis: Dokument „Finanzplan light".

### 2.7 Erste Kundenansprache als Entwurf
- Zielgruppe, Gesprächsleitfaden, E-Mail-Entwurf (ohne Versand).
- Ergebnis: Entwurf mit Versandverbot-Hinweis.

---

## 3. Workflow-Eigenschaften (Pflicht)

Jeder Workflow hat:

- **Name, Version, Scope**
- **Einstiegsvoraussetzungen** (z. B. bestehendes Projekt)
- **Schritte** mit Pflicht-/Optionalmarkierung
- **Zwischenstände** (Pausierbarkeit)
- **Abbruchkriterien**
- **Ausgabeobjekte** (Aufgaben, Risiken, Dokumente)
- **Datenschutzwirkung** dokumentiert
- **Fachprüfungsbedarf** dokumentiert
- **Testplan**

---

## 4. Pausieren und Fortsetzen

Nutzer können jederzeit:

- pausieren (Zwischenstand wird gespeichert)
- fortsetzen (Workflow nimmt Kontext wieder auf)
- abbrechen (mit Bestätigung, Zwischenstand bleibt oder wird gelöscht, je nach Datenschutzmodus)

---

## 5. Abbruchkriterien

Workflows brechen ab, wenn:

- Nutzer abbricht.
- Datenschutzrisiko erkannt wurde und Nutzer nicht bestätigt.
- Fachprüfungsbedarf besteht, der nicht durch Nutzer-Handlung aufgelöst werden kann.
- Agent wiederholt außerhalb Scope läuft.

Abbruch wird in Audit-Log vermerkt.

---

## 6. Verbotene Workflow-Ergebnisse (MVP)

- Automatischer E-Mail-Versand
- Automatische Antragseinreichung
- Automatische Zahlungen
- Automatische Verträge
- Automatische Social-Media-Aktionen

---

## 7. Offene Punkte

- Konkrete Schrittdefinition je Workflow (Runs 3+).
- UI-Darstellung der Workflow-Schritte (Phase 2/5).
- Persistenz der Workflow-Zwischenstände (Phase 1).
- Agent-Zuordnung je Schritt (Phase 3).

---

## 8. Stand Run 1

- **Keine** Workflows implementiert.
- Dieser Text dokumentiert nur die geplanten Umrisse.
