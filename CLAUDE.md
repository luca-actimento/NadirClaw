# nadirclaw – CLAUDE.md

<!-- Diese Datei liegt im Projekt-Root und wird von Claude Code automatisch geladen
     wenn die Session in diesem Verzeichnis gestartet wird. -->

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
