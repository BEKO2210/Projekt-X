# ADR-NNN — <Kurztitel der Entscheidung>

- **Datum:** YYYY-MM-DD
- **Status:** `vorgeschlagen` | `akzeptiert` | `abgelehnt` | `ersetzt-durch-ADR-NNN`
- **Autor:** <Name oder Rolle>
- **Betroffene Dokumente:** <Liste der Dateien, die diese ADR tangiert>
- **Run-Bezug:** <Run-Nummer, der diese ADR erzeugt hat>

---

## 1. Kontext

Was ist die Situation, die eine Entscheidung verlangt? Welches Problem soll gelöst werden? Welche Zwänge, Ziele, Randbedingungen gelten? Kurz und faktisch.

---

## 2. Entscheidung

**Was wird entschieden?** In einem oder zwei Sätzen.

Anschließend: wesentliche Eckpunkte, Umfang, ausdrückliche Grenzen.

---

## 3. Betrachtete Alternativen

| # | Alternative | Pro | Contra | Verworfen, weil … |
|---|---|---|---|---|
| 1 | <Alternative A> | … | … | … |
| 2 | <Alternative B> | … | … | … |
| 3 | <Alternative C> | … | … | … |

---

## 4. Konsequenzen

**Positiv (was diese Entscheidung ermöglicht):**

- …

**Negativ (was sie kostet oder einschränkt):**

- …

**Offene Folge-ADRs oder offene Fragen:**

- …

---

## 5. Pflichtprüfungen

Vor Akzeptanz zu prüfen (gemäß `CLAUDE.md` §6/§7/§8/§11/§17):

- [ ] **Datenschutzwirkung** geprüft (keine neuen sensiblen Datenflüsse ohne Rechtfertigung).
- [ ] **Sicherheitswirkung** geprüft (keine neuen Rechte, keine Secrets, keine kritische Aktion ohne Gate).
- [ ] **MVP-Scope** eingehalten (`MVP_SPEC.md`).
- [ ] **Fachberatungsgrenzen** eingehalten (`COMPLIANCE.md`).
- [ ] **Quellenpflicht** erfüllt, falls externe/fachliche Quelle zitiert (`SOURCES.md`).
- [ ] **Release-/Umgebungsregeln** nicht verletzt (`RELEASES.md`, `CLAUDE.md` §11/§17).
- [ ] **Tests/Testplan** sind für die Umsetzung dokumentiert (`TESTING.md`).

---

## 6. Umsetzungsplan (grob)

- **Schritte:** <nummerierte Liste, falls mehrstufig>
- **Betroffene Runs:** <welche künftigen Runs setzen diese ADR um>
- **Rollback-Strategie:** <wie wird die Entscheidung rückgängig gemacht, falls sich ein Fehler zeigt>

---

## 7. Referenzen

- Blueprint-Abschnitt: `KI_COMPANION_BLUEPRINT.md` §<Kapitel>
- Betroffene Dokumente: `<Datei>`
- Externe Quellen (mit Datum und Quellenstatus nach `SOURCES.md`): …

---

## Hinweis zur ADR-Pflege

- ADRs werden **nicht rückwirkend abgeschwächt**, sondern bei Bedarf durch eine neue ADR **ersetzt** (Status `ersetzt-durch-ADR-NNN`).
- Jede Änderung an einer akzeptierten ADR erfordert eine neue ADR.
- ADR-Dateinamen folgen dem Muster `ADR-NNN-<kurztitel>.md` (dreistellige, fortlaufende Nummer).
