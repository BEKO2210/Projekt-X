# reports/

## Zweck

Dieser Ordner enthält **Run-Berichte**. Jeder Claude-Code-Run dokumentiert sein Ergebnis hier.

## Konvention

- Dateiname: `run-XXX-<kurzname>.md` (`XXX` dreistellig, beginnend bei `001`).
- Vorlage: `templates/run_report_template.md`.
- Pflicht pro Bericht: Ziel, gelesene Dateien, Änderungen, Datenschutzprüfung, Sicherheitsprüfung, Quellenprüfung, Fachprüfungsprüfung, Tests, Ergebnis, offene Punkte, Blocker, nächster Run-Prompt.

## Ablauf

1. Run startet (vorgegebener Prompt oder zuletzt geschriebener Next-Prompt, vom Nutzer gestartet).
2. Claude Code arbeitet gemäß `CLAUDE.md` §2.
3. Run-Bericht wird **immer** geschrieben — auch bei Abbruch oder Blocker.
4. Letzter Abschnitt des Berichts enthält den Vorschlag für den nächsten Run-Prompt.
5. Der nächste Prompt wird **nicht** automatisch ausgeführt.

## Inhalt

- `run-001-foundation.md` — Foundation (Phase 0, Run 1).
- weitere Berichte folgen.
