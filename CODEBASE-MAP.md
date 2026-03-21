# CODEBASE-MAP — nadirclaw

> Auto-generiert: 2026-03-21 18:36 | Update: `scripts/generate-codebase-map.sh`
> 🎯 Dieses File lesen → sofort wissen wo Code liegt (spart ~80K Exploration-Tokens)
> Tiefere Docs: `.planning/codebase/` (falls vorhanden)

## Stack
Python (pyproject.toml)

## Struktur
```
  .github/ (2 files)
  docs/ (11 files)
  nadirclaw/ (26 files)
  tests/ (24 files)
```

## Key Files
- Config: `.env.example`
- Config: `docker-compose.yml`
- Config: `Dockerfile`
- Config: `.github/workflows`

## Alle Dateien (Root)
  .dockerignore
  .env.example
  .gitignore
  CHANGELOG.md
  CONTRIBUTING.md
  docker-compose.yml
  Dockerfile
  install.sh
  LICENSE
  logo_rb.png
  pyproject.toml
  README.md
  ROADMAP.md


## Letzte Commits
```
c4ba4bb feat: Context Optimize with safe + aggressive modes (v0.13.0)
f74f189 feat: add X-Routed-* response headers for routing transparency (v0.12.0)
582c004 fix: add get_tier_fallback_chain to mock settings in tests
2a20be6 feat: restore OpenClaw token reuse, add per-tier fallbacks (v0.11.0)
d1704a8 feat: multi-tier routing, editor integrations, analytics (v0.10.0)
```

## Häufig geänderte Dateien
  nadirclaw/server.py (11x)
  README.md (9x)
  nadirclaw/__init__.py (9x)
  nadirclaw/settings.py (5x)
  nadirclaw/cli.py (5x)
  ROADMAP.md (4x)
  nadirclaw/rate_limit.py (3x)
  tests/test_streaming_fallback.py (2x)

---
*Für präzise Feature→File Mappings: `/gsd:map-codebase` ausführen → distilliert tiefe Analyse in dieses File*
