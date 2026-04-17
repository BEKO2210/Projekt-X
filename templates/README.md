# templates/

## Zweck

Wiederverwendbare **Prüf- und Berichtsvorlagen**.

## Inhalt

- `run_report_template.md` — Vorlage für jeden Run-Bericht in `reports/`.

Weitere Vorlagen (Dev-to-Test-Prüfformular, Test-to-Production-Prüfformular, ADR-Vorlage, Gate-Prüfvorlage, Abweichungsprüfung Test/Prod) folgen in späteren Runs.

## Harte Regeln

- Vorlagen enthalten **keine** echten Daten, **keine** Secrets, **keine** produktiven Endpunkte.
- Vorlagen sind so gestaltet, dass sie Datenschutz- und Sicherheitsprüfung **erzwingen**, nicht optional anbieten.
