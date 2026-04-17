# DOCUMENTS.md — Dokumenttypen und Statuslogik (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 12.

---

## 1. Grundsatz

Dokumente im System sind immer **Entwürfe** mit sichtbarem Status. Kein Dokument wird als „fertig / verbindlich" ausgeliefert, ohne dass Nutzer und — wo nötig — Fachprüfung beteiligt waren.

---

## 2. MVP-Dokumenttypen

- **Mini-Businessplan** — Angebot, Zielgruppe, Nutzenversprechen, Weg.
- **Finanzplan light** — Kosten, Einnahmeannahmen, Szenarien, Risikoampel.
- **MVP-Plan** — Kernfunktion, Nicht-Ziele, Experiment.
- **Datenschutz-Basischeck** — Datenarten, externe Verarbeitung, Sensibilität, Empfehlungen.
- **Fördercheck light** — Förderhinweise mit **Quellenstatus**, keine Garantien.
- **Angebotsentwurf** — Leistung, Preis-Annahmen, Bedingungen.
- **E-Mail-Entwurf (ohne Versand)** — nie automatisch versandt.

Weitere Typen (Vertrag, PDF-Print, Social-Media-Text) sind **nicht** MVP.

---

## 3. Statusfelder pro Dokument

- **Entwurfsstatus:** `leer` → `entwurf` → `ueberarbeitung` → `freigegeben_intern` → `exportiert`
- **Abschnittsstatus:** pro Abschnitt eigener Status (`leer`, `entwurf`, `zu_pruefen`, `fertig_intern`).
- **Quellenstatus:** pro Aussage, wo relevant (`quelle_fehlt`/`quelle_unklar`/`quelle_veraltet`/`quelle_geprueft`).
- **Fachprüfungsstatus:** pro Dokument und, wo nötig, pro Abschnitt.
- **Exportwarnung:** wird gesetzt, wenn sensible Daten oder ungeprüfte Quellen enthalten sind.
- **Versionierung basic:** jede Speicherung erzeugt neue Version.

---

## 4. Exportregeln

- Primär: **Markdown**.
- Optional: **JSON** für maschinenlesbare Ausgabe.
- Exportwarnungen werden vor Export angezeigt.
- Export erzeugt Audit-Log-Eintrag.

---

## 5. Verbotene Ausgaben (MVP)

- Verbindliche Rechtsgutachten.
- Steuerliche Berechnungen als verbindliche Endergebnisse.
- Fördermittelanträge mit Antragscharakter.
- Final signierte Verträge.
- Finale Rechnungen.

All diese sind — wenn überhaupt — nur in späteren Phasen und dann ausschließlich als dokumentiert geprüfte Entwürfe möglich.

---

## 6. Löschung

- Nutzer kann jedes Dokument einzeln löschen.
- Löschung mit Bestätigung.
- Löschung erzeugt Audit-Log-Eintrag.
- Löschung im strengen Datenschutzmodus löst Nachverfolgung externer Kopien (falls vorhanden) als Hinweis aus — vollautomatisierte Anbieter-Löschung ist **nicht** MVP.

---

## 7. Offene Punkte

- Konkrete Abschnittsschemata je Dokumenttyp (Phase 4).
- Versionierungs-Detail (Diffs, Wiederherstellung).
- PDF-Erzeugung — **nicht** Priorität im MVP.
- Vorlagen in `templates/` (folgen in späteren Runs).

---

## 8. Stand Run 1

- **Keine** Dokumenttypen implementiert.
- Dieser Text dokumentiert nur Regeln und geplante Typen.
