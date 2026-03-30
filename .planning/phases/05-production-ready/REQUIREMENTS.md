# Phase 5: Production-Ready (v1.0)

## Goal
Stabilize the API, add custom classifier training, build integration tests, and set up a LaunchAgent for persistent local operation.

## Requirements

### R1: Stable API Contract
- Document and freeze /v1/* endpoint shapes
- OpenAPI spec generated from FastAPI (already built-in)
- Breaking change = major version bump policy documented

### R2: Custom Classifier Training
- `nadirclaw train --data prompts.jsonl` rebuilds centroids from labelled data
- JSONL format: `{"prompt": "...", "tier": "simple|mid|complex"}`
- Actimento-specific prompt patterns can tune the classifier

### R3: End-to-End Integration Tests
- Test suite covering: classify -> route -> provider call -> log
- Runs in CI without real API keys (recorded fixtures/mocks)
- `pytest tests/integration/` with at least 10 test cases

### R4: LaunchAgent for Persistent Operation
- `de.actimento.nadirclaw.plist` for auto-start on login
- Logs to ~/Library/Logs/nadirclaw/
- Health-check script that restarts on crash
- Registered in claude-setup launchagents/

## Acceptance Criteria
- [ ] OpenAPI spec accessible at /docs
- [ ] `nadirclaw train --data fixtures/test-prompts.jsonl` succeeds
- [ ] `pytest tests/integration/` passes with 100% on fixtures
- [ ] LaunchAgent starts nadirclaw on login, verified via `launchctl list`
- [ ] `nadirclaw --version` shows 1.0.0

## Estimated Effort
Large (3-4 sessions)
