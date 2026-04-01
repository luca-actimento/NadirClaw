# NadirClaw — Masterplan

> Zuletzt aktualisiert: 2026-03-30

---

## Vision

Fork von [NadirClaw](https://github.com/doramirdor/NadirClaw) — einem Open-Source LLM-Router, der einfache Prompts automatisch an guenstigere Modelle weiterleitet und 40-70% API-Kosten spart. Der Fork liegt unter `luca-actimento/NadirClaw` und dient als Testbed fuer Actimento-spezifische Anpassungen sowie als Grundlage fuer die eigene Model-Routing-Strategie in claude-setup.

**Upstream:** `doramirdor/NadirClaw` (MIT License)
**Fork:** `luca-actimento/NadirClaw`
**Port:** 8856 (Default NadirClaw Server)

---

## Tech-Stack

| Komponente | Technologie |
|---|---|
| Sprache | Python 3.10+ |
| Framework | FastAPI + Uvicorn |
| Klassifizierung | sentence-transformers (Embedding-basiert), NumPy Centroids |
| LLM-Proxy | LiteLLM (Multi-Provider) |
| CLI | Click |
| Streaming | SSE-Starlette |
| Optional | OpenTelemetry (Telemetry), Rich (Dashboard) |

---

## Architektur

```
nadirclaw/
  classifier.py      # Prompt-Klassifizierung (simple/mid/complex) via Embedding-Centroids
  routing.py          # Tier-basiertes Routing zu Providern (Fallback-Chains)
  server.py           # FastAPI Proxy-Server (OpenAI-kompatibel, /v1/*)
  cli.py              # CLI: serve, status, report, onboard-Commands
  budget.py           # Budget-Alerts und Kosten-Tracking
  cache.py            # In-Memory LRU Cache fuer Prompt-Klassifizierung
  metrics.py          # Prometheus /metrics Endpoint
  rate_limit.py       # Rate-Limiting pro Provider
  savings.py          # Kostenersparnis-Berechnung und Reporting
  web_dashboard.py    # Browser-Dashboard fuer Kosten/Routing-Uebersicht
  encoder.py          # Sentence-Transformer Embedding-Encoder
  settings.py         # Konfiguration via Environment-Variablen
  auth.py / oauth.py  # API-Key und OAuth-Authentifizierung
  credentials.py      # Provider-Credential-Management
```

---

## Kernentscheidungen

| Entscheidung | Grund |
|---|---|
| Fork statt eigene Loesung | NadirClaw hat solide Basis (Classifier, Multi-Provider, Cost-Tracking) |
| Upstream-Sync beibehalten | Bugfixes und neue Features von doramirdor mitnehmen |
| LiteLLM als Provider-Layer | Unterstuetzt 100+ Modelle, OpenAI-kompatibles Interface |
| Embedding-Classifier | Schnell (~10ms), keine API-Calls fuer Klassifizierung noetig |
| Lokaler Betrieb | API-Keys bleiben auf der Maschine, kein Cloud-Proxy |

---

## Fork-Divergenzen

Aktuelle Aenderungen gegenueber Upstream:

1. **Context Optimization** (v0.13.0) — Safe + Aggressive Modes fuer Prompt-Komprimierung
2. **X-Routed-* Response Headers** (v0.12.0) — Transparenz welches Modell genutzt wurde
3. **Per-Tier Fallback Chains** (v0.11.0) — Automatischer Failover innerhalb eines Tiers
4. **GSD Integration** — ROADMAP.md, CODEBASE-MAP.md, CLAUDE.md fuer Agent-Workflow

---

## Sync-Strategie mit Upstream

```
upstream (doramirdor/NadirClaw)  →  git fetch upstream
                                     git merge upstream/main --no-edit
                                     Konflikte manuell loesen
origin (luca-actimento/NadirClaw) ←  git push origin main
```

- Regelmaessig Upstream-Merges (vor jeder neuen Feature-Phase)
- Eigene Features in separaten Commits, klar getrennt von Upstream-Code
- Bei Upstream-Breaking-Changes: Adapter-Layer statt Fork-Drift

---

## Abgeschlossene Phasen

- [x] Phase 0: Fork erstellt, Upstream-Remote konfiguriert
- [x] Phase 0.1: GSD-Setup (CLAUDE.md, MASTERPLAN, CODEBASE-MAP, ROADMAP)
- [x] Phase 0.2: Context Optimization (v0.13.0)
- [x] Phase 0.3: Response Headers + Fallback Chains (v0.11-v0.12)

---

## Aktive Phase

### Phase 1: MVP Router fuer Actimento-Ecosystem

- [ ] Provider Health-Aware Routing (429/5xx Tracking, Auto-Downgrade)
- [ ] `nadirclaw update-models` Command (Registry-basierte Modell-Updates)
- [ ] Persistent SQLite Cache (ueberlebt Restarts)
- [ ] Integration mit claude-setup Model-Router (Haiku/Sonnet/Opus Tier-Mapping)

---

## Backlog

### Phase 2: Analytics und Feedback
- [ ] Routing Feedback Loop (`nadirclaw flag --reason misrouted`)
- [ ] Grafana Dashboard JSON fuer Prometheus-Metriken
- [ ] Per-Projekt Kosten-Attribution (Actimento-Projekte tracken)

### Phase 3: Production-Ready (v1.0)
- [ ] Stable API Contract (/v1/* einfrieren)
- [ ] Custom Classifier Training mit eigenen Prompt-Daten
- [ ] End-to-End Integration-Tests mit Fixtures
- [ ] LaunchAgent fuer dauerhaften lokalen Betrieb

---

## Bekannte Constraints

- Sentence-Transformer braucht ~500MB RAM beim ersten Load
- Kein GPU noetig (CPU-Inference genuegt fuer Klassifizierung)
- LiteLLM muss bei neuen Providern ggf. aktualisiert werden
- OpenRouter Passthrough-Mode noch nicht implementiert
