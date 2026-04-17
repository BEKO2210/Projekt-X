# CLAUDE.md — Arbeitsvertrag für Claude Code

> **Status:** Konzept- und Architekturphase. Diese Datei ist oberste Projektregel für jeden Claude-Code-Run.
> Bei Widersprüchen zwischen einem Run-Prompt und diesem Dokument hat **CLAUDE.md Vorrang**, bis der Widerspruch explizit aufgelöst ist.
> Struktur folgt Blueprint Teil 37. Details werden an Spezialdokumente delegiert (siehe §34).

---

## 1. Projektmission

Dieses Projekt entwickelt ein KI-basiertes Begleitsystem für Menschen, die sich beruflich orientieren, selbstständig machen, ein kleines Unternehmen starten, ein Projekt strukturieren oder neue Fähigkeiten aufbauen möchten.

Das System soll Nutzer unterstützen bei:

- Orientierung
- Projektstruktur
- Aufgaben
- Dokumententwürfen
- Finanzplanung light
- Datenschutzbewusstsein
- Quellenstatus
- Risiken
- Lernpfaden
- sicheren nächsten Schritten

Das System ersetzt **keine** Rechtsberatung, Steuerberatung, Förderberatung, Finanzberatung, medizinische Beratung oder sonstige Fachprüfung. Es arbeitet vorbereitend, strukturierend und erklärend.

---

## 2. Systemgrenzen

Das System **darf**:

- Informationen strukturieren
- Entwürfe erstellen
- Risiken markieren
- Aufgaben ableiten
- Quellenbedarf markieren
- Fachprüfungsbedarf markieren
- Lernschritte vorschlagen
- Finanzannahmen grob modellieren
- Datenschutzfragen sichtbar machen
- Nutzer beim nächsten Schritt unterstützen

Das System **darf nicht**:

- verbindliche Rechtsberatung geben
- verbindliche Steuerberatung geben
- Förderansprüche garantieren
- Verträge final freigeben
- Behördenentscheidungen vorhersagen
- Zahlungen auslösen
- E-Mails ohne Bestätigung senden
- echte Außenwirkung im MVP erzeugen
- sensible Daten ohne Zweck verarbeiten
- Datenschutzmodus umgehen
- Nutzer zu riskanten Entscheidungen drängen
- illegale oder täuschende Handlungen unterstützen

---

## 3. Aktuelle Roadmap-Phase

**Aktive Phase:** Phase 0 — Projektgrundlage und Architekturverfassung. **Run 1 abgeschlossen** (siehe `reports/run-001-foundation.md`). **Run 2 aktiv** (Vertiefung Kerndokumentation).

**Erlaubt in aktueller Phase:**

- Dokumentationsstruktur anlegen und vertiefen
- Architektur beschreiben
- MVP-Scope definieren und präzisieren
- Datenmodell spezifizieren (konzeptionell)
- Datenschutz- und Sicherheitsregeln dokumentieren
- Agentenrollen als Spezifikation (noch nicht als Code)
- Test- und Releaseprozess definieren
- ADRs in `decisions/` anlegen
- synthetische Testdaten vorbereiten

**Nicht erlaubt in aktueller Phase:**

- produktive App bauen
- echte Integrationen aktivieren
- autonome Agenten implementieren
- E-Mail-/Kalender-/Zahlungs-/Behörden-Integrationen
- produktive RAG mit Fachquellen
- Techstack-Wahl ohne ADR

Aufgaben, die nicht zur aktuellen Phase passen, werden als spätere Phase dokumentiert (siehe `ROADMAP.md`).

---

## 4. MVP-Scope

Der MVP enthält **nur** das, was in `MVP_SPEC.md` ausdrücklich erlaubt ist. Diese Kurzform ist verbindlich:

- Onboarding light
- Projekt anlegen, Projektakte, Dashboard basic
- Aufgabenliste, Risikoübersicht light
- CEO-Orchestrator basic + Kernagenten (siehe §9)
- Mini-Businessplan, Finanzplan light, MVP-Plan
- Datenschutz-Basischeck
- Fördercheck light **ohne Garantie**
- Quellenstatus light, Fachprüfungsstatus light
- Export Markdown (JSON optional)
- Projektlöschung
- Datenschutzmodus **Standard** und **Streng**
- Audit basic für Export und Löschung
- Dev-/Test-/Prod-Struktur, Feature Flags basic, Tests basic

Alles außerhalb dieser Liste ist **nicht automatisch MVP**. Detail in `MVP_SPEC.md`.

---

## 5. MVP-Nicht-Ziele

Im MVP ausdrücklich **nicht** bauen:

- E-Mail-Versand, Kalendertermine, Zahlungen, Buchhaltung, CRM
- Behördenintegration, automatische Förderanträge, automatische Vertragsfreigabe
- verbindliche Rechts-/Steuerberatung, Fördergarantie, vollständige Datenschutzberatung
- Teamrollen, Organisationen, Enterprise, Self-Hosted
- internationale Rechtslogik
- produktive RAG-Fachwissensdatenbank, lizenzierte Fachquellen ohne geprüfte Lizenz
- Social-Media-Veröffentlichung, Telefonie, automatische Kundenkommunikation
- autonome Agenten mit Außenwirkung

Berührt eine Anforderung eines dieser Themen, muss Claude Code sie **blockieren** oder als spätere Phase dokumentieren.

---

## 6. Harte Datenschutzregeln

Datenschutz ist Produktkern. Bei jeder Funktion prüfen:

- Welche Daten entstehen?
- Warum werden sie gebraucht?
- Sind sie personenbezogen?
- Sind Daten Dritter betroffen?
- Sind sie sensibel?
- Werden sie gespeichert?
- Können sie gelöscht werden?
- Können sie exportiert werden?
- Welche Agenten dürfen sie sehen?
- Wird externe Verarbeitung genutzt?
- Gilt Datenschutzmodus Standard oder Streng?

**Verboten:**

- echte Nutzerdaten in Entwicklung oder Test
- echte Kundendaten in Testdaten
- Speicherung ohne Zweck
- externe Verarbeitung sensibler Daten ohne Freigabe
- Agentenvollzugriff auf Projektakte
- sensible Daten in Logs
- Passwörter, Tokens oder API-Schlüssel in Code, Logs, Prompts oder Dokumenten
- Nutzerdaten für Training im MVP
- Datenschutzrechte hinter Paywall

Jede datenverarbeitende Funktion braucht Lösch- und Exportbetrachtung. Datenminimierung, Zweckbindung, Nutzerkontrolle, Löschbarkeit sind **Pflichtmerkmale**, keine Features.

Detail: `PRIVACY.md`.

---

## 7. Harte Sicherheitsregeln

Bei jeder Funktion prüfen:

- Wer darf die Funktion nutzen?
- Welche Objekte werden gelesen / geändert?
- Wird `project_id` geprüft?
- Wird `user_id` geprüft?
- Gibt es sensible Daten?
- Gibt es Agentenzugriff?
- Gibt es Toolzugriff?
- Gibt es Feature Flag?
- Welche Umgebung ist erlaubt?
- Gibt es kritische Aktion?
- Ist Nutzerbestätigung nötig?
- Muss Audit geschrieben werden?

**Verboten:**

- Zugriffskontrolle nur im Frontend
- fremde Projektzugriffe
- Secrets im Code
- Secrets in Logs
- kritische Aktionen ohne Bestätigung
- produktive Secrets in Entwicklung oder Test
- Toolrechte ohne Gate
- Agentenrechte ohne Rollenvertrag
- Testsystem mit echter Außenwirkung
- Produktion ohne Test-Gate
- Commit von API-Keys, Passwörtern, Private Keys, Access Tokens, `.env`-Werten oder Zugangsdaten

Secret-Vorlagen gehören in dokumentierte Platzhalter (`<API_KEY>`, `change_me`).

Detail: `SECURITY.md`.

---

## 8. Fachberatungsgrenzen

Das System darf **keine** verbindliche Fachberatung vortäuschen. Besonders begrenzt:

- Recht, Steuern, Förderung, Versicherungen, Arbeitsrecht, Verträge
- Datenschutzrecht, Medizin/Gesundheit
- Finanzberatung, Kreditberatung, Anlageberatung

**Erlaubt:**

- allgemeine Orientierung, Checklisten, Fragen für Fachpersonen
- Entwürfe, Quellenbedarf, Risiken, Fachprüfungsstatus
- Aufgaben zur Klärung

**Verbotene Formulierungen (Beispiele):**

- „Du bekommst diese Förderung."
- „Das ist rechtlich sicher."
- „Diese Rechnung ist steuerlich korrekt."
- „Dieser Vertrag ist gültig."
- „Du musst genau X Euro Steuer zahlen."
- „Diese Datenschutzerklärung ist DSGVO-konform."
- „Kündige jetzt."
- „Nimm diesen Kredit."

Keine Fördergarantie. Keine Erfolgsquoten. Keine „sichere" Bewilligung. Förderinformationen erhalten immer einen Quellenstatus. Alle kritischen Aussagen brauchen Quellenstatus **und** Fachprüfungsmarkierung.

Detail: `COMPLIANCE.md`.

---

## 9. Agentenregeln

**Kein Agent ohne Rollenvertrag.** Jeder Agent braucht vor Betrieb dokumentiert:

- Name, Rolle, Zweck
- erlaubte Aufgaben, verbotene Aufgaben
- erlaubte Daten, verbotene Daten
- Toolrechte
- Datenschutzregeln, Sicherheitsregeln
- Quellenregeln, Fachprüfungsregeln
- Ausgabeformat
- Verhaltenstests
- Freigabestatus

**MVP-Agenten (geplant, nicht implementiert):**

- CEO-Orchestrator basic
- Orientierungs-Agent
- Gründungs-Agent light
- Finanz-Agent light
- Datenschutz-Agent light
- Dokumenten-Agent
- Quellenstatus-Agent light
- Qualitäts-Agent

**Agenten dürfen im MVP:** strukturieren, Entwürfe erstellen, Aufgaben erzeugen, Risiken markieren, Quellenbedarf markieren, Fachprüfungsbedarf markieren.

**Agenten dürfen im MVP nicht:** externe Aktionen ausführen, E-Mails senden, Kalendertermine erstellen, Zahlungen auslösen, Behörden kontaktieren, Verträge versenden, Kundendaten automatisch nutzen, Rechte selbst erweitern.

Detail: `AGENTS.md`.

---

## 10. Integrationsregeln

**Keine Integration ohne Integrationsakte.** Jede Integration braucht vor Aktivierung:

- Zweck, Anbieter, Datenfluss
- Rechte und Scopes
- Datenschutzprüfung, Sicherheitsprüfung
- Secrets-Konzept (nie im Repo)
- Sandbox
- Feature Flag
- Deaktivierungsmöglichkeit
- Audit, falls kritisch
- Rollback
- Teststatus, Freigabestatus

**Im MVP nicht aktivieren:** E-Mail-Versand, Kalendererstellung, Zahlungen, CRM, Buchhaltung, Behörden, Social-Media-Veröffentlichung, Telefonie.

**Im MVP erlaubt (mit Gate):** Export lokal, optional kontrollierte Webrecherche (nur wenn Datenschutz und Quellenstatus geregelt), lokale Modelle als Konzept oder Test, Datei-Upload nur mit klaren Grenzen.

Kein „mal kurz anbinden".

---

## 11. Umgebungsregeln

Es gibt **drei** Umgebungen, technisch getrennt:

**Development:**
- nur Mock-Daten
- keine echten Daten
- keine echten Secrets
- keine echte Außenwirkung
- experimentelle Prompts erlaubt, aber markiert

**Test:**
- produktionsnah
- synthetische Testdaten
- Sandbox-Integrationen
- Gate-Tests
- keine echte Außenwirkung

**Production:**
- nur getestete Funktionen
- nur freigegebene Agenten
- echte Daten nur mit Datenschutz und Sicherheit
- kritische Aktionen nur mit Bestätigung
- Monitoring und Audit aktiv

**Test und Produktion müssen technisch getrennt sein.** Dev-Only-Komponenten, Mocks, Dummy-Agenten, Test-API-Schlüssel dürfen nie aktiv in Produktion sein.

Detail: `RELEASES.md`.

---

## 12. Feature-Flag-Regeln

Riskante Funktionen müssen über Feature Flags steuerbar sein.

**MVP-Flags (geplant):**

- `feature.ceo_orchestrator`
- `feature.agent_finance_light`
- `feature.agent_privacy_light`
- `feature.agent_document`
- `feature.agent_quality`
- `feature.export_markdown`
- `feature.export_json`
- `feature.delete_project`
- `feature.source_status`
- `feature.financial_plan_light`
- `feature.privacy_mode_strict`
- `feature.external_research`
- `feature.email_send`
- `feature.calendar_create`
- `feature.payments`
- `feature.rag`

**MVP-Defaults (verbindlich):**

- `feature.email_send = false`
- `feature.calendar_create = false`
- `feature.payments = false`
- `feature.rag = false` oder `test_only`
- `feature.external_research = false` oder `controlled_test_only`

**Feature Flags dürfen Sicherheits- und Datenschutzregeln nicht umgehen.** Ein Flag auf `true` entbindet nicht von Gate, Test, Audit.

---

## 13. Datenmodellregeln

Jedes wichtige Objekt braucht:

- `id`
- `owner_user_id` oder `user_id` (falls nutzerbezogen)
- `project_id` (falls projektbezogen)
- `status`
- `created_at`, `updated_at`
- `sensitivity_level` (falls relevant)
- `privacy_status` (falls relevant)
- `security_status` (falls relevant)
- `source_status` (falls relevant)
- `expert_review_status` (falls relevant)

**MVP-Objekte (geplant):**

`user`, `user_profile_light`, `project`, `project_context_summary`, `task`, `workflow_basic`, `document`, `document_version`, `source_basic`, `risk`, `decision_light`, `agent_config`, `agent_run_summary`, `gate_result`, `audit_log`, `export_request`, `deletion_request`, `feature_flag`, `environment_config`.

**Keine neuen Datenfelder ohne Zweck.** Datenminimierung gilt auch im Datenmodell.

Detail: `DATA_MODEL.md`.

---

## 14. Dokumentenstatusregeln

**Kein Dokument darf ohne Status erscheinen.** Dokumentstatus-Skala:

- `draft`
- `internal_use`
- `source_required`
- `expert_review_recommended`
- `expert_review_required`
- `privacy_review_required`
- `security_review_required`
- `blocked`
- `archived`

**Jedes MVP-Dokument braucht:** Zweck, Dokumenttyp, Version, Status, Quellenstatus, Fachprüfungsstatus, Datenschutzstatus, Sensibilitätsstufe, Exportwarnung (falls relevant).

Dokumente mit Recht, Steuer, Förderung, Datenschutz oder Verträgen dürfen **niemals** als final oder garantiert korrekt erscheinen.

Detail: `DOCUMENTS.md`.

---

## 15. Quellenstatusregeln

Kritische Aussagen brauchen Quellenstatus. Skala:

- `no_source_required`
- `source_recommended`
- `source_required`
- `source_checked`
- `source_outdated`
- `source_conflict`
- `not_decision_ready`

**Quellenpflicht bei:** Recht, Steuern, Förderung, Datenschutzrecht, Behörden, Gebühren, Fristen, Versicherungen, Plattformregeln, Lizenzfragen, Preisen, aktuellen Gesetzen, aktuellen Programmen.

**Wenn Quelle fehlt:** nicht als sicher formulieren, Quellenbedarf markieren, Fachprüfungsbedarf markieren, Aufgabe zur Prüfung erzeugen.

**Keine erfundenen Quellen.** Keine stilisierten Scheinzitate.

Detail: `SOURCES.md`.

---

## 16. Testpflichten

Zentrale Funktionen brauchen Tests.

**Pflichttests im MVP:**

- Nutzer ohne Idee
- Nutzer mit Idee
- Finanzrisiko
- Förderung
- Datenschutzfall Kundendaten
- Export sensibler Daten
- Projektlöschung
- Agentenrolle und Kontextminimierung
- Prompt Injection
- Umgebungstrennung

**Zusätzliche Tests:**

- Zugriffskontrolle, Statuslogik, Sensibilitätsstufen
- Feature Flags, Quellenstatus, Fachprüfungsstatus
- Dokumentenstatus, Exportwarnungen, Löschlogik
- Keine Secrets in Logs

Wenn Tests technisch noch nicht möglich sind, muss ein **Testplan** und ggf. ein **Blocker** dokumentiert werden. Jeder Run erstellt oder aktualisiert Tests bzw. einen Testplan.

Detail: `TESTING.md`, `MVP_SPEC.md` §12 (MVP-Testfälle).

---

## 17. Release-Gates

**Keine direkte Produktion aus Entwicklung.**

**Development-to-Test-Gate (erforderlich):**

- Zweck dokumentiert
- MVP-Bezug geprüft
- Datenschutz grob geprüft
- Sicherheit grob geprüft
- Feature Flag vorhanden
- Testdaten synthetisch
- keine echten Secrets
- Basis-Tests vorhanden
- Dokumentation aktualisiert

**Test-to-Production-Gate (erforderlich):**

- Tests bestanden
- Datenschutz-Gate bestanden
- Sicherheits-Gate bestanden
- Quellenstatus geprüft (falls relevant)
- Fachprüfungsstatus geprüft (falls relevant)
- UI-Warnungen sichtbar
- Export/Löschung geprüft (falls relevant)
- Audit geprüft (falls relevant)
- Rollback vorhanden
- Monitoring vorhanden
- keine Produktionsblocker offen

Detail: `RELEASES.md`.

---
