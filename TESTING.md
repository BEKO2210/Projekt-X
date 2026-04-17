# TESTING.md — Teststrategie und Pflichtfälle (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Testinfrastruktur aktiv.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 24.

---

## 1. Grundsatz

Jede Funktion wird **vor** Produktivschaltung getestet. „Wir testen später" ist unzulässig. Ohne Tests kein Gate-Pass, ohne Gate-Pass kein Produktionseinsatz.

---

## 2. Teststufen (geplant)

- **Unit-Tests** — einzelne Funktionen, Agentenverhalten isoliert.
- **Integrationstests** — Zusammenspiel von Orchestrator, Agenten, Dokumenten, Export, Löschung.
- **End-to-End-Tests** — MVP-Kernflüsse (Projekt anlegen → Workflow → Dokument → Export/Löschung).
- **Datenschutztests** — Sensibilität, Modi, Kontextminimierung.
- **Sicherheitstests** — Zugriffskontrolle, Agentenrechte, Secrets-Scan.
- **Agentenverhaltenstests** — Positiv/Negativ, Prompt-Injection, Out-of-Scope.
- **Regressionstestliste** — wächst mit jeder neuen Funktion.
- **UI-Warnungstests** — Exportwarnung, Umgebungskennzeichnung, Sensibilitätshinweise.

---

## 3. Pflichtfälle MVP (Liste wächst je Phase)

### 3.1 Projektakte
- Projekt anlegen, Felder speichern, laden.
- Projekt löschen mit Bestätigung, Audit-Eintrag entsteht.
- Export Markdown, Warnung erscheint bei sensibler Daten.

### 3.2 Agenten
- Agent läuft nur mit gültigem Rollenvertrag.
- Agent versucht Out-of-Scope-Aktion → wird blockiert.
- Agent erhält nur minimiertes Kontextpaket.

### 3.3 Datenschutz
- Modus-Wechsel Standard ↔ Streng wirkt auf Kontext.
- Sensible Felder werden im strengen Modus nicht extern verarbeitet.
- Keine echten Daten in Dev/Test.

### 3.4 Sicherheit
- Kein Zugriff auf fremde Projekte.
- Kein Secret im Repository (automatischer Scan im CI, später).
- Agent kann Rechte nicht erweitern.

### 3.5 Dokumente
- Statusfelder funktionieren.
- Quellenstatus wird korrekt übernommen.
- Fachprüfungsstatus blockiert „freigegeben" bei offener Prüfung.

### 3.6 Kritische Aktionen
- Es gibt keine aktive kritische Außenaktion (MVP).
- Sollte eine auftauchen, bricht Test ab.

---

## 4. Testdaten

- Nur **synthetische** Daten in `testdata/`.
- Keine Klarnamen, keine realen Adressen/Telefonnummern/Mails.
- Testdaten sind dokumentiert (Herkunft, Zweck).

---

## 5. Testumgebung

- Produktionsnah (siehe `RELEASES.md`).
- Keine Außenwirkung.
- Getrennte Test-Secrets.
- Abweichungen zu Prod werden dokumentiert.

---

## 6. Testberichte

Jeder Run dokumentiert im Run-Bericht:

- welche Tests ausgeführt wurden,
- welche Tests als Testplan dokumentiert (aber nicht ausgeführt) wurden,
- welche Tests fehlgeschlagen sind,
- welche Lücken bestehen.

---

## 7. Offene Punkte

- Test-Framework-Entscheidung (ADR, Phase 1 oder später).
- CI-Pipeline-Setup (nach Techstack-ADR).
- Agentenverhaltens-Testing-Ansatz (Golden Sets, Szenarien).
- Regressionstestliste als Datei (Phase 8).

---

## 8. Stand Run 1

- **Keine** Tests aktiv.
- **Kein** Test-Framework gewählt.
- Pflicht für jeden weiteren Run: Testplan dokumentieren, auch wenn nicht ausführbar.
