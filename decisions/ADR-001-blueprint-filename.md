# ADR-001 — Dateiname der Projektverfassung

- **Datum:** 2026-04-17
- **Status:** akzeptiert
- **Autor:** Claude Code (Run 2) im Auftrag des Projektinhabers
- **Betroffene Dokumente:** `KI_COMPANION_BLUEPRINT.md`, `README.md`, `CLAUDE.md`, `MASTER_INDEX.md`, alle Run-Prompts
- **Run-Bezug:** Run 2 (Vertiefung Kerndokumentation)

---

## 1. Kontext

Die Projektverfassung liegt im Repository als `KI_COMPANION_BLUEPRINT.md`. In Run 1 und frühen Arbeitsprompten wurde die Datei teilweise auch als „PROJECT_BLUEPRINT.md" referenziert (z. B. im Run-1-Startprompt). Dies kann zu Fehlinterpretationen oder fehlschlagenden Verweisen führen, wenn Claude Code oder Menschen nach der Datei unter einem nicht existierenden Namen suchen.

Im Ordner existiert aktuell nur eine Datei: `KI_COMPANION_BLUEPRINT.md`. Keine zweite Verfassungsdatei. Kein Inhalt ist verloren oder dupliziert.

---

## 2. Entscheidung

**Der verbindliche Dateiname der Projektverfassung ist `KI_COMPANION_BLUEPRINT.md`.**

Eckpunkte:

- Alle Dokumente und künftigen Run-Prompts referenzieren ausschließlich `KI_COMPANION_BLUEPRINT.md`.
- Der Begriff „Blueprint" (ohne Dateinamen) bleibt als Kurzform zulässig.
- Die Bezeichnung „PROJECT_BLUEPRINT.md" wird **nicht** als Datei oder Alias eingeführt.
- Erwähnungen von „PROJECT_BLUEPRINT.md" in älteren Run-Prompten oder Notizen werden als historisch und synonym interpretiert, aber nicht kopiert oder übernommen.
- Bestehende Dateien werden **nicht** umbenannt, um keine Git-History-Brüche und keine Link-Brüche zu erzeugen.

---

## 3. Betrachtete Alternativen

| # | Alternative | Pro | Contra | Verworfen, weil … |
|---|---|---|---|---|
| 1 | Umbenennung zu `PROJECT_BLUEPRINT.md` | vereinheitlicht künftige Prompts | bricht bestehende Links, Git-History-Referenzen, externe Lesezeichen; 1,1 MB-Datei müsste neu indiziert werden | Risiko ohne Nutzen; Bestand ist stabil |
| 2 | Symlink `PROJECT_BLUEPRINT.md` → `KI_COMPANION_BLUEPRINT.md` | beide Namen funktionieren | Plattformabhängigkeit (Windows-Inkonsistenz), Verdopplung in Suche, Verwirrung | erzeugt zwei scheinbare Quellen der Wahrheit |
| 3 | Kopie unter `PROJECT_BLUEPRINT.md` | Kompatibilität mit Altprompts | zwei Wahrheiten, Drift-Risiko, 1,1 MB doppelt | verletzt Single-Source-of-Truth-Prinzip |
| 4 | **Beibehalten von `KI_COMPANION_BLUEPRINT.md` als einzige Quelle** | klar, konsistent, kein Risiko, Git-History bleibt | künftige Run-Prompts müssen den korrekten Namen nutzen | **gewählt** |

---

## 4. Konsequenzen

**Positiv:**

- Eine einzige, unverwechselbare Quelle der Projektverfassung.
- Keine Link-Brüche in bestehenden Commits und Dokumenten.
- Keine Duplikation einer 1,1 MB-Datei.

**Negativ:**

- Run-Prompts, die „PROJECT_BLUEPRINT.md" referenzieren, müssen mental umgedeutet werden. Lösung: `MASTER_INDEX.md` und `CLAUDE.md` nennen den korrekten Namen prominent.
- Externe Dokumentation außerhalb dieses Repositories (falls vorhanden) muss ggf. nachgezogen werden.

**Offene Folge-ADRs:** keine.

---

## 5. Pflichtprüfungen

- [x] **Datenschutzwirkung** geprüft — keine (reine Metadatenentscheidung).
- [x] **Sicherheitswirkung** geprüft — keine.
- [x] **MVP-Scope** eingehalten — Dokumentationsentscheidung, außerhalb MVP-Code.
- [x] **Fachberatungsgrenzen** eingehalten — nicht berührt.
- [x] **Quellenpflicht** — interne Quelle (Blueprint selbst), keine externe Quelle benötigt.
- [x] **Release-/Umgebungsregeln** — nicht berührt.
- [x] **Tests/Testplan** — manuelle Prüfung: Grep nach „PROJECT_BLUEPRINT" im Repo zeigt erwartbare Treffer (ältere Run-Prompts, diese ADR). Keine Codeänderungen nötig.

---

## 6. Umsetzungsplan

- **Schritt 1:** Diese ADR ablegen (erledigt mit diesem Commit).
- **Schritt 2:** `MASTER_INDEX.md` aktualisieren, dass `KI_COMPANION_BLUEPRINT.md` der verbindliche Name ist (Run 2).
- **Schritt 3:** Künftige Run-Prompts nutzen den korrekten Namen.
- **Rollback-Strategie:** Falls später ein anderer Name gewünscht ist, wird eine neue ADR geschrieben, die diese ersetzt (`ersetzt-durch-ADR-NNN`). Umbenennung erfolgt dann mit dokumentierter Link-Aktualisierung.

---

## 7. Referenzen

- Verfassung: `KI_COMPANION_BLUEPRINT.md`
- Prompt-Bezug: `reports/run-001-foundation.md` §10 Punkt 4 (Namensinkonsistenz)
- Vorlage: `decisions/ADR-template.md`
