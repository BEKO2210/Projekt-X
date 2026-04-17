# ROADMAP.md — Phasen und Reihenfolge

> **Status:** Konzept. Phasen sind Leitplanken, keine Termine.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 33.

---

## Aktuelle Phase

**Phase 0 — Projektgrundlage und Architekturverfassung.**

Aktueller Fortschritt: Run 1 (Foundation) abgeschlossen. Siehe `reports/run-001-foundation.md`.

---

## Phasenübersicht

| Phase | Ziel | Status |
|---|---|---|
| **Phase 0** | Projektgrundlage und Architekturverfassung | **aktiv** |
| Phase 1 | Datenmodell, Umgebungen und Sicherheitsfundament | geplant |
| Phase 2 | Projektakte, Aufgaben und Basis-UI | geplant |
| Phase 3 | CEO-Orchestrator und Kernagenten | geplant |
| Phase 4 | Dokumente, Quellenstatus und Export | geplant |
| Phase 5 | Onboarding, Reifegrad und erste Workflows | geplant |
| Phase 6 | Finanzplan light und Risikoübersicht | geplant |
| Phase 7 | Datenschutzmodus, Datenlebenszyklus und Nutzerrechte | geplant |
| Phase 8 | Qualitätssicherung, Gates und Testsystem | geplant |
| Phase 9 | MVP-Pilot | geplant |
| Phase 10 | MVP-Produktion | geplant |
| Phase 11 | Marketing-, Vertriebs- und Kundenkommunikationsmodule | spätere Ausbauphase |
| Phase 12 | Lernsystem und Kompetenzpfade | spätere Ausbauphase |
| Phase 13 | Integrationen als Entwurf, keine Außenwirkung | spätere Ausbauphase |
| Phase 14 | Wissenssystem-Ausbau und optionale RAG-Vorbereitung | spätere Ausbauphase |
| Phase 15 | B2B-, Team- und Organisationsfunktionen | spätere Ausbauphase |
| Phase 16 | Kontrollierte Automatisierung mit Bestätigung | spätere Ausbauphase |
| Phase 17 | Skalierung, Monitoring-Ausbau und Geschäftsmodellvalidierung | spätere Ausbauphase |
| Phase 18 | Self-Hosted, Enterprise und lizenzierte Fachquellen | spätere Ausbauphase |
| Phase 19 | Internationale Erweiterung | spätere Ausbauphase |
| Phase 20 | Kontinuierliche Verbesserung | laufend |

---

## Phase 0 — Projektgrundlage und Architekturverfassung

**Ziel:** Das Projekt bekommt eine feste Grundlage. Claude Code kann aus den Dokumenten ableiten, was gebaut werden darf und was nicht.

**Artefakte (Auswahl):**

- `README.md`, `CLAUDE.md`, `MASTER_INDEX.md`
- `MVP_SPEC.md`, `ROADMAP.md`
- `ARCHITECTURE.md`, `DATA_MODEL.md`
- `PRIVACY.md`, `SECURITY.md`, `COMPLIANCE.md`
- `AGENTS.md`, `WORKFLOWS.md`, `DOCUMENTS.md`, `SOURCES.md`
- `TESTING.md`, `RELEASES.md`, `MONITORING.md`
- `BUSINESS_MODEL.md`, `LICENSE.md`
- Grundstruktur der Ordner und Templates

**Nicht-Ziele Phase 0:**

- produktive App
- echte Agentenautomation
- echte Integrationen
- Datenbank
- Nutzerkonten
- E-Mail
- RAG
- Zahlungsfunktionen
- CRM
- Buchhaltung
- Produktionsdeployment

**Erfolgskriterium:** Claude Code kann aus diesen Dokumenten ableiten, was gebaut werden darf und was nicht.

---

## Phase 1 — Datenmodell, Umgebungen und Sicherheitsfundament

Technische Basis schaffen: Dev/Test/Prod-Umgebungen, Feature Flags basic, Datenmodell-Start (Nutzer, Projekt, Aufgabe, Dokument, Quelle, Risiko, Entscheidung, Gate-Ergebnis, Audit-Log), Sensibilitätsstufen, Zugriffskontrolle basic.

---

## Phase 2 — Projektakte, Aufgaben und Basis-UI

Projekt-Dashboard basic, Projektakte, Aufgabenverwaltung, Risikoübersicht light, Dokumentenzentrum basic, Quellenstatusanzeige light, Umgebungshinweis sichtbar, Export basic.

---

## Phase 3 — CEO-Orchestrator und Kernagenten

CEO-Orchestrator basic + MVP-Kernagenten (siehe `AGENTS.md`). Rollenverträge, Promptversionierung basic, Agentenlauf-Objekt, Kontextpakete, Agentenrechte basic, Agentenverhaltenstests.

---

## Phase 4 — Dokumente, Quellenstatus und Export

Dokumenttypen, Statuslogik, Versionierung basic, Abschnittsstatus, Quellenstatus pro Dokument, Fachprüfungsstatus, Exportwarnungen, Markdown-/JSON-Export, Export-Gate, Dokumenten-Gate.

---

## Phase 5 — Onboarding, Reifegrad und erste Workflows

Onboarding light, Zielklärung, Reifegradmodell basic, Workflows: Startorientierung, Idee validieren, Mini-Businessplan, MVP planen, Datenschutz-Basischeck, Finanzplan light, erste Kundenansprache als Entwurf. Pausieren und Fortsetzen.

---

## Phase 6 — Finanzplan light und Risikoübersicht

Kostenliste, Einnahmenannahmen, Szenarien, Break-even grob, Liquiditätsrisiko light, Risikoampel, Preisannahmen, Fachprüfungsstatus, Finanzexport.

---

## Phase 7 — Datenschutzmodus, Datenlebenszyklus und Nutzerrechte

Gespeicherte Daten anzeigen, Profil bearbeiten, Projekt/Dokument löschen, Export, Datenschutzmodi, Sensibilitätsklassifikation basic, externe Verarbeitung markieren, Agentenkontextminimierung, Einwilligung basic, Widerruf basic, Audit bei Export/Löschung.

---

## Phase 8 — Qualitätssicherung, Gates und Testsystem

Gate-Engine basic, Datenschutz-, Sicherheits-, Quellen-, Fachprüfungs-, Agenten-, Export-, kritische-Aktion-, Release-Gate. Testsystem und synthetische Testdaten. Regressionstestliste. Release-Checkliste.

---

## Phase 9 — MVP-Pilot

Kontrollierter Pilotbetrieb mit Kennzeichnung, ohne kritische Außenwirkung. Export, Löschung, Datenschutzinformationen, Feedbackkanal, Monitoring basic, Rollback.

---

## Phase 10 — MVP-Produktion

Stabile erste Produktionsversion, wenn Test-to-Production-Gate bestanden. Produktionsblocker aus `MASTER_INDEX.md` §7 müssen geschlossen sein.

---

## Spätere Ausbauphasen (11–20)

Marketing-/Vertriebs-/Kommunikationsmodule, Lernsystem, Integrationen als Entwurf, RAG-Vorbereitung, Team/Organisation, kontrollierte Automatisierung, Skalierung, Self-Hosted/Enterprise, internationale Erweiterung, kontinuierliche Verbesserung.

Kein Vorziehen. Jede Phase wird eigenständig geplant, umgesetzt, getestet und freigegeben.

---

## Reihenfolge-Disziplin

- Keine Phase wird übersprungen.
- Keine Phase wird parallel zu einer nicht abgeschlossenen Phase gestartet, außer ausdrücklich geplante Arbeit.
- Jeder Schritt ist durch einen Run-Bericht in `reports/` belegt.
- Phasenwechsel wird in `releases/` dokumentiert.
