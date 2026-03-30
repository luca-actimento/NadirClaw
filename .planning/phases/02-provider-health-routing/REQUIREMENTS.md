# Phase 2: Provider Health-Aware Routing

## Goal
Make the router resilient — track provider errors (429/5xx/timeout), auto-downgrade to healthy alternatives, and expose health scores.

## Requirements

### R1: Rolling Error Tracking
- Track rolling error rates per provider (window: 5 min)
- Error types: 429 (rate limit), 5xx (server error), timeout (configurable threshold)
- Store in-memory, no external dependencies

### R2: Auto-Downgrade
- When a provider's error rate exceeds threshold (e.g. >30% in window), mark as degraded
- Routing falls back to next provider in the tier's fallback chain (already exists in v0.11.0)
- Auto-recover: when error rate drops below threshold, restore provider

### R3: Health Visibility
- `nadirclaw status` shows per-provider health score (0-100%)
- `/health` endpoint includes provider health summary
- X-Provider-Health response header on routed requests

### R4: Model Registry Update Command
- `nadirclaw update-models` pulls latest model list from a registry JSON
- Updates context windows, pricing, and available models
- Falls back gracefully if registry unreachable

## Acceptance Criteria
- [ ] Simulated 429 errors cause automatic provider downgrade within 30s
- [ ] `nadirclaw status` shows health scores per provider
- [ ] `nadirclaw update-models` updates local model registry
- [ ] Recovery: provider marked healthy again after errors stop

## Estimated Effort
Medium (2-3 sessions)
