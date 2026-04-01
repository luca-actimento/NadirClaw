# Split Oversized Source Files

> Auto-generiert: 2026-03-21 | Limit: 300 Zeilen pro Source-Datei
> Grund: Große Dateien verschwenden Tokens (ganzes File wird gelesen statt gezielter Teil)

## 17 Dateien über dem Limit

- [ ] `tests/test_tool_calling.py` — **485 Zeilen**
- [ ] `tests/test_setup.py` — **620 Zeilen**
- [ ] `tests/test_routing.py` — **706 Zeilen**
- [ ] `tests/test_pipeline_integration.py` — **458 Zeilen**
- [ ] `tests/test_optimize.py` — **474 Zeilen**
- [ ] `tests/test_optimize_lossless.py` — **388 Zeilen**
- [ ] `tests/test_e2e.py` — **565 Zeilen**
- [ ] `nadirclaw/setup.py` — **988 Zeilen**
- [ ] `nadirclaw/server.py` — **1919 Zeilen**
- [ ] `nadirclaw/routing.py` — **555 Zeilen**
- [ ] `nadirclaw/report.py` — **507 Zeilen**
- [ ] `nadirclaw/optimize.py` — **537 Zeilen**
- [ ] `nadirclaw/oauth.py` — **1012 Zeilen**
- [ ] `nadirclaw/dashboard.py` — **305 Zeilen**
- [ ] `nadirclaw/credentials.py` — **474 Zeilen**
- [ ] `nadirclaw/cli.py` — **1365 Zeilen**
- [ ] `nadirclaw/budget.py` — **301 Zeilen**

## Strategie
- Logische Blöcke extrahieren (z.B. Helpers, Types, Sub-Components)
- Re-Exports aus Index-Datei wenn nötig
- Tests mitnehmen beim Aufteilen
- CODEBASE-MAP.md nach Split aktualisieren
