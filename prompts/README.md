# prompts/

## Zweck

Ablage für **Agenten-Prompt-Spezifikationen** und versionierte Prompt-Dateien.

## Harte Regeln

- **Keine echten Daten** in Beispielausgaben oder Testinputs.
- **Keine Secrets**, keine Zugänge, keine Zugangsdaten.
- **Keine produktiven Integrationen** aus Prompts heraus.
- **Keine Außenwirkung** (kein realer Versand, keine reale Buchung).
- Jeder Prompt gehört zu einem Agenten mit **Rollenvertrag** (siehe `AGENTS.md`). Kein Prompt ohne Rollenbezug.
- Prompts sind **versioniert**. Jede Änderung erhöht die Version.

## Konvention (geplant)

- Dateiname: `<agent_name>/<agent_name>_v<MAJOR>.<MINOR>.md`
- Kopf jeder Datei: Agentname, Version, Scope, erlaubte/verbotene Aktionen, Eingaben, Ausgaben, Testfälle.

## Stand Run 1

Leer. Prompts entstehen erst ab Phase 3 (Kernagenten), nicht vorher.
