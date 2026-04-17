# scripts/

## Zweck

Hilfsskripte für Entwicklung, Test, Prüfung und Wartung **ohne echte Außenwirkung**.

## Harte Regeln

- **Keine echten Daten.** Skripte arbeiten nie mit echten Nutzer-/Kundendaten.
- **Keine Secrets.** Keine Zugangsdaten im Code. Secrets werden, falls nötig, als Parameter oder aus Secret Manager geladen (später).
- **Keine produktiven Integrationen.** Kein Skript ruft Produktions-APIs ohne explizites Gate und Human-in-the-loop.
- **Keine Außenwirkung.** Kein automatischer Versand, keine automatische Buchung, keine automatische Antragstellung, keine Social-Media-Aktion.
- **Idempotenz bevorzugt.** Skripte bevorzugt so gestaltet, dass Mehrfachausführung keinen Schaden erzeugt.
- **Dokumentation im Kopf.** Jedes Skript beschreibt Zweck, Eingaben, Ausgaben, Seiteneffekte, Umgebungen.

## Erlaubt (Beispiele, geplant)

- Lint-/Format-Helfer
- Secret-Scan-Helfer
- Testdatengenerator (synthetisch)
- Dokumentations-Indexer
- Gate-Prüf-Helfer

## Verboten

- Produktions-Datenbankmigrationen ohne Gate
- Mail- / Kalender- / Zahlungs- / Behörden-Tools
- Scraping gegen Drittdienste ohne Rechtsklärung

## Stand Run 1

Leer. Skripte folgen bedarfsgetrieben in späteren Phasen.
