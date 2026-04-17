# RELEASES.md — Umgebungen, Gates, Rollback, Hotfix (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Deployments. Keine Produktion.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 3 und Teil 20.

---

## 1. Drei-Stufen-System

Jede Änderung durchläuft verbindlich drei Umgebungen:

1. **Entwicklung (Dev)** — synthetische Daten, Mocks erlaubt, keine Außenwirkung.
2. **Test** — produktionsnah, synthetische Daten, keine Außenwirkung, getrennte Test-Secrets.
3. **Produktion (Prod)** — echte Daten möglich, strenge Gates, keine Dev/Test-Artefakte aktiv.

Kein Sprung **Dev → Prod** ohne Testumgebung.

---

## 2. Identität und Kennzeichnung

- Jede Umgebung ist in der UI sichtbar gekennzeichnet (Badge/Label).
- Umgebungsvariable entscheidet Verhalten (keine Konstanten im Code).
- Logs, Exporte und Fehler tragen Umgebungsmerkmal.

---

## 3. Gates

### 3.1 Dev → Test (Dev-to-Test-Freigabe)
Formular mit mindestens:

- Funktion, Kurzbeschreibung, Zweck, Nutzerwert
- Scope, Nicht-Ziele, beteiligte Module, beteiligte Agenten
- Datenfluss, personenbezogene Daten, sensible Daten
- Externe Dienste, Datenschutzrisiken, Sicherheitsrisiken
- Quellenbedarf, kritische Aktionen
- Feature Flags, Testfälle, Fehlerfälle
- bekannte Einschränkungen, offene Fragen
- Freigabestatus + Begründung

### 3.2 Test → Prod (Test-to-Production-Freigabe)
Zusätzlich geprüft:

- Teststatus bestanden
- Datenschutzprüfung geprüft
- Sicherheitsprüfung geprüft
- Agentenrechte geprüft
- Rollenrechte geprüft
- externe Dienste geprüft
- Quellenprüfung geprüft
- Löschfunktion geprüft
- Exportfunktion geprüft
- Audit-Logs geprüft
- kritische Aktionen geprüft
- Feature Flags geprüft
- keine Dev-Only-Komponenten aktiv
- keine Mock-Daten aktiv
- keine Dummy-Agenten aktiv
- keine Test-API-Schlüssel aktiv
- Rückrollplan
- offene Risiken

---

## 4. Rollback

- Jedes Prod-Release enthält einen dokumentierten Rückrollplan.
- Rollback ist bevorzugt gegenüber Hotfix-Forcierung.
- Nach Rollback: Incident-Bericht in `incidents/`.

---

## 5. Hotfix

- Nur für kritische Sicherheits-/Datenschutzvorfälle.
- Auch Hotfix muss Test-Umgebung durchlaufen (Smoke-Test minimum).
- Keine Hotfix-Pipeline, die Gates umgeht.

---

## 6. Feature Flags

- Jede neue Funktion startet hinter einem Flag.
- Flags werden zentral verwaltet (Phase 1+).
- Entfernung eines Flags nach vollständigem Rollout dokumentiert.

---

## 7. Secrets über Umgebungen

- Dev: keine echten Secrets; Platzhalter.
- Test: getrennte Test-Secrets, nie Produktionswerte.
- Prod: Secrets nur aus Secret Manager / CI Secrets (später).

---

## 8. Versionierung

- Semantische Versionierung der Dokumente (z. B. MVP-Spec).
- Releases in `releases/` dokumentiert mit Datum, Inhalten, Gate-Ergebnissen.
- Branch-Modell folgt in ADR.

---

## 9. Produktionsblocker (Auswahl, siehe `MASTER_INDEX.md` §7)

- Echte Nutzerdaten außerhalb Produktion.
- Secrets im Repo.
- Fehlende Löschfunktion.
- Fehlender Export.
- Agenten ohne Rollenvertrag aktiv.
- Kritische Aktionen ohne Human-in-the-loop.
- Integrationen mit Außenwirkung ohne Gate.
- Datenschutz-/Sicherheitsprüfung nicht bestanden.
- Tests fehlen / schlagen fehl.
- Dev-Only-Artefakte aktiv.

Ein einziger offener Blocker verhindert das Prod-Release.

---

## 10. Offene Punkte

- Konkrete Branch- und Deployment-Strategie (ADR).
- CI/CD-Pipeline (nach Techstack-ADR).
- Feature-Flag-Framework (ADR).
- Rollback-Mechanik (abhängig von Persistenz-Wahl).

---

## 11. Stand Run 1

- **Keine** Umgebungen existieren.
- **Keine** Releases.
- Dieser Text dokumentiert Regeln für alle späteren Phasen.
