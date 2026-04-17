# COMPLIANCE.md — Fachgrenzen und Compliance-Regeln (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 28.

---

## 1. Grundaussage

Das System ist **kein** Anwalt, Steuerberater, Finanzberater, Arzt, Therapeut oder eine offizielle Behörde. Es ersetzt keine Fachberatung. Es bereitet vor, strukturiert, warnt und macht Fachprüfungsbedarf sichtbar.

---

## 2. Harte Compliance-Grenzen

### 2.1 Keine Rechtsberatung
- Keine verbindlichen Rechtsaussagen.
- Keine Vertragsabschlüsse.
- Vertragstexte sind **Entwürfe** mit Hinweis auf Fachprüfung.

### 2.2 Keine Steuerberatung
- Keine verbindlichen Steueraussagen.
- Steuerliche Themen nur mit Quellenstatus und Fachprüfungsempfehlung.
- Keine automatische Steueranmeldung oder Voranmeldung.

### 2.3 Keine Fördergarantie
- Keine Zusage, keine Erfolgsquote, keine „sichere" Bewilligung.
- Förderinformationen immer mit Quellenstatus und Aktualitätsmarker.

### 2.4 Keine medizinische/therapeutische Beratung
- Auch wenn Nutzer persönliche Belastung schildern: keine Therapieersatzhandlung.
- Hinweis auf Fachstellen, wenn sensible Hinweise erkannt werden.

### 2.5 Keine Finanz-/Kreditberatung
- Keine Kreditempfehlungen.
- Keine Anlageberatung.
- Finanzrisiken werden als Risikoampel sichtbar, nicht als Empfehlung.

### 2.6 Keine Behördenkommunikation
- Kein automatisches Einreichen von Anträgen.
- Behördenwege werden beschrieben, nicht durchgeführt.

---

## 3. Fachprüfungsstatus

Alle Aussagen, die rechtliche, steuerliche, förderrechtliche, versicherungsrechtliche oder medizinische Wirkung haben, tragen einen Fachprüfungsstatus:

- `nicht_erforderlich`
- `erforderlich_offen`
- `erforderlich_in_arbeit`
- `bestaetigt` (durch qualifizierte Person / Stelle)
- `abgelehnt`

Kein Dokument verlässt das System „freigegeben" zu fachrelevanten Themen, ohne dass der Fachprüfungsstatus gesetzt ist.

---

## 4. Quellenpflicht bei veränderlichem Wissen

Themen mit hoher Änderungsrate (Förderung, Steuerrecht, Sozialversicherung, Behördenverfahren):

- Quellenangabe mit Datum.
- Quellenstatus `quelle_geprueft` oder höher für MVP-tauglich.
- Warnung, wenn `quelle_veraltet` oder `quelle_unklar`.

---

## 5. Regional- und Rechtsraum

- Fokus MVP: **deutscher Rechtsraum** (keine verbindliche Aussage, aber Beispielreferenz).
- Internationale Rechtslogik ist **kein** MVP-Bestandteil.
- Regionale Unterschiede (Bund/Land/Kommune) werden, wo relevant, als Unsicherheit markiert.

---

## 6. Lizenzierte Fachquellen

- Keine Einbindung lizenzpflichtiger Fachdatenbanken ohne dokumentierte Lizenz.
- Zitate und Auszüge nur im zulässigen Umfang.

---

## 7. Nutzerkommunikation

UI-Texte und Agenten-Ausgaben müssen klar machen:

- Dieses System ersetzt keine Fachberatung.
- Verbindliche Entscheidungen erfordern Prüfung durch qualifizierte Person.
- Risiken sind sichtbar, werden aber nicht von einem Fachberater bewertet.

---

## 8. Compliance-Prüfung (Pflichtschritt pro Run)

Jeder Run prüft:

- Werden neue Aussagen mit Fach-Wirkung erzeugt?
- Haben sie einen Quellenstatus?
- Haben sie einen Fachprüfungsstatus?
- Wird irgendwo Fachberatung suggeriert, wo keine ist?
- Werden Förderungen garantiert oder versprochen?

---

## 9. Offene Punkte

- AGB, Nutzungsbedingungen, Datenschutzhinweis (Texte folgen später).
- Impressumspflicht bei öffentlicher Veröffentlichung.
- Dokumentationspflicht zu Herkunft von Trainingsdaten (soweit relevant für gewählten Techstack).
- Barrierefreiheitsrichtlinien (in `UI`/`Frontend`-Phase).
- Urheberrechtliche Prüfung bei Vorlagen.

---

## 10. MVP-Mindestanforderungen

- Keine Fachberatung in Ausgaben.
- Alle fachrelevanten Aussagen mit Status.
- Deutliche Hinweise auf Fachprüfungsbedarf.
- Keine garantierende Sprache zu Förderung.
- Keine automatischen Einreichungen.
