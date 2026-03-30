# Phase 4: Analytics & Routing Feedback

## Goal
Build cost visibility and a feedback loop so misrouted prompts can be flagged and the classifier improves over time.

## Requirements

### R1: Routing Feedback Loop
- `nadirclaw flag <request-id> --reason misrouted` writes a correction record
- Corrections stored in SQLite for future centroid retraining
- Track correction rate as quality signal

### R2: Per-Project Cost Attribution
- Tag requests with project identifier (X-Project header or config)
- `nadirclaw report --by-project` shows cost breakdown per Actimento project
- CSV/JSONL export for tracking/ integration

### R3: Grafana Dashboard
- Pre-built Grafana dashboard JSON for the existing Prometheus /metrics endpoint
- Covers: request rate, routing distribution, cost per tier, error rates
- Setup docs in docs/grafana.md

### R4: Cost Anomaly Alerts
- Alert when a project's daily spend exceeds 2x its 7-day average
- Output to stderr/log (no external notification system needed yet)

## Acceptance Criteria
- [ ] `nadirclaw flag` writes correction records
- [ ] `nadirclaw report --by-project` shows per-project costs
- [ ] Grafana dashboard JSON importable and shows live data
- [ ] Anomaly detection triggers on simulated cost spike

## Estimated Effort
Medium (2-3 sessions)
