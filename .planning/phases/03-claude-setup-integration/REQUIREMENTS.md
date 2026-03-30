# Phase 3: Claude-Setup Model Routing Integration

## Goal
Connect NadirClaw to the claude-setup ecosystem so that model-routing rules (Haiku/Sonnet/Opus tier mapping) flow through the router, and other studio projects can use it as their LLM proxy.

## Requirements

### R1: Tier Mapping for Claude Ecosystem
- Map claude-setup model tiers to NadirClaw routing:
  - Haiku tasks (trivial) -> simple tier -> cheapest model
  - Sonnet tasks (standard dev) -> mid tier -> balanced model
  - Opus tasks (architecture) -> complex tier -> best model
- Configurable via ENV or config file

### R2: Persistent SQLite Cache
- Opt-in SQLite-backed prompt classification cache (survives restarts)
- Config: `NADIRCLAW_CACHE_BACKEND=sqlite` (default remains in-memory LRU)
- Cache key: prompt hash -> classification result + timestamp

### R3: Integration Endpoint
- `/v1/route` endpoint that returns routing decision without proxying
- Response: `{"tier": "simple", "model": "ollama/llama3", "reason": "short prompt, low complexity"}`
- Useful for claude-setup to query routing decisions without sending the full request

### R4: Port Registration
- Register port 8856 in claude-setup config/port-registry.json
- Add nadirclaw to config/provider-status.json if applicable

## Acceptance Criteria
- [ ] claude-setup's model-routing can query NadirClaw for tier decisions
- [ ] SQLite cache persists classifications across server restarts
- [ ] `/v1/route` returns valid routing decisions
- [ ] Port 8856 registered in claude-setup port-registry

## Estimated Effort
Medium (2-3 sessions)
