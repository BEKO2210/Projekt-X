# testdata/

## Zweck

Ausschließlich **synthetische Testdaten** für Entwicklung und Test.

## Harte Regeln

- **Keine echten Daten.** Keine Klarnamen, keine realen Adressen, keine realen E-Mails, keine realen Telefonnummern, keine realen IDs (Steuer-, Renten-, Kranken-, Kontonummer).
- **Keine Secrets.** Keine API-Keys, keine Tokens, keine Passwörter, keine Zugangsdaten.
- **Keine produktiven Integrationen.** Kein echter Drittdienst darf mit diesen Daten kontaktiert werden.
- **Keine Außenwirkung.** Testdaten erzeugen nie einen echten Versand, keine echte Buchung, keinen echten Antrag.

## Erwartet

- Jede Datei beschreibt ihren **Zweck** und ihre **Herkunft** im Kopf.
- Namen/Werte sind erkennbar synthetisch (`user_test_01`, `beispiel@example.invalid`, `+49 000 00000000`).
- Keine sensiblen Klartextinhalte, auch nicht synthetisch imitiert für echte Personen.

## Stand Run 1

Leer. Synthetische Testdaten folgen in späteren Runs.
