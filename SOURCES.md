# SOURCES.md — Quellenstatus, Aktualität, Lizenz (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung, keine aktiven Quellen.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 8 und Teil 27.

---

## 1. Grundsatz

Veränderliches Wissen (Recht, Steuern, Förderung, Sozialversicherung, Behördenverfahren, wirtschaftliche Rahmen) unterliegt einer **Quellenpflicht**. Aussagen ohne Quelle werden entweder als „nicht entscheidungsreif" markiert oder nicht ausgegeben.

---

## 2. Quellenstatus (verbindliche Skala)

- `quelle_fehlt` — Aussage ohne Beleg. Darf nicht als Grundlage für Nutzerentscheidungen dienen.
- `quelle_unklar` — Quelle benannt, aber nicht ausreichend verifiziert.
- `quelle_veraltet` — Quelle vorhanden, aber nicht aktuell genug.
- `quelle_geprueft` — aktuelle, vertrauenswürdige Quelle mit Datum.

MVP-Grenze: Ausgaben mit Fachwirkung setzen mindestens `quelle_geprueft` **oder** tragen sichtbaren Status-Hinweis mit Empfehlung zur Fachprüfung.

---

## 3. Aktualitätsmarker

- **Datum der Prüfung** pro Quelle.
- **Gültigkeit bis / Prüfintervall** (für Förderprogramme, Gesetze).
- **Letzte automatische/manuelle Prüfung**.
- Quellen werden periodisch re-verifiziert (Phase 8+).

---

## 4. Lizenzstatus

- Nur Quellen nutzen, deren Lizenz bekannt und erlaubt ist.
- Lizenzpflichtige Fachdatenbanken sind **nicht** Teil des MVP.
- Zitate nur im zulässigen Umfang. Kein Pseudo-Zitieren ohne Herkunftsangabe.

---

## 5. RAG-Grenzen

- **Kein** RAG mit ungeprüften Fachquellen im MVP.
- Optionaler RAG-Ausbau in Phase 14 (mit Quellenprüfung und Lizenzklärung).
- Keine stillschweigende Anreicherung von Agentenantworten aus ungeprüften Quellen.

---

## 6. Fachgebiete und Risikoprofil

| Fachgebiet | Änderungsrate | MVP-Behandlung |
|---|---|---|
| Rechtsgrundlagen (Gewerbe, Verträge) | hoch | nur mit Quellenstatus + Fachprüfungsempfehlung |
| Steuerrecht | hoch | kein verbindliches Ergebnis, nur Orientierung |
| Förderprogramme | sehr hoch | mit Quellenstatus, keine Garantie |
| Sozialversicherung | mittel–hoch | mit Quellenstatus |
| Behördenverfahren | mittel | beschreibend, keine Einreichung |
| allgemeine Unternehmerpraxis | gering–mittel | mit Hinweis, keine Garantie |

---

## 7. Umgang mit veralteten/unklaren Quellen

- Ausgaben aus `quelle_veraltet` oder `quelle_unklar` werden sichtbar markiert.
- Nutzer wird zur Verifikation aufgefordert.
- Im strengen Datenschutzmodus: zusätzliche Zurückhaltung bei Förderzusagen.

---

## 8. Offene Punkte

- Konkretes Quellenregister-Format (Phase 4).
- Quellen-Aktualisierungslauf (manuell / automatisch, Phase 8+).
- Prüfer-Rolle für Fachquellen (Phase 18 bei Enterprise / lizenzierten Quellen).
- Integration externer Fachquellen (nicht MVP).

---

## 9. Stand Run 1

- **Kein** Quellenregister implementiert.
- **Keine** aktiven Quellen angelegt.
- Dieser Text ist reines Regelwerk und zukünftige Leitplanke.
