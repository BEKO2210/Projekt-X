# MASTER_INDEX.md — Zentrale Dokumentübersicht

> **Status:** Konzept- und Architekturphase (Phase 0 aktiv).
> **Aktueller Stand:** Run 1 ✔ (Foundation), Run 2 aktiv (Vertiefung Kerndokumentation).
> **Verbindlicher Name der Projektverfassung:** `KI_COMPANION_BLUEPRINT.md` (siehe `decisions/ADR-001-blueprint-filename.md`). Andere Bezeichnungen wie „PROJECT_BLUEPRINT.md" sind **nicht** gültig.

---

## 1. Lesereihenfolge

Empfohlene Reihenfolge für neue Leser, Agenten und Prüfer:

1. `KI_COMPANION_BLUEPRINT.md` — Projektverfassung (Masterdokument).
2. `CLAUDE.md` — Arbeitsvertrag und harte Regeln.
3. `MASTER_INDEX.md` — diese Datei.
4. `MVP_SPEC.md` — verbindliche MVP-Grenze.
5. `ROADMAP.md` — Phasen, Reihenfolge, aktuelle Phase.
6. `ARCHITECTURE.md` — geplante Systemschichten.
7. `DATA_MODEL.md` — Objekte, Status, Beziehungen.
8. `PRIVACY.md`, `SECURITY.md`, `COMPLIANCE.md` — Schutzprinzipien.
9. `AGENTS.md` — Rollenmodell der Agenten.
10. `WORKFLOWS.md`, `DOCUMENTS.md`, `SOURCES.md` — operative Dokumente.
11. `TESTING.md`, `RELEASES.md`, `MONITORING.md` — Qualität und Betrieb.
12. `BUSINESS_MODEL.md` — Kostenstruktur und Preismodellhypothesen.
13. `LICENSE.md` — Lizenzstatus.

---

## 2. Hauptdokumente

| Datei | Zweck |
|---|---|
| `README.md` | Einstieg für Menschen, ehrliche Projektbeschreibung. |
| `CLAUDE.md` | Arbeitsvertrag für Claude Code, harte Regeln. |
| `MASTER_INDEX.md` | Zentrale Lesereihenfolge, Prioritäten. |
| `MVP_SPEC.md` | Verbindliche MVP-Grenze. |
| `ROADMAP.md` | Phasen und Reihenfolge. |
| `ARCHITECTURE.md` | Technische Zielstruktur. |
| `DATA_MODEL.md` | Objekte, Status, Beziehungen, Sensibilität. |
| `PRIVACY.md` | Datenschutzregeln, Datenlebenszyklus. |
| `SECURITY.md` | Zugriff, Secrets, Agentenrechte. |
| `COMPLIANCE.md` | Fachgrenzen, rechtliche Grenzen. |
| `AGENTS.md` | Rollenmodell, Rollenverträge. |
| `WORKFLOWS.md` | MVP-Workflows. |
| `DOCUMENTS.md` | Dokumenttypen und Statuslogik. |
| `SOURCES.md` | Quellenstatus, Aktualität, Lizenz. |
| `TESTING.md` | Teststrategie, Pflichtfälle. |
| `RELEASES.md` | Umgebungen, Gates, Rollback. |
| `MONITORING.md` | Logging, Audit, Incidents. |
| `BUSINESS_MODEL.md` | Kosten, Preismodell, Fairness. |
| `LICENSE.md` | Lizenzentscheidung oder `license_decision_pending`. |

---

## 3. Ordner

| Ordner | Zweck |
|---|---|
| `decisions/` | Architecture Decision Records (ADR). |
| `specs/` | Detaillierte Funktionsspezifikationen. |
| `prompts/` | Agenten-Prompt-Spezifikationen. |
| `templates/` | Wiederverwendbare Prüf- und Berichtsvorlagen. |
| `testdata/` | Ausschließlich synthetische Testdaten. |
| `examples/` | Beispielabläufe und Beispielausgaben. |
| `releases/` | Release-Dokumentation. |
| `incidents/` | Incident-Berichte und -Regeln. |
| `audits/` | Prüfberichte. |
| `reports/` | Run-Berichte. |
| `src/` | Code — erst nach Techstack-ADR. |
| `tests/` | Tests — erst nach Testsetup. |
| `config/` | Konfiguration ohne Secrets. |
| `scripts/` | Hilfsskripte ohne echte Außenwirkung. |

---

## 4. Prioritäten (Phase 0)

1. Dokumentationsfundament.
2. Harte Regeln (`CLAUDE.md`).
3. MVP-Grenze (`MVP_SPEC.md`).
4. Roadmap-Phasen (`ROADMAP.md`).
5. Architekturprinzipien (`ARCHITECTURE.md`).
6. Datenschutz-, Sicherheits-, Compliance-Grundlagen.

Alles Weitere folgt erst, wenn diese Fundamente tragen.

---

## 5. MVP-Erlaubnisliste

Im MVP dürfen geplant (und später, nach Gates, implementiert) werden:

- Projektakte mit Projektname, Ziel, Ausgangslage, Status.
- Aufgabenliste, Blockerstatus, Priorität.
- Risikoübersicht light.
- Dokumentenzentrum mit Entwurfsstatus.
- Quellenstatus und Fachprüfungsstatus pro Aussage.
- Finanzplan light (Kosten, Annahmen, Szenarien, Risikoampel).
- Datenschutzmodus (Standard, Streng).
- Export als Markdown und optional JSON.
- Projektlöschung mit Bestätigung und Audit.
- CEO-Orchestrator basic + begrenzte Kernagenten (siehe `AGENTS.md`).
- Onboarding light.
- Feature-Flags basic.
- Entwicklungs-, Test- und Produktionskonzept.

---

## 6. MVP-Verbotsliste

Im MVP **nicht** erlaubt:

- Automatisches Senden von E-Mails, Nachrichten, Anträgen.
- Behördeneinreichungen.
- Zahlungen, Bankintegration, Buchhaltung.
- Automatische Kalenderaktionen, Social-Media-Posts.
- Verbindliche Rechts- oder Steuerberatung.
- Fördergarantien oder Bewilligungsversprechen.
- RAG mit ungeprüften oder unlizenzierten Fachquellen.
- Vollständiges CRM, Enterprise-Teamrollen.
- Internationale Rechtslogik.
- Kreditberatung, Zahlungsintegration.
- Automatische Verträge.
- Produktionsdeployment ohne Test-Gate.

---

## 7. Höchste Produktionsblocker

Ein Release in Produktion ist verboten, solange einer dieser Blocker offen ist:

1. Echte Nutzerdaten außerhalb Produktion im System.
2. Secrets im Repository oder in Konfigurationen.
3. Fehlende oder fehlerhafte Löschfunktion.
4. Fehlender oder fehlerhafter Export.
5. Agenten ohne Rollenvertrag aktiv.
6. Kritische Aktionen ohne Human-in-the-loop aktiv.
7. Integrationen mit Außenwirkung ohne Gate aktiv.
8. Datenschutzprüfung nicht bestanden.
9. Sicherheitsprüfung nicht bestanden.
10. Tests nicht bestanden oder nicht vorhanden für MVP-Kernflüsse.
11. Dev-Only-Komponenten, Mocks oder Test-API-Schlüssel aktiv.
12. Widersprüche zwischen `CLAUDE.md`, `MVP_SPEC.md` und Implementierung.

---

## 8. Statusmarkierungen

Alle Dokumente in diesem Repository tragen einen der folgenden Reifegrade:

- **Konzept:** Idee, noch nicht entschieden.
- **Entwurf:** Beschreibung vorhanden, offene Fragen.
- **Entschieden:** ADR oder Run-Bericht vorhanden.
- **Implementiert:** Code existiert in späteren Phasen.
- **Freigegeben:** durchlaufene Gates (Datenschutz, Sicherheit, Test).

Stand Run 2: Dokumente überwiegend **Entwurf**. Folgende Punkte sind **entschieden** (ADR oder Run-Report vorhanden):

- Dateiname der Projektverfassung → `ADR-001-blueprint-filename.md`
- CLAUDE.md-Struktur nach Blueprint Teil 37 → Run-Bericht Run 2
- Abnahmekriterien-Skala für MVP → `MVP_SPEC.md` §10 (28 Kriterien A01–A28)
- 10 MVP-Pflichttestfälle → `MVP_SPEC.md` §12

---

## 9. Run-Historie

| Run | Name | Status | Bericht |
|---|---|---|---|
| 001 | Foundation | abgeschlossen | `reports/run-001-foundation.md` |
| 002 | Vertiefung Kerndokumentation | aktiv (dieser Run) | `reports/run-002-deepen-core-docs.md` |

---

## 10. ADR-Register

| ID | Titel | Status | Datum |
|---|---|---|---|
| ADR-001 | Dateiname der Projektverfassung | akzeptiert | 2026-04-17 |

ADR-Vorlage: `decisions/ADR-template.md`.

---

## 11. Offene ADR-Kandidaten (nicht entschieden, nicht blockierend für Dokumentation)

- Techstack (Sprache, Framework, Datenbank, Laufzeit) — **zwingend** vor Phase 1.
- Test-Framework und CI-Pipeline — vor Phase 1.
- Branch- und Deployment-Strategie — vor Phase 1.
- Feature-Flag-Framework — vor oder mit Phase 1.
- Lizenz (siehe `LICENSE.md`) — offen, nicht blockierend für Phase 0/1.
