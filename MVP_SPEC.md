# MVP_SPEC.md — Verbindliche MVP-Grenze

> **Status:** Entwurf (Phase 0). Der MVP ist **nicht implementiert**. Dieses Dokument beschreibt den späteren MVP-Umfang und dient als Leitplanke für alle Runs.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 35.

---

## 1. Kernversprechen

Ein Nutzer kann:

1. eine berufliche oder unternehmerische Ausgangslage erfassen,
2. ein Projekt anlegen,
3. seine Idee strukturieren,
4. Risiken erkennen,
5. Aufgaben ableiten,
6. erste Dokumente als **Entwurf** erzeugen,
7. Quellenbedarf sehen,
8. Datenschutzstatus verstehen,
9. das Ergebnis exportieren oder löschen.

Der MVP hilft beim **Denken, Strukturieren, Planen und Vorbereiten**. Der MVP führt **keine kritischen Außenaktionen** aus.

---

## 2. Zielnutzer

Primäre Nutzergruppen:

- Menschen mit Geschäftsidee
- Menschen ohne klare Idee, aber Neuorientierungswunsch
- nebenberufliche Gründer
- Menschen in beruflicher Neuorientierung
- Menschen, die Selbstständigkeit prüfen wollen
- kleine Einzelunternehmer in früher Phase
- Menschen, die KI sinnvoll für ein kleines Vorhaben nutzen wollen

**Nicht** primär MVP: große Unternehmen, Behörden, komplexe Teams, Steuerkanzleien, Rechtskanzleien, Enterprise, internationale Multi-Länder-Nutzung.

---

## 3. Erlaubte MVP-Funktionen

- Startseite / Einstieg
- Onboarding light
- Datenschutzmodus basic (mind. **Standard** und **Streng**)
- Projekt anlegen
- Projektakte
- Projekt-Dashboard
- CEO-Orchestrator basic
- begrenzte Kernagenten (siehe §5)
- Aufgabenliste
- Risikoübersicht light
- Workflows light
- Dokumentenzentrum
- Dokumente als Entwurf (mit Status)
- Quellenstatus light
- Fachprüfungsstatus light
- Finanzplan light
- Mini-Businessplan
- MVP-Plan
- Datenschutz-Basischeck
- Export als Markdown, optional JSON
- Projektlöschung
- Einfache Audit-Logs für Export und Löschung
- Entwicklungs-/Test-/Produktionsumgebung
- Feature Flags basic
- Basis-Tests
- Run- und Release-Dokumentation

---

## 4. Nicht erlaubte MVP-Funktionen

- Echte E-Mail-Automation
- Echte Kalenderautomation
- Zahlungen, Bankintegration
- Behördeneinreichung
- Automatische Social-Media-Posts
- Automatische CRM-Aktionen
- Automatische Vertragsfinalisierung
- Verbindliche Rechts- oder Steuerberatung
- Fördergarantien
- Vollständiges CRM
- Buchhaltungssystem
- Enterprise-Teamrollen
- Internationale Rechtslogik
- RAG mit ungeprüften Fachquellen
- Lizenzierte Fachdatenbanken ohne Lizenz
- Kreditberatung
- Automatische Kundenkommunikation mit Versand

---

## 5. Kernagenten (MVP)

Alle MVP-Agenten arbeiten **vorbereitend, nicht autonom handelnd**. Keine echten externen Aktionen.

| Agent | Aufgabe |
|---|---|
| CEO-Orchestrator basic | Koordination, nächste Schritte, Widerspruchs- und Risiko-Erkennung. |
| Orientierungs-Agent | Ziel, Ausgangslage, Richtung klären. |
| Gründungs-Agent light | Idee, Angebot, Zielgruppe, erste Schritte strukturieren. |
| Finanz-Agent light | Kosten, Einnahmenannahmen, Szenarien, Risikoampel. |
| Datenschutz-Agent light | Datenarten, Datenschutzmodus, externe Verarbeitung, Sensibilität. |
| Dokumenten-Agent | Entwürfe mit Status erzeugen. |
| Quellenstatus-Agent light | Quellenbedarf, Aktualitätsbedarf, nicht entscheidungsreife Aussagen. |
| Qualitäts-Agent | Prüft Entwürfe auf falsche Sicherheit, fehlende Quellen, Risiken, Fachprüfungsbedarf. |

Agenten dürfen nicht: E-Mails senden, Termine erstellen, Zahlungen auslösen, Verträge final freigeben, Steuer- oder Rechtsberatung geben, Förderungen garantieren, Nutzer zur Kreditaufnahme drängen, CRM-Aktionen ausführen, Social-Media-Posts veröffentlichen, Agentenrechte selbst erweitern, Produktionsregeln umgehen.

---

## 6. Workflows (MVP)

- Workflow: Startorientierung
- Workflow: Idee validieren
- Workflow: Mini-Businessplan
- Workflow: MVP planen
- Workflow: Datenschutz-Basischeck
- Workflow: Finanzplan light
- Workflow: erste Kundenansprache als Entwurf (ohne Versand)
- Pausieren und Fortsetzen
- Abbruchkriterien

---

## 7. Dokumenttypen (MVP)

- Mini-Businessplan
- Finanzplan light
- MVP-Plan
- Datenschutz-Basischeck
- Fördercheck light (nur mit Quellenstatus)
- Angebotsentwurf
- E-Mail-Entwurf (ohne Versand)

Jedes Dokument trägt: Entwurfsstatus, Abschnittsstatus, Quellenstatus, Fachprüfungsstatus, Exportwarnung, Versionierung basic.

---

## 8. Export und Löschung

- **Export:** Markdown zwingend, JSON optional. Warnung bei sensiblen Daten. Audit-Log-Eintrag bei Export.
- **Löschung:** Nutzer kann Projekt und Dokumente löschen, mit Bestätigung. Audit-Log-Eintrag bei Löschung.
- **Datenzugang:** Nutzer kann gespeicherte Daten anzeigen.

---

## 9. Datenschutzmodus

Mindestens unterstützt:

- **Standard:** Projektakte wird gespeichert, Agenten nutzen minimierten Kontext, Export und Löschung verfügbar, externe Verarbeitung sichtbar.
- **Streng:** weniger Kontextweitergabe, sensible Daten markiert, externe Verarbeitung sensibler Daten blockiert oder gewarnt, vorsichtige Speicherung, strengere Exportwarnungen.

Optional (nur wenn technisch sauber): **Temporär** — keine dauerhafte Speicherung.

---

## 10. Abnahmekriterien

Der MVP gilt als aufnahmefähig, wenn:

1. Ein Nutzer kann Projekt anlegen, Ziel erfassen, Aufgaben sehen.
2. CEO-Orchestrator basic schlägt sinnvolle nächste Schritte vor.
3. Kernagenten erzeugen Aufgaben, Risiken, Entwürfe — ohne externe Aktion.
4. Dokumente tragen sichtbaren Status (Entwurf, Quellenstatus, Fachprüfungsstatus).
5. Datenschutzmodus **Standard** und **Streng** wählbar.
6. Export (Markdown) funktioniert, mit Exportwarnung.
7. Löschung funktioniert, mit Bestätigung und Audit-Log.
8. UI zeigt Umgebung (Dev/Test/Prod) sichtbar.
9. Tests für MVP-Kernflüsse bestehen.
10. Datenschutz-Gate, Sicherheits-Gate, Test-to-Production-Gate dokumentiert.
11. Produktionsblocker aus `MASTER_INDEX.md` §7 geschlossen.

---

## 11. Stand dieses Dokuments

- **Reifegrad:** Konzept/Entwurf.
- **Implementierung:** nicht vorhanden.
- **Techstack:** nicht entschieden.
- **Nächste Vertiefung:** in Run 2 geplant (siehe `reports/run-001-foundation.md`).
