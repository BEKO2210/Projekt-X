# SECURITY.md — Sicherheit, Zugriff, Secrets, Agentenrechte (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 7 und Teil 22.

---

## 1. Grundhaltung

Sicherheit ist **dauerhafter Prozess**, nicht einmalige Prüfung. Jede Funktion wird auf Sicherheitsrisiken geprüft, bevor sie gebaut wird.

---

## 2. Kernprinzipien

- **Least Privilege:** Jeder Akteur (Nutzer, Agent, Prozess) erhält nur die Rechte, die er für seine Aufgabe braucht.
- **Defense in Depth:** Mehrere Schutzschichten, nicht eine einzige.
- **Kein Secret im Code:** Secrets nur aus kontrollierten Quellen.
- **Trennung der Umgebungen:** Dev, Test, Prod strikt getrennt.
- **Audit statt Vertrauen:** Kritische Aktionen werden geloggt.

---

## 3. Secrets

- **Verboten im Repository:** API-Keys, Passwörter, Tokens, Private Keys, Zertifikate, Produktiv-Credentials, `.env`-Werte mit Realwerten.
- **Erlaubt:** Dokumentierte Platzhalter (`<API_KEY>`, `change_me`), ohne echte Werte.
- **Produktion:** Secrets werden erst bei Bedarf über sichere Quellen (Secret Manager, CI Secrets) eingespielt — **nicht** in Run 1.
- **Rotations- und Entzugsregeln:** in späteren Runs (SECURITY-ADR).

---

## 4. Zugriffskontrolle

### 4.1 Nutzerzugriff
- Ein Nutzer sieht nur eigene Daten.
- Kein pauschaler Admin-Zugriff auf Nutzerprojekte.
- Mandantentrennung konzeptionell vorgesehen, Umsetzung folgt in Phase 1.

### 4.2 Agentenzugriff
- Agenten haben **keine** eigenen Rechte über ihren Rollenvertrag hinaus.
- Agenten können Rechte **nicht** selbst erweitern.
- Agenten greifen nur auf Kontextpakete zu, nicht auf das vollständige Profil.

### 4.3 Externe Dienste
- Kein externer Dienst erhält Zugriff ohne dokumentiertes Integrations-Gate.
- Im MVP: keine externen Dienste aktiv.

---

## 5. Agentenrechte (MVP)

| Bereich | Erlaubt | Verboten |
|---|---|---|
| Textverarbeitung | Entwürfe erzeugen, strukturieren, markieren | echten Versand, Bestätigung, Freigabe |
| Datenzugriff | minimiertes Kontextpaket | vollständiges Profil, andere Projekte |
| Aktionen | Vorschläge erzeugen | kritische Aktionen autonom ausführen |
| Eskalation | Risiken, Widersprüche markieren | eigenständig Entscheidungen treffen |

---

## 6. Kritische Aktionen (Definition)

Kritisch ist jede Aktion mit Außenwirkung oder irreversiblen Folgen:

- Versand einer Nachricht / E-Mail
- Einreichung bei Behörden
- Zahlungsauslösung
- Vertragsabschluss
- Veröffentlichung
- Massenhafte Datenverarbeitung
- Löschungen auf Produktionsdaten
- Rechte-Änderungen

Im MVP: **keine** dieser Aktionen automatisiert oder aktiviert. In späteren Phasen nur mit Human-in-the-loop.

---

## 7. Missbrauchsschutz

- Eingabefilter für Prompt-Injection (in Phase 3+ zu detaillieren).
- Rate-Limits (in Phase 8).
- Erkennung von Datenabfluss-Versuchen (Monitoring, Phase 8).
- Schutz vor automatisierten Agenten-Eigenmächtigkeiten über Rollenverträge.

---

## 8. Umgebungen

- **Dev:** Mocks erlaubt, keine echten Secrets, keine Produktionsdaten, keine Außenwirkung.
- **Test:** produktionsnah, synthetische Daten, Test-Secrets getrennt, keine Außenwirkung.
- **Prod:** echte Daten möglich, strenge Gates, keine Dev/Test-Artefakte aktiv.

Abweichungen zwischen Test und Prod werden in `RELEASES.md` dokumentiert.

---

## 9. Sicherheitsprüfung (Pflichtschritt pro Run)

Jeder Run dokumentiert:

- welche Rechte neu vergeben werden,
- welche Angriffsflächen neu entstehen,
- ob Secrets oder Zugänge berührt werden,
- ob Agentenrechte verändert werden,
- ob kritische Aktionen neu ermöglicht werden.

---

## 10. Incident-Grundsatz

- Jeder Sicherheitsvorfall erhält einen Bericht in `incidents/`.
- Sofortmaßnahme: Funktion deaktivieren, nicht „weiterbetreiben mit Bitte um Vorsicht".
- Post-Mortem wird geschrieben, Lernpunkte in `CLAUDE.md` aufgenommen, wenn nötig.

---

## 11. Offene Punkte

- Konkrete Auth-Methode (wird ADR).
- Mandantentrennung in Datenbank (Phase 1).
- Verschlüsselung at-rest und in-transit (ADR).
- Logging-Strategie mit Datenschutzrücksicht (in `MONITORING.md` zu detaillieren).
- Threat-Model für Agentenebene.

---

## 12. MVP-Mindestanforderungen

- Keine Secrets im Repo.
- Keine Agenten ohne Rollenvertrag.
- Keine kritischen Aktionen aktiv.
- Zugriff auf eigene Daten begrenzt.
- Umgebungen sichtbar gekennzeichnet.
- Audit-Logs für Export und Löschung.
