# ARCHITECTURE.md — Zielstruktur (Konzept)

> **Status:** Konzept/Entwurf (Phase 0). Keine Implementierung. Kein Techstack entschieden.
> Quelle: `KI_COMPANION_BLUEPRINT.md`, Teil 2 und Teil 16.

---

## 1. Architekturziele

- Modular statt monolithisch.
- Status statt Bauchgefühl (jede relevante Information hat einen expliziten Status).
- Privacy-first, Hybrid-fähig (lokal/Cloud je nach Sensibilität).
- Human-in-the-loop bei allen Entscheidungen mit Außenwirkung.
- Quellenpflicht bei veränderlichem Wissen.
- Agentenrechte begrenzt und explizit.
- Testbar, auditierbar, rückrollbar.

---

## 2. Hauptschichten (Konzept)

Die geplante Systemstruktur umfasst folgende Schichten. Sie sind in späteren Phasen zu verfeinern:

1. **Nutzeroberfläche** — Dashboard, Projektakte, Workflows, Statusanzeigen, Umgebungskennzeichnung.
2. **Gesprächs- und Interaktionsschicht** — strukturierte Dialoge, kein freies Orakel.
3. **CEO-Orchestrator** — koordiniert Agenten, führt Widersprüche zusammen, schlägt nächste Schritte vor.
4. **Agentenebene** — spezialisierte Agenten mit Rollenverträgen (siehe `AGENTS.md`).
5. **Aufgaben- und Workflowebene** — deterministische Prozesslogik.
6. **Wissens- und Quellenebene** — Quellenstatus, Aktualität, Lizenz (siehe `SOURCES.md`).
7. **Datenschutzebene** — Datenminimierung, Modi, externe Verarbeitung sichtbar.
8. **Sicherheitsebene** — Zugriffskontrolle, Secrets, Agentenrechte.
9. **Prüf- und Qualitätsebene** — Gates, Tests, Qualitätsprüfer.
10. **Dokumentenebene** — Dokumenttypen, Abschnittsstatus, Exportwarnungen.
11. **Speicher- und Datenbankebene** — lokal/Cloud, Sensibilitätstrennung.
12. **Integrations- und Tool-Ebene** — in MVP **ausgeschaltet / nicht vorhanden**.
13. **Umgebungs- und Deploymentebene** — Dev, Test, Prod klar getrennt.
14. **Monitoring-, Audit- und Protokollebene** — Logging, Audit-Logs, Incidents.
15. **Governance- und Freigabeebene** — Release-Gates, ADRs, Run-Berichte.

---

## 3. Vereinfachtes Architekturdiagramm (Konzept)

```
[Nutzer]
   │
   ▼
[Nutzeroberfläche]  ← sichtbare Umgebung (Dev/Test/Prod)
   │
   ▼
[Gesprächs-/Interaktionsschicht]
   │
   ▼
[CEO-Orchestrator] ─── [Gate-Engine] ─── [Audit/Log]
   │
   ▼
[Agenten mit Rollenverträgen] ← [Kontextpakete minimiert]
   │
   ▼
[Workflow-/Aufgabenebene]
   │
   ▼
[Dokumentenebene] ── [Quellenebene] ── [Datenschutzebene]
   │
   ▼
[Speicher/DB]  ← Sensibilitätstrennung
```

Integrationen, E-Mail, Zahlungen, Behörden: **nicht** in diesem Diagramm, da MVP-ausgeschlossen.

---

## 4. Architekturprinzipien

### 4.1 Modular statt monolithisch
Jede Schicht ist austauschbar. Kein direkter Durchgriff von UI auf Agenten ohne Orchestrator.

### 4.2 Status statt Bauchgefühl
Jede Aussage hat einen Status: Quellenstatus, Fachprüfungsstatus, Datenschutzstatus, Sicherheitsstatus, Sensibilitätsstufe.

### 4.3 Privacy-first Hybrid
Sensible Daten bleiben lokal oder im gewählten Datenschutzmodus. Externe Verarbeitung ist sichtbar.

### 4.4 Human-in-the-loop
Kritische Aktionen benötigen explizite Nutzerbestätigung. Kein Autopilot für Außenwirkung.

### 4.5 Quellenpflicht
Veränderliches Wissen (Förderung, Recht, Steuern, Behörden) trägt Quellenstatus und Aktualitätsmarker.

### 4.6 Agentenrechte begrenzt
Kein Agent kann sich selbst Rechte geben. Rollenverträge definieren Scope, erlaubte/verbotene Aktionen.

---

## 5. Umgebungen

- **Dev (Entwicklung)** — synthetische Daten, Mocks erlaubt, keine Außenwirkung.
- **Test** — produktionsnah, synthetische Daten, keine echten Secrets.
- **Prod** — echte Nutzerdaten möglich, strenge Gates, keine Dev-/Mock-Komponenten aktiv.

Details in `RELEASES.md`.

---

## 6. Was explizit **nicht** Teil des MVP-Architekturzustands ist

- Integrationen mit Außenwirkung
- E-Mail-, Kalender-, Zahlungs-, Bank-, Behördensysteme
- Enterprise-SSO, Teamrollen-Matrix
- Internationale Rechtslogik
- RAG mit Fachquellen
- Lizenzierte Fachdatenbanken

---

## 7. Offene Punkte

- Techstack-Entscheidung (ADR in `decisions/` ausstehend).
- Speicher-/DB-Auswahl.
- Hybrid-Modell (lokal vs. Cloud) im Detail.
- Orchestrator-Implementierung (Pattern, Framework-Entscheidung).
- Prompt-Versionierungs-Mechanismus.

Diese Punkte werden **nicht** in Run 1 entschieden. Sie stehen später in ADRs.
