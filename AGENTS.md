# AGENTS.md — Rollenmodell und Rollenverträge (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung, keine Agentenautomation.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 4 und Teil 5.

---

## 1. Grundidee

Das System ist als „digitale kleine Firma" konzipiert: ein **CEO-Orchestrator** koordiniert mehrere **Spezialagenten**. Jeder Agent hat einen **Rollenvertrag**. Ohne Rollenvertrag kein Agentenbetrieb.

---

## 2. Rollenvertrag — Pflichtfelder

Jeder Agent benötigt vor Betrieb einen dokumentierten Rollenvertrag mit mindestens:

- **Name und Version** des Agenten
- **Scope / Aufgabe**
- **Erlaubte Aktionen**
- **Verbotene Aktionen**
- **Datenzugriff** (nur minimiertes Kontextpaket)
- **Eingabe- und Ausgabeformat**
- **Eskalationspfad** (wann an Orchestrator, wann an Menschen)
- **Fehlerverhalten**
- **Grenzen gegenüber Recht/Steuern/Fördermitteln/Medizin/Finanzen**
- **Testfälle**
- **Reifegrad** (Prototyp, intern, freigegeben)
- **Rollenvertrag-Version**

Rollenverträge werden in `specs/` oder `prompts/` abgelegt, sobald erstellt. In Run 1 existieren **noch keine** Rollenverträge.

---

## 3. CEO-Orchestrator (Rolle)

Koordinationsinstanz. Ordnet Anfragen, sammelt Ergebnisse, führt Widersprüche zusammen, benennt Risiken, schlägt nächste Schritte vor.

- **Macht nicht** selbst fachliche Aussagen zu Recht/Steuern/Medizin.
- **Macht nicht** Endentscheidungen für den Nutzer.
- **Kann** Subagenten aktivieren, Ergebnisse prüfen, markieren, blockieren.

---

## 4. MVP-Kernagenten (geplant, nicht implementiert)

### 4.1 Orientierungs-Agent
Hilft Ziel, Ausgangslage, Richtung klären.

### 4.2 Gründungs-Agent light
Strukturiert Gründungsidee, Angebot, Zielgruppe, erste Schritte.

### 4.3 Finanz-Agent light
Erstellt Kostenübersicht, Einnahmenannahmen, Szenarien, Risikoampel — **keine** Steuerberatung.

### 4.4 Datenschutz-Agent light
Erkennt Datenarten, Sensibilität, externe Verarbeitung.

### 4.5 Dokumenten-Agent
Erzeugt Entwürfe mit Status.

### 4.6 Quellenstatus-Agent light
Markiert Quellenbedarf, Aktualitätsbedarf, nicht entscheidungsreife Aussagen.

### 4.7 Qualitäts-Agent
Prüft Entwürfe auf falsche Sicherheit, fehlende Quellen, Risiken, Fachprüfungsbedarf.

---

## 5. Verbotene Agentenaktionen (MVP, hart)

Agenten dürfen im MVP **nicht**:

- E-Mails senden
- Kalendertermine erstellen
- Behördenanträge einreichen
- Zahlungen auslösen
- Verträge final freigeben
- Steuerberatung geben
- Rechtsberatung geben
- Förderungen garantieren
- Nutzer zu Kreditaufnahme drängen
- Echte Kundendaten automatisiert verarbeiten
- CRM-Aktionen ausführen
- Social-Media-Posts veröffentlichen
- RAG-Fachquellen ungeprüft nutzen
- Agentenrechte selbst erweitern
- Produktionsregeln umgehen

---

## 6. Agentenlauf (Pflichtdatenfluss)

Jeder Agentenlauf erzeugt (später, bei Implementierung) ein `agent_run`-Objekt mit:

- Agent + Version + Rollenvertrag-Version
- Prompt-Version
- Kontextpaket (minimiert, protokolliert)
- Aufgabe
- Ergebnis
- Fehler/Warnungen
- Zeit, Dauer

---

## 7. Prompt-Versionierung

- Prompts liegen später in `prompts/` als versionierte Dateien.
- Jede Änderung an einem Prompt erhöht die Version.
- Agentenläufe referenzieren die genutzte Prompt-Version.

---

## 8. Eskalationspfad

Wenn ein Agent unsicher ist, Widerspruch erkennt, Fachprüfungsbedarf feststellt oder außerhalb Scope läuft:

1. Markierung der Ausgabe mit Unsicherheits-/Risikostatus.
2. Weitergabe an Orchestrator.
3. Bei Bedarf: Rückfrage an Nutzer.
4. Niemals: eigenmächtige Entscheidung, eigenmächtige Toolnutzung.

---

## 9. Testpflicht (Agentenverhalten)

Vor Produktionsfreigabe eines Agenten:

- Positivtests: typische Aufgaben, erwartete Struktur.
- Negativtests: Prompt-Injection-Versuche, Out-of-Scope-Anfragen, Fachberatungsanfragen, Förderzusagen-Fragen.
- Datenschutztests: sensible Felder werden nicht unnötig verarbeitet.
- Sicherheitstests: keine Rechteerweiterung möglich.

---

## 10. Offene Punkte

- Konkrete Prompt-Texte (ab Phase 3 in `prompts/`).
- Framework-/Laufzeitentscheidung (ADR).
- Konkrete Kontextpaket-Struktur (DATA_MODEL + ARCHITECTURE).
- Agentenlauf-Persistenz (DB).

---

## 11. Stand Run 1

- **Keine** Agenten implementiert.
- **Keine** Rollenverträge geschrieben.
- **Keine** Prompts angelegt.
- Dieser Text ist ausschließlich Rahmen und Regelwerk.
