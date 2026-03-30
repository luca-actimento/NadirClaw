# Roadmap — nadirclaw

> Milestone: MVP Router for Actimento Ecosystem

## Phases

| # | Phase | Status | Effort | Description |
|---|-------|--------|--------|-------------|
| 01 | Local Setup & Validation | TODO | Small | Get NadirClaw running locally, verify fork works E2E |
| 02 | Provider Health-Aware Routing | TODO | Medium | Error tracking, auto-downgrade, health visibility |
| 03 | Claude-Setup Integration | TODO | Medium | Tier mapping, SQLite cache, /v1/route endpoint |
| 04 | Analytics & Feedback | TODO | Medium | Cost attribution, routing feedback loop, Grafana |
| 05 | Production-Ready (v1.0) | TODO | Large | Stable API, custom training, integration tests, LaunchAgent |

## Dependencies

- Phase 01 must complete before any other phase (need working local setup)
- Phase 02 and 03 can run in parallel after Phase 01
- Phase 04 depends on Phase 03 (needs per-project tagging from integration)
- Phase 05 depends on all previous phases

## Key Decisions

- Port 8856 (NadirClaw default)
- LiteLLM as provider abstraction layer
- Embedding-based classifier (no API calls for classification)
- SQLite for persistence (no external DB dependency)
