# ROADMAP.md — Phasen und Reihenfolge

> **Status:** Konzept. Phasen sind Leitplanken, keine Termine.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 33.

---

## Aktuelle Phase

**Phase 0 — Projektgrundlage und Architekturverfassung (aktiv).**

Aktueller Fortschritt:

- **Run 1 (Foundation) abgeschlossen.** Siehe `reports/run-001-foundation.md`.
- **Run 2 (Vertiefung Kerndokumentation) aktiv.** Siehe `reports/run-002-deepen-core-docs.md`. Ziel: `CLAUDE.md` nach Blueprint Teil 37 ausbauen, `MVP_SPEC.md` um testbare Abnahmekriterien und 10 MVP-Testfälle ergänzen, `ROADMAP.md` Phase 1 strukturell vorbereiten, `MASTER_INDEX.md` aktualisieren, erste ADR anlegen.

Phase 0 bleibt aktiv, solange Dokumentation nicht vollständig tragfähig ist und Techstack-ADR fehlt.

---

## Phasenübersicht

| Phase | Ziel | Status |
|---|---|---|
| **Phase 0** | Projektgrundlage und Architekturverfassung | **aktiv** (Run 1 ✔, Run 2 aktiv) |
| Phase 1 | Datenmodell, Umgebungen und Sicherheitsfundament | geplant, strukturell vorbereitet (§ Phase 1 unten) |
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

**Ziel:** Technische Basis schaffen. Das System kann Kernobjekte sicher speichern, projektbezogen trennen und Status führen (Blueprint §33.6).

**Voraussetzungen vor Phase 1 (Eintrittsgates):**

- Phase 0 als abgeschlossen markiert.
- Techstack-ADR in `decisions/` (Sprache, Framework, Datenbank, Laufzeit, Test-Framework). **Ohne diese ADR kein Phase-1-Start.**
- `CLAUDE.md` enthält alle Teil-37-Kapitel (erfüllt in Run 2).
- `MVP_SPEC.md` mit testbaren Abnahmekriterien (erfüllt in Run 2).
- `DATA_MODEL.md` mit Objekten und Statusfeldern (erfüllt in Run 1).

**Artefakte Phase 1:**

- Entwicklungsumgebung (Dev)
- Testumgebung (Test)
- Produktionskonzept (Prod, noch nicht deployed)
- Umgebungskonfiguration mit Trennung (siehe `config/README.md`)
- Feature Flags basic (nach `CLAUDE.md` §12)
- Datenmodell-Start in Code (passend zu `DATA_MODEL.md`):
  - Nutzerobjekt (`user`, `user_profile_light`)
  - Projektobjekt (`project`, `project_context_summary`)
  - Aufgabenobjekt (`task`)
  - Dokumentobjekt basic (`document`, `document_version`)
  - Quellenobjekt basic (`source_basic`)
  - Risikoobjekt basic (`risk`)
  - Entscheidungsobjekt basic (`decision_light`)
  - Gate-Ergebnis basic (`gate_result`)
  - Audit-Log basic (`audit_log`)
- Sensibilitätsstufen (`gering`/`mittel`/`hoch`/`sehr_hoch`)
- Datenschutzstatus, Sicherheitsstatus, Quellenstatus als Enums
- Zugriffskontrolle basic: `user_id`/`project_id`-Check auf jedem Objekt
- Basis-Testsystem mit synthetischen Testdaten (in `testdata/`)
- Erste Tests für: Zugriffskontrolle, Statuslogik, Umgebungstrennung, Secret-Scan

**Erfolgskriterium Phase 1:**

Kernobjekte können sicher gespeichert, projektbezogen getrennt und mit Status versehen werden. Tests für Zugriffskontrolle und Umgebungstrennung bestehen. Keine kritische Außenwirkung möglich.

**Verlassen Phase 1 → Phase 2 möglich, wenn:**

- Datenmodell in Code vorhanden und getestet.
- Umgebungstrennung nachweisbar (Dev-Artefakt kann nicht Prod berühren).
- Keine Secrets im Repo (automatischer Scan).
- Keine echten Daten in Dev/Test (manuell geprüft).
- Dev-to-Test-Gate existiert (noch nicht mit Inhalt befüllt).

**Nicht-Ziele Phase 1** (aus `CLAUDE.md` §32 und Blueprint §33.7):

- komplexe UI
- vollständige Agenten
- echte Integrationen
- E-Mail-Automation
- Zahlungsfunktionen
- vollständiges CRM
- umfangreiche Teamrollen
- lizenzierte Fachquellen
- komplexe RAG

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
