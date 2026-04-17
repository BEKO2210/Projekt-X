# config/

## Zweck

Konfiguration **ohne Secrets**. Umgebungs- und Feature-Flag-Definitionen, Platzhalter, Beispiele.

## Harte Regeln

- **Keine Secrets.** Keine API-Keys, keine Tokens, keine Passwörter im Klartext.
- **Keine echten Daten.** Keine echten Nutzer- oder Kundendaten in Beispielkonfigurationen.
- **Keine produktiven Integrationen.** Beispiel-Konfigurationen zeigen Struktur, nicht reale Endpunkte.
- **Keine Außenwirkung** aus Konfiguration heraus.
- Platzhalter sind erkennbar: `<API_KEY>`, `change_me`, `example.invalid`.
- Umgebungsvariablen werden in `.env.example`-Dateien dokumentiert — **ohne** echte Werte.

## Konvention (geplant)

- `config/dev/` — Entwicklungs-Defaults (nur Platzhalter).
- `config/test/` — Testumgebung (synthetisch, getrennt).
- `config/prod/` — Produktionsstruktur (Werte via Secret Manager zur Laufzeit, nie im Repo).
- `config/feature_flags.md` — Liste aller Flags mit Zweck, Umgebung, Standardwert.

## Stand Run 1

Leer. Konkrete Konfiguration folgt erst nach Techstack-ADR und Phase 1.
