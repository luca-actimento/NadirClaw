# nadirclaw – CLAUDE.md

> Globale Regeln (Persoenlichkeit, Memory, Routing, Enforcement) -> `~/.claude/CLAUDE.md`
> 40 Skills verfuegbar -> `~/.claude/commands/` | 52 Hooks aktiv -> `~/.claude/hooks/`
> Rules (Git-Safety, Security, DoD, Credentials) -> `~/.claude/rules/`

<!-- Diese Datei liegt im Projekt-Root und wird von Claude Code automatisch geladen
     wenn die Session in diesem Verzeichnis gestartet wird. -->


## Ecosystem-Integration

Dieses Projekt ist Teil des Claude-Ökosystems. Was dir zur Verfügung steht:

| System | Was es tut | Wie du es nutzt |
|--------|-----------|-----------------|
| **Skills** (40) | Spezialisierte Workflows | `/deploy`, `/qa`, `/review`, `/blast`, `/gsd:*` — alle via `~/.claude/commands/` |
| **Hooks** (52) | Automatische Guards | Git-Safety, Secret-Scanner, Verify-Before-Commit — laufen automatisch |
| **Rules** | Enforcement | Security, Credentials, DoD — in `~/.claude/rules/` |
| **Brain** (:8043) | Event-Hub + Graph | Events empfangen/senden, Projekt-Graph, Compliance |
| **Actimento Tasks** | Aufgaben-SSoT | `ls .planning/todos/pending/acti-*.md` — deine aktuellen Tasks (alle 30min gesynct) |
| **Dispatch** | Cross-Repo Tasks | claude-setup kann HANDOFF-Dateien in dieses Repo schreiben |
| **CODEBASE-MAP** | Token-Spar-Übersicht | `CODEBASE-MAP.md` im Root — lies das statt Explore-Agent |

**Cross-Projekt Interaktion:**
- Du kannst via `curl -X POST http://localhost:8043/event` Events an andere Projekte senden
- HANDOFFs in deinem Root (`HANDOFF-*.md`) werden vom Dashboard erkannt und angezeigt
- Dein Projekt-Status wird von `scripts/project-audit.js` in claude-setup überwacht

## Persönlichkeit
<!-- Optional: Gib diesem Projekt-Agent einen eigenen Charakter.
     Beispiel: "Du bist 'Pixel' — der kreative Agent. Sprichst in Metaphern, liebst Retro-Ästhetik."
     Ohne diese Section nutzt Claude den Standard-Charakter aus der globalen CLAUDE.md. -->

## Projektbeschreibung
<!-- Kurz: Was ist das Projekt, wer nutzt es, welches Problem löst es? -->

## Tech-Stack
- **Frontend:** ...
- **Backend:** ...
- **Datenbank:** ...
- **Auth:** ...
- **Hosting:** ...

## Key Files
```
src/                    # ...
prisma/schema.prisma    # DB Models
.env.example            # Env-Var Platzhalter
```

## Architektur-Entscheidungen
<!-- Wichtige Decisions die Claude kennen muss (z.B. REST statt GraphQL, warum) -->

## Entwicklung

### Lokaler Start
```bash
# Abhängigkeiten
# ...

# Dev-Server
# ...
```

### Tests
```bash
# Unit-Tests
# ...

# Smoke-Test (Happy Path)
# curl -X POST ... etc.
```

## Phasen-Abschluss (Pflicht)
1. `pnpm type-check && pnpm lint && pnpm test` (oder äquivalent)
2. Alle neuen Endpoints per curl testen
3. Browser-Check der betroffenen UI-Bereiche

## Deployment
- **Staging:** ...
- **Production:** ...
- **Wie:** (Coolify / GitHub Actions / manuell)

## Umgebungsvariablen
<!-- Keine Keys! Nur Env-Var-Namen + Zweck -->
| Var | Zweck |
|-----|-------|
| `DATABASE_URL` | PostgreSQL Connection String |
| `...` | ... |

## Datei-Disziplin (HARD RULE)

| Datei | Zweck | Max. Größe |
|-------|-------|------------|
| **CLAUDE.md** | Dauerhaftes Projektwissen, keine TODOs/Pläne | ~70 Zeilen |
| **MASTERPLAN.md** | Roadmap: Vision + aktive/geplante Phasen. Abgeschlossene Phasen → Memory auslagern | ~200 Zeilen |
| **MASTERPLAN-DIGEST.md** | Auto-generierte Kurzversion des MASTERPLAN | ~20 Zeilen |
| **PLAN.md** | Aktuelle Session-Arbeit, wird on-demand erstellt/gelöscht | beliebig |

- MASTERPLAN.md > 200 Zeilen = **zu groß** → abgeschlossene Phasen als Memory-Datei auslagern
- Pläne, TODOs, Nächste Schritte → **PLAN.md** (nicht MASTERPLAN, nicht CLAUDE.md)
- CLAUDE.md enthält nur dauerhaftes Projektwissen, keine laufenden Aufgaben
