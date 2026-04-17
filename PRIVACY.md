# PRIVACY.md — Datenschutzregeln und Datenlebenszyklus (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 6 und Teil 26.

---

## 1. Grundhaltung

Datenschutz ist **Produktmerkmal**, nicht Nachgedanke. Jede Funktion wird auf Datenschutzwirkung geprüft, **bevor** sie entworfen oder implementiert wird.

---

## 2. Grundprinzipien

### 2.1 Datenminimierung
Nur so viele Daten erheben, wie für den Zweck unbedingt nötig. Optionales bleibt optional.

### 2.2 Zweckbindung
Daten werden ausschließlich für den im Onboarding / in der Funktion angegebenen Zweck verwendet.

### 2.3 Nutzerkontrolle
Nutzer können:
- gespeicherte Daten einsehen,
- Projekte/Dokumente einzeln löschen,
- das gesamte Profil löschen,
- Datenschutzmodus wechseln,
- Export erzeugen.

### 2.4 Transparenz
Externe Verarbeitung (Modelle, Dienste) ist sichtbar gekennzeichnet. Kein verstecktes Weitergeben.

### 2.5 Keine echten Daten in Dev/Test
In Entwicklung und Test ausschließlich synthetische Daten. Kein Import aus Produktion.

---

## 3. Datenschutzmodi (MVP)

| Modus | Verhalten |
|---|---|
| **Standard** | Projektakte wird gespeichert. Agenten nutzen minimierten Kontext. Export und Löschung verfügbar. Externe Verarbeitung sichtbar. |
| **Streng** | Reduzierte Kontextweitergabe. Sensible Daten besonders markiert. Externe Verarbeitung sensibler Daten blockiert oder gewarnt. Vorsichtige Speicherung. Strengere Exportwarnung. |
| **Temporär (optional)** | Keine dauerhafte Speicherung oder stark reduziert. Export statt Langzeitspeicherung. Nur bei sauberer technischer Umsetzbarkeit. |

MVP unterstützt mindestens **Standard** und **Streng**.

---

## 4. Sensibilitätsstufen

- `gering` — allgemeine Projektbeschreibungen
- `mittel` — finanzielle Grobzahlen, Zielgruppenbeschreibung
- `hoch` — persönliche Umstände, Gesundheit, Familie, rechtliche Vorgänge
- `sehr_hoch` — IDs, Konten, Behördenaktenzeichen

Ab `hoch` gelten zusätzliche Schutzregeln: lokale Verarbeitung bevorzugt, strenger Modus empfohlen, Warnungen bei Export.

---

## 5. Datenlebenszyklus

1. **Erhebung** — nur mit Zweckangabe.
2. **Nutzung** — zweckgebunden, mit Agentenkontextminimierung.
3. **Speicherung** — nach gewähltem Modus.
4. **Export** — Nutzer-initiiert, mit Warnung und Audit-Eintrag.
5. **Löschung** — Nutzer-initiiert, mit Bestätigung und Audit-Eintrag.

Keine automatische Langzeitspeicherung ohne Nutzerentscheidung.

---

## 6. Agentenkontext

- Agenten erhalten **nur** die Daten, die sie für die aktuelle Aufgabe brauchen.
- Kein Agent erhält das gesamte Nutzerprofil pauschal.
- Sensible Felder werden im strengen Modus vor Agenten-Prompts maskiert oder ausgelassen.

---

## 7. Externe Verarbeitung

- Externe Modelle/Dienste: explizit benannt, Zweck benannt, alternative lokale Option prüfen.
- Keine stille Weitergabe.
- Bei Sensibilität `hoch` oder höher: externe Verarbeitung standardmäßig **blockiert** oder explizit bestätigungspflichtig.

---

## 8. Einwilligung und Widerruf

- Einwilligung nur für klar beschriebene Zwecke.
- Widerruf jederzeit möglich, führt zur Verarbeitungseinstellung.
- Einwilligungen werden im Profil dokumentiert.

---

## 9. Audit

- Export und Löschung erzeugen Audit-Log-Einträge.
- Audit-Logs enthalten keine unnötigen Klartextinhalte, nur Metadaten zum Vorgang.

---

## 10. Datenschutzprüfung (Pflichtschritt pro Run)

Jeder Run dokumentiert:

- welche neuen Datenflüsse vorgeschlagen werden,
- welche Sensibilität betroffen ist,
- ob externe Verarbeitung vorgeschlagen wird,
- ob Nutzerkontrolle (Anzeige, Export, Löschung) abgedeckt ist,
- ob Datenminimierung eingehalten wird.

---

## 11. Offene Punkte

- Formale DSGVO-Abbildung (Art. 13/14/15/17/20) in konkreten Texten.
- Auftragsverarbeitungsverträge mit etwaigen Dienstleistern (nicht vor Integration).
- Datenschutz-Folgenabschätzung (DSFA) pro Modul in späteren Phasen.
- Konkrete Löschfristen und automatische Lösch-/Aufbewahrungsregeln.

---

## 12. MVP-Mindestanforderungen

- Modi **Standard** und **Streng** wählbar.
- Export (Markdown) funktional.
- Löschung mit Bestätigung und Audit funktional.
- Agentenkontextminimierung aktiv.
- Externe Verarbeitung sichtbar.
- Keine echten Daten in Dev/Test.
