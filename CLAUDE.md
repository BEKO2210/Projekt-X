# CLAUDE.md — Arbeitsvertrag für Claude Code

> **Status:** Konzept- und Architekturphase. Diese Datei ist oberste Projektregel für jeden Claude-Code-Run.
> Bei Widersprüchen zwischen einem Run-Prompt und diesem Dokument hat **CLAUDE.md Vorrang**, bis der Widerspruch explizit aufgelöst ist.

---

## 1. Harte, nicht verhandelbare Regeln

Diese Regeln gelten in jedem Run, jeder Phase, jeder Umgebung.

### 1.1 Datenschutz zuerst
- Kein Run darf echte personenbezogene Daten einführen, verarbeiten oder speichern.
- Jede neue Funktion muss auf Datenschutzrisiken geprüft werden, bevor sie dokumentiert oder (später) implementiert wird.
- Datenminimierung, Zweckbindung, Nutzerkontrolle und Löschbarkeit sind Pflichtmerkmale, keine Features.

### 1.2 Sicherheit zuerst
- Kein Run darf Secrets, API-Schlüssel, Zugangsdaten, Tokens oder Produktiv-Credentials einführen.
- Jede neue Funktion muss auf Sicherheitsrisiken (Zugriffskontrolle, Missbrauch, Agentenrechte) geprüft werden.
- Unsicherer Code, der „schnell mal" etwas freischaltet, ist verboten.

### 1.3 MVP-Scope einhalten
- Claude Code baut nur, was die MVP-Spezifikation (`MVP_SPEC.md`) explizit erlaubt.
- Funktionen außerhalb des MVP sind in späteren Roadmap-Phasen dokumentiert, aber **nicht** vorzuziehen.
- Wenn ein Run-Prompt MVP-Grenzen verletzt, wird der Widerspruch sichtbar gemacht, nicht ignoriert.

### 1.4 Keine echten Daten in Development oder Test
- In `testdata/`, `examples/`, Prompts, Fixtures, Mocks: **ausschließlich synthetische Daten**.
- Keine Klarnamen, keine echten Adressen, keine echten Steuer-IDs, keine echten E-Mail-Adressen, keine echten Telefonnummern.
- Erkennt Claude Code echte Daten im Repo, ist das sofort ein **Blocker**.

### 1.5 Keine Secrets
- Keine API-Keys, Passwörter, Private Keys, Access Tokens, `.env`-Werte oder Zugangsdaten im Repo.
- Kein Commit solcher Werte, auch nicht als Beispiel.
- Secret-Vorlagen gehören in dokumentierte Platzhalter (`<API_KEY>`, `change_me`).

### 1.6 Keine Fachberatung vortäuschen
- Das System darf sich nie als Anwalt, Steuerberater, Arzt, Therapeut, Bankberater, Finanzberater, Behörde oder offizielle Fachstelle darstellen.
- Dokumente, Prompts und UI-Texte müssen diese Grenze deutlich machen.

### 1.7 Keine Rechts- oder Steuerberatung
- Ausgaben des Systems zu Recht, Steuern, Sozialversicherung, Fördermitteln, Verträgen und Meldepflichten sind **Entwurf/Orientierung**, nie rechtsverbindlich.
- Fachprüfungspflicht muss sichtbar gemacht werden (`fachpruefung_erforderlich`).

### 1.8 Keine Fördergarantie
- Das System darf keine Förderzusage, keine Erfolgsquote, keine „sichere" Bewilligung in Aussicht stellen.
- Förderinformationen erhalten immer einen Quellenstatus (`quelle_geprueft`, `quelle_veraltet`, `quelle_unklar`).

### 1.9 Keine kritische Außenwirkung im MVP
- Kein automatisches Senden von E-Mails, Nachrichten, Anträgen, Zahlungen, Buchungen.
- Keine automatische Kalenderpflege, keine automatischen Social-Media-Posts, keine Behördeneinreichungen.
- Agenten bereiten vor — Menschen entscheiden.

### 1.10 Keine Integrationen ohne Gate
- Jede externe Integration (API, Dienst, Drittanbieter) benötigt vor Aktivierung ein dokumentiertes Gate mit Datenschutz-, Sicherheits- und Fachprüfungsentscheidung.
- Kein „mal kurz anbinden".

### 1.11 Keine Agenten ohne Rollenvertrag
- Jeder Agent benötigt eine Rollenbeschreibung mit Scope, erlaubten Aktionen, verbotenen Aktionen, Datenzugriff, Eskalationspfad.
- Ohne Rollenvertrag kein Agentenbetrieb.

### 1.12 Keine Produktion ohne Test-Gate
- Kein Übergang Dev → Prod ohne durchlaufene Testumgebung und dokumentiertes Test-to-Production-Gate.
- Dev-Only-Komponenten, Mocks, Dummy-Agenten, Test-API-Schlüssel dürfen nie aktiv in Produktion sein.

### 1.13 Tests und Dokumentation verpflichtend
- Jeder Run erstellt oder aktualisiert Tests bzw. einen Testplan.
- Jeder Run aktualisiert die betroffene Dokumentation.
- Jeder Run erzeugt einen Run-Bericht in `reports/run-XXX-<name>.md`.

---

## 2. Run-Ablauf

Jeder Claude-Code-Run folgt verbindlich diesem Ablauf (siehe Blueprint 40.11):

1. Aktuellen Run-Prompt lesen.
2. `CLAUDE.md` lesen.
3. `MASTER_INDEX.md` lesen (falls vorhanden).
4. `MVP_SPEC.md` lesen.
5. `ROADMAP.md` lesen.
6. Betroffene Spezifikationen und Dokumente lesen.
7. Vorhandene Dateien prüfen, nicht blind überschreiben.
8. Scope des Runs begrenzen.
9. Datenschutzrisiken prüfen.
10. Sicherheitsrisiken prüfen.
11. Quellenpflicht prüfen.
12. Fachprüfungsbedarf prüfen.
13. Änderungen durchführen.
14. Tests erstellen oder Testplan dokumentieren.
15. Tests ausführen, wenn technisch möglich.
16. Dokumentation aktualisieren.
17. Run-Bericht schreiben.
18. Ergebnis gegen Ziel prüfen.
19. Offene Punkte und Blocker dokumentieren.
20. Erst danach den nächsten Run-Prompt schreiben.
21. Nächsten Run-Prompt **nicht selbst ausführen**.
22. Auf ausdrücklichen Start warten.

---

## 3. Selbststeuerung

- Nur Run 1 wird extern vorgegeben.
- Ab Run 2 schreibt Claude Code den nächsten Prompt selbst — **aber erst nach Abschluss** des laufenden Runs.
- Claude Code darf **keine** automatische Prompt-Kette starten.
- Jeder nächste Prompt ist ein **Vorschlag**, den der Nutzer ausdrücklich startet.

---

## 4. Blocker-Regel

Wenn einer der folgenden Punkte offen ist, darf **kein normaler Fortschritts-Prompt** geschrieben werden:

- offener Datenschutzblocker
- offener Sicherheitsblocker
- echte Daten im Repo gefunden
- Secrets im Repo gefunden
- widersprüchliche Dokumentation
- unklarer MVP-Scope
- `CLAUDE.md` fehlt oder zu schwach
- unklare Zugriffskontrolle
- fehlende Teststrategie
- offene Produktionsblocker
- vorheriger Run nicht dokumentiert
- wichtige Dateien fehlen
- Run-Ziel nicht abgeschlossen

In diesen Fällen schreibt Claude Code einen **Blocker-Prompt**, der ausschließlich die Blockerbehebung behandelt.

---

## 5. Was Claude Code **nicht** tun darf

- Run 1–10 automatisch durchlaufen.
- Mehrere Run-Prompts gleichzeitig schreiben und ausführen.
- Den nächsten Prompt ausführen, ohne dass der Nutzer startet.
- Blocker ignorieren und weitermachen.
- Nach unvollständigem Run einen normalen Fortschritts-Prompt schreiben.
- Spätere Roadmap-Phasen vorziehen.
- Code bauen, wenn Dokumentation dran ist.
- UI bauen, wenn Datenmodell unklar ist.
- Agenten bauen, wenn Rollenverträge fehlen.
- Integrationen bauen, wenn Gates fehlen.
- Techstack eigenmächtig wählen (erfordert ADR in `decisions/`).
- Echte Daten, Secrets oder Produktivzugänge einführen.

---

## 6. Grundhaltung

- Sachlich, respektvoll, vorsichtig, praktisch, realistisch.
- Keine Überautomatisierung, kein Versprechen, was das System nicht halten kann.
- Human-in-the-loop bei allen Entscheidungen mit Außenwirkung.
- Transparenz über Status, Quellen, Unsicherheiten und Grenzen.
- Begründen statt behaupten.

---

## 7. Quellendokumente

- Verfassung: `KI_COMPANION_BLUEPRINT.md` (Masterdokument, oberste Projektregel).
- Index: `MASTER_INDEX.md`.
- MVP-Grenze: `MVP_SPEC.md`.
- Phasen: `ROADMAP.md`.
- Freigabe- und Umgebungsregeln: `RELEASES.md`.
- Privatsphäre/Sicherheit/Compliance: `PRIVACY.md`, `SECURITY.md`, `COMPLIANCE.md`.

Bei Widersprüchen zwischen diesen Dokumenten gilt: Erst Blueprint, dann CLAUDE.md, dann MVP_SPEC.md, dann Detaildokumente. Widersprüche sind sichtbar zu machen, nicht stillschweigend aufzulösen.
