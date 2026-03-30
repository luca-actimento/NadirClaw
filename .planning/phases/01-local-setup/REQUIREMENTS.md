# Phase 1: Local Setup & Validation

## Goal
Get NadirClaw running locally on the M5 Pro, verify the fork works end-to-end, and establish the dev workflow.

## Requirements

### R1: Python Environment
- Python 3.10+ venv created and documented
- All dependencies from pyproject.toml installed
- sentence-transformers model downloaded and cached

### R2: Server Runs
- `nadirclaw serve` starts on port 8856 without errors
- Health endpoint responds: `curl -sf http://localhost:8856/health`
- `/v1/chat/completions` accepts a test prompt and routes it

### R3: Provider Configuration
- At least one provider configured (Ollama local or Claude API key from ~/.secrets)
- Classifier categorizes a simple prompt as "simple" and a complex one as "complex"
- Routing sends simple prompts to cheaper tier, complex to expensive tier

### R4: LaunchAgent (Optional)
- plist for `de.actimento.nadirclaw` to auto-start on login
- Verify with `launchctl list | grep nadirclaw`

## Acceptance Criteria
- [ ] `nadirclaw serve` runs without crash for 60s
- [ ] `curl -sf http://localhost:8856/v1/chat/completions -d '{"model":"auto","messages":[{"role":"user","content":"hello"}]}'` returns a valid response
- [ ] `nadirclaw status` shows provider health
- [ ] Classifier latency < 50ms (embedding-based, no API call)

## Estimated Effort
Small (1-2 sessions)
