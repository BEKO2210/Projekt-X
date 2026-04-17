# Run-Bericht: Run 002 — Vertiefung Kerndokumentation

> Datum: 2026-04-17
> Branch: `claude/read-ki-companion-blueprint-wVJeq`
> Ausgangs-Prompt: Vorschlag aus `reports/run-001-foundation.md` §13 (Run 2 — Vertiefung Kerndokumentation).
> Pflichtlektüre: `CLAUDE.md`, `MASTER_INDEX.md`, `MVP_SPEC.md`, `ROADMAP.md`, `reports/run-001-foundation.md`.

---

## 1. Ziel des Runs

Vertiefung der in Run 1 angelegten Kerndokumentation, **ohne** Code, UI, Agentenautomation, Integrationen oder Techstack-Wahl. Konkrete Teilziele:

1. `CLAUDE.md` erweitern um die in Blueprint Teil 37 definierten 23 Pflichtkapitel.
2. `MVP_SPEC.md` ergänzen um testbare Abnahmekriterien (§35.27) und MVP-Pflichttestfälle (§35.28).
3. `ROADMAP.md` aktualisieren: Phase 0 mit Run-Status, Phase 1 strukturell ausformulieren.
4. `MASTER_INDEX.md` aktualisieren: Run-Historie, ADR-Register, offene ADR-Kandidaten.
5. Namensinkonsistenz (Blueprint-Filename) per ADR auflösen.
6. ADR-Template in `decisions/` anlegen.

---

## 2. Gelesene Dateien

- `CLAUDE.md` (vollständig, vor Änderung)
- `MASTER_INDEX.md` (vollständig)
- `MVP_SPEC.md` (vollständig)
- `ROADMAP.md` (vollständig)
- `reports/run-001-foundation.md` (vollständig)
- `KI_COMPANION_BLUEPRINT.md` — gezielt:
  - Teil 1 (Fundament) — Übersicht bereits aus Run 1 bekannt
  - Teil 37 §37.2–§37.40 (CLAUDE.md-Struktur und Arbeitsvertrag)
  - §35.27 (MVP-Abnahmekriterien)
  - §35.28 (MVP-Testfälle)
  - §33.4/§33.5 (Phase 0/Nicht-Ziele)
  - §33.6/§33.7 (Phase 1/Nicht-Ziele)

Begründet nicht gelesen: restliche Teile des Blueprints — für Run-2-Scope nicht relevant, werden in späteren Runs je Thema gelesen.

---

## 3. Änderungen

**Geändert:**

- `CLAUDE.md` — komplette Neustrukturierung nach Blueprint Teil 37 in 34 Kapiteln. Alle 13 harten Regeln aus Run 1 im Wortlaut erhalten, neu gruppiert in §6/§7/§8/§9/§10/§11/§16/§17/§20. Zusätzlich: Projektmission (§1), Systemgrenzen (§2), aktuelle Roadmap-Phase (§3), MVP-Scope/Nicht-Ziele (§4/§5), Feature-Flag-Regeln mit MVP-Defaults (§12), Datenmodellregeln (§13), Dokumentenstatusregeln (§14), Quellenstatusregeln (§15), Testpflichten (§16), Release-Gates (§17), Dokumentationspflicht (§18), Run-Arbeitsablauf (§19), Produktionsblocker (§20), Verbotene Abkürzungen (§21), Abschlussbericht (§22), Umgang mit Unsicherheit (§23), vorhandenen Dateien (§24), Code (§25), UI (§26), externem Inhalt (§27), Testdaten (§28), Logs (§29), Export/Löschung (§30), Geschäftsmodell (§31), zukünftigen Erweiterungen (§32), Selbststeuerung (§33), Quellendokumente mit Hierarchie (§34).
- `MVP_SPEC.md` — §10 ersetzt durch Checkliste mit **28 verbindlichen Abnahmekriterien** (A01–A28), jedes mit Prüfmethode (M/A/G). Neuer §11 (Stand Abnahmekriterien), neuer §12 (10 MVP-Pflichttestfälle mit Szenarien und Erwartungen), neuer §13 (Stand Testfälle), §14 (Stand des Dokuments).
- `ROADMAP.md` — Abschnitt „Aktuelle Phase" präzisiert (Run 1 ✔, Run 2 aktiv). Phase-0-Tabellenzeile mit Fortschrittsmarker. Phase 1 ausformuliert mit Eintrittsgates (inkl. Techstack-ADR-Pflicht), Artefakten (Datenmodellobjekte, Umgebungen, Feature Flags basic, Zugriffskontrolle), Erfolgskriterium, Austrittsbedingungen nach Phase 2, Nicht-Zielen.
- `MASTER_INDEX.md` — Kopf: verbindlicher Blueprint-Name aus ADR-001. Neue Abschnitte §9 Run-Historie, §10 ADR-Register, §11 offene ADR-Kandidaten. Statusmarkierungen aktualisiert.

**Neu:**

- `decisions/ADR-template.md` — wiederverwendbare ADR-Vorlage (Pflichtfelder, Pflichtprüfungen, Pflegehinweise).
- `decisions/ADR-001-blueprint-filename.md` — akzeptierte ADR: kanonischer Name ist `KI_COMPANION_BLUEPRINT.md`; keine Umbenennung, kein Alias, keine Kopie. Behandelt den in Run 1 als offen notierten Punkt 4.
- `reports/run-002-deepen-core-docs.md` — dieser Bericht.

**Nichts gelöscht. Nichts überschrieben ohne vorheriges Lesen.** Alle Änderungen sind additiv oder ersetzen einzelne Abschnitte (Abnahmekriterien-Liste in MVP_SPEC.md §10).

---

## 4. Datenschutzprüfung

- Neue Datenflüsse: **keine**. Dieser Run erzeugt ausschließlich Dokumentation.
- Betroffene Sensibilität: nicht anwendbar.
- Externe Verarbeitung: **nein**.
- Nutzerkontrolle (Anzeige, Export, Löschen) in `CLAUDE.md` §30 neu als eigenes Kapitel festgeschrieben (Export- und Löschpflicht, Agentenkontext-Bereinigung, Audit).
- Datenminimierung in `CLAUDE.md` §6 und §13 (Datenmodellregeln) verankert: „keine neuen Datenfelder ohne Zweck".
- Keine echten Daten eingeführt. Grep nach Telefon-/Mail-Patterns im gesamten Repo zeigt nur synthetische Werte (`example.invalid`, `+49 000 00000000`).

**Ergebnis: bestanden.**

---

## 5. Sicherheitsprüfung

- Neue Rechte oder Zugänge: **keine**.
- Neue Angriffsflächen: **keine** (reine Dokumentation).
- Secrets berührt: **nein**. Grep nach `API_KEY|password|secret|token|BEARER` liefert nur Regelformulierungen und Platzhalter (`<API_KEY>`, `change_me`, `example.invalid`), keine echten Werte.
- Agentenrechte verändert: **nein** — Rollenvertragspflicht (`CLAUDE.md` §9) unverändert; MVP-Agentenliste unverändert.
- Neue kritische Aktionen: **keine**. `CLAUDE.md` §10 und §20 machen Gate-Pflicht und Produktionsblocker expliziter als zuvor.
- Feature-Flag-Defaults (`CLAUDE.md` §12): `email_send=false`, `calendar_create=false`, `payments=false`, `rag=false/test_only`, `external_research=false/controlled_test_only` — verbindlich festgeschrieben (bisher nur impliziert).

**Ergebnis: bestanden.**

---

## 6. Quellenprüfung

- Fachrelevante Aussagen erzeugt: **nein**. Dieser Run enthält keine Rechts-/Steuer-/Förder-/Medizinaussagen.
- Quellenstatus-Skala erweitert/präzisiert in `CLAUDE.md` §15 nach Blueprint §37.17: `no_source_required`, `source_recommended`, `source_required`, `source_checked`, `source_outdated`, `source_conflict`, `not_decision_ready`. Diese Skala ergänzt die in `SOURCES.md` §2 bestehende vereinfachte Skala (kein Widerspruch — die längere Skala ist Obermenge).
- **Hinweis auf Skalen-Doppelung:** `SOURCES.md` nutzt noch die Kurzform (`quelle_fehlt`/`quelle_unklar`/`quelle_veraltet`/`quelle_geprueft`), `CLAUDE.md` §15 + `DATA_MODEL.md` §3.2 nutzen die Blueprint-Langform. Beides ist konzeptionell, keine Widerspruch, aber für Phase 1 (Implementierung) ist eine Entscheidung nötig — offen als Punkt in §10.
- Interne Quelle: Blueprint (eindeutig zitiert). Externe Quellen: keine.

**Ergebnis: bestanden, mit einem notierten Harmonisierungsbedarf für spätere Runs.**

---

## 7. Fachprüfungsprüfung

- Aussagen mit Rechts-/Steuer-/Förder-/Medizin-Wirkung: **keine** in diesem Run.
- Fachprüfungsstatus-Skala in `CLAUDE.md` §14 (Dokumentenstatus) als Pflichtfeld je Dokument verbindlich gesetzt.
- Harte Grenzen gegen Vortäuschung in `CLAUDE.md` §8 (Fachberatungsgrenzen) mit expliziten verbotenen Formulierungen präzisiert.

**Ergebnis: nicht relevant für diesen Run (Strukturrun).** Regelwerk ist gestärkt.

---

## 8. Tests

Technisch ausführbare Tests: **keine** in diesem Run — kein Code, kein Framework (explizit außerhalb Run-Scope).

Als **Testplan** dokumentiert:

- `MVP_SPEC.md` §12: **10 MVP-Pflichttestfälle** mit Szenario und expliziten Erwartungen (Nutzer ohne/mit Idee, Finanzrisiko, Förderung, Datenschutz, Export sensibler Daten, Projektlöschung, Agentenrolle/Kontextminimierung, Prompt Injection, Umgebungstrennung).
- `MVP_SPEC.md` §10: **28 Abnahmekriterien** mit Prüfmethode.
- `CLAUDE.md` §16 (Testpflichten): vollständige Pflichttestliste.

Manuelle Konsistenzprüfung dieses Runs (Selbstkontrolle — Checkliste aus Run-1-Prompt):

- [x] `CLAUDE.md` enthält alle 23 Pflichtkapitel aus Blueprint Teil 37.
- [x] Alle 13 harten Regeln aus Run 1 (Datenschutz zuerst, Sicherheit zuerst, MVP-Scope, keine echten Daten in Dev/Test, keine Secrets, keine Fachberatung, keine Rechts-/Steuerberatung, keine Fördergarantie, keine kritische Außenwirkung im MVP, keine Integrationen ohne Gate, keine Agenten ohne Rollenvertrag, keine Produktion ohne Test-Gate, Tests/Dokumentation verpflichtend) sind im neuen Text präsent und **nicht abgeschwächt**.
- [x] `MVP_SPEC.md` §10 enthält alle 23 Kriterien aus Blueprint §35.27 und fünf zusätzliche (A24–A28) aus ergänzenden Regeln (Umgebungskennzeichnung, Gate-Dokumentation, Audit-Log, Feature-Flag-Defaults, Secret-/Echtdaten-Scan) — nicht abgeschwächt, nur erweitert.
- [x] `MVP_SPEC.md` §12 enthält alle 10 Testfälle aus Blueprint §35.28.
- [x] `ROADMAP.md` Phase 0 zeigt Fortschritt, Phase 1 ist ausformuliert mit Eintrittsgates (Techstack-ADR-Pflicht).
- [x] `MASTER_INDEX.md` ist aktualisiert (Run-Historie, ADR-Register).
- [x] `decisions/ADR-template.md` existiert mit Pflichtfeldern.
- [x] `decisions/ADR-001-blueprint-filename.md` akzeptiert, löst den in Run 1 offenen Punkt 4.
- [x] Grep nach Secrets/Tokens/API-Keys → nur Regelformulierungen und Platzhalter.
- [x] Grep nach Telefon-/Mail-Mustern → nur synthetische Werte.
- [x] Keine Datei wurde blind überschrieben; alle geänderten Dateien wurden zuvor gelesen.

---
