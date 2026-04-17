# Run-Bericht: Run XXX — <Kurzname>

> Dateiname: `reports/run-XXX-<kurzname>.md`
> Pflichtlektüre vor Bearbeitung: `CLAUDE.md`, `MASTER_INDEX.md`, `MVP_SPEC.md`, `ROADMAP.md`, letzter Run-Bericht.

---

## 1. Ziel des Runs

Kurzbeschreibung, was dieser Run erreichen sollte (1–3 Sätze).

---

## 2. Gelesene Dateien

- `CLAUDE.md`
- `MASTER_INDEX.md`
- `MVP_SPEC.md`
- `ROADMAP.md`
- <weitere Dateien, die für diesen Run relevant waren>

Begründet nicht gelesene Dateien:

- <Datei>: <Grund>

---

## 3. Änderungen

Liste aller neuen, geänderten, gelöschten Dateien mit Kurzbegründung:

- **neu** `pfad/datei.md` — <Zweck>
- **geändert** `pfad/datei.md` — <Änderung>
- **gelöscht** `pfad/datei.md` — <Grund>

---

## 4. Datenschutzprüfung

- Neue Datenflüsse: <ja/nein + Beschreibung>
- Betroffene Sensibilität: <gering/mittel/hoch/sehr_hoch>
- Externe Verarbeitung: <ja/nein + Beschreibung>
- Nutzerkontrolle (Anzeigen, Export, Löschen) abgedeckt: <ja/nein>
- Datenminimierung eingehalten: <ja/nein>
- Ergebnis: <bestanden / offen / blockiert>

---

## 5. Sicherheitsprüfung

- Neue Rechte oder Zugänge: <ja/nein>
- Neue Angriffsflächen: <ja/nein>
- Secrets berührt: <ja/nein>
- Agentenrechte verändert: <ja/nein>
- Neue kritische Aktionen: <ja/nein>
- Ergebnis: <bestanden / offen / blockiert>

---

## 6. Quellenprüfung

- Werden fachrelevante Aussagen erzeugt? <ja/nein>
- Quellenstatus dokumentiert? <ja/nein>
- Aktualitätsmarker vorhanden? <ja/nein>
- Lizenz geklärt? <ja/nein/nicht relevant>
- Ergebnis: <bestanden / offen / blockiert / nicht relevant>

---

## 7. Fachprüfungsprüfung

- Aussagen mit Rechts-/Steuer-/Förder-/Medizin-Wirkung? <ja/nein>
- Fachprüfungsstatus gesetzt? <ja/nein>
- Ergebnis: <bestanden / offen / blockiert / nicht relevant>

---

## 8. Tests

- Ausgeführt: <Liste>
- Als Testplan dokumentiert (nicht ausführbar): <Liste + Grund>
- Fehlgeschlagen: <Liste + Ursache>
- Neue Regressionseinträge: <Liste>

---

## 9. Ergebnis

- Ziel erreicht: <vollständig / teilweise / nein>
- Begründung:
- Einstufung: <abgeschlossen / abgeschlossen mit Blockern / nicht abgeschlossen>

---

## 10. Offene Punkte

- <Punkt 1>
- <Punkt 2>

---

## 11. Blocker

- <Blocker 1 — Beschreibung, betroffene Dateien, vorgeschlagene Behebung>
- <Blocker 2 — …>

Wenn keine: „Keine Blocker."

---

## 12. Nächster Run

- **Run-Nummer:** <z. B. 002>
- **Geplanter Fokus:** <Kurzbeschreibung>
- **Der vollständige Run-Prompt steht am Ende dieses Berichts unter §13.**

---

## 13. Nächster Run-Prompt (Vorschlag)

> Wenn Blocker offen sind: **nur** Blocker-Prompt. Sonst: normaler Fortschritts-Prompt.
> Der Nutzer startet den nächsten Prompt ausdrücklich. Claude Code führt ihn nicht selbst aus.

```
# Nächster Run-Prompt: Run <N>

Lies zuerst CLAUDE.md, MASTER_INDEX.md, MVP_SPEC.md, ROADMAP.md und den letzten Run-Bericht.
Arbeite nur am Ziel dieses Runs: <Ziel>.
Führe folgende Aufgaben aus: <Aufgaben>.
Baue keine Funktionen außerhalb dieses Runs.
Nutze keine echten Daten und keine Secrets.
Prüfe Datenschutz, Sicherheit, Quellenpflicht und Fachprüfungsbedarf.
Erstelle oder aktualisiere Tests bzw. dokumentiere einen Testplan.
Aktualisiere die betroffene Dokumentation.
Schreibe reports/run-<NNN>-<name>.md.
Schreibe erst nach Abschluss dieses Runs den nächsten Prompt und führe ihn nicht selbst aus.
```
