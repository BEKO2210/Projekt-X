# MONITORING.md — Logging, Audit, Incidents, Systemaufsicht (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 25.

---

## 1. Grundsatz

Systemaufsicht dient Nutzerschutz und Nachvollziehbarkeit, nicht Überwachung. Logs werden datenschutzsparsam erhoben, nur Metadaten, keine unnötigen Inhalte.

---

## 2. Logging

### 2.1 Was wird geloggt
- Systemereignisse (Start, Stop, Fehler, Release-Schritte)
- Gate-Ergebnisse (bestanden / nicht bestanden)
- Agentenläufe (Metadaten, nicht Volltext, nicht sensibler Inhalt)
- Export- und Löschvorgänge
- Zugriffsverweigerungen

### 2.2 Was **nicht** geloggt wird
- Sensible Nutzerdaten im Klartext
- Vollständige Prompt-Eingaben, wenn sie personenbezogen sind (nur mit Zustimmung und Zweck)
- Keine Tracking-IDs Dritter

### 2.3 Aufbewahrung
- Kurz gehalten, definiert in späteren Runs.
- Rotierend, automatisch löschbar.
- Export für Nutzer-Auskunft möglich (Phase 7).

---

## 3. Audit-Log

Spezielles Log für nutzerrelevante Ereignisse:

- Export eines Dokuments / Projekts
- Löschung eines Dokuments / Projekts
- Einwilligungen / Widerrufe
- Datenschutzmodus-Wechsel

Audit-Einträge sind für Nutzer einsehbar.

---

## 4. Incidents

- Jeder Sicherheits-/Datenschutzvorfall wird dokumentiert in `incidents/`.
- Pflichtfelder: Zeit, Auslöser, betroffene Daten/Personen, Sofortmaßnahme, Ursache, Lernpunkte.
- Post-Mortem wird geschrieben, ggf. fließen Lernpunkte in `CLAUDE.md` ein.

---

## 5. Eskalation

- Incident mit Datenschutzwirkung → Sofort: Funktion deaktivieren.
- Kommunikation an betroffene Nutzer nach rechtlicher/ethischer Prüfung.
- Kein „laufen lassen".

---

## 6. Monitoring (später)

Geplant in Phase 8+:

- Verfügbarkeit
- Fehlerraten
- Agenten-Fehlerhäufigkeit
- Gate-Durchflussrate
- Exportvolumen (Metadaten)
- Löschvolumen

Kein Business-Analytics-Tracking des Nutzerverhaltens ohne Einwilligung.

---

## 7. Offene Punkte

- Logging-Framework-Wahl (ADR).
- Log-Anonymisierung (Strategie, Phase 8).
- Alerting-Regeln (Phase 8+).
- Zentralisiertes Monitoring-Backend.
- Regelmäßige Audit-Reviews.

---

## 8. Stand Run 1

- **Kein** Logging aktiv.
- **Kein** Audit-Log implementiert.
- **Keine** Incidents vorhanden.
- Dieser Text ist Konzept und Leitplanke.
