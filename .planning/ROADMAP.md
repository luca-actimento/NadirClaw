# Roadmap — nadirclaw

## Milestone: MVP Router

### Phase 1: Anforderungen & Design
**Goal:** Klarer Scope, API-Design, Routing-Logik definieren.
**Scope:**
- Routing-Strategie: welche Metriken → welches Model (Komplexität, Token-Count, Kontext)
- API-Design: POST /route → {model, reason}
- Unterstützte Provider: Ollama (lokal), Claude, Gemini, OpenAI

### Phase 2: Core Router
**Goal:** Minimaler funktionierender Router.
**Scope:**
- FastAPI oder Flask Endpunkt
- Heuristic-Router: kurz/einfach → Ollama, lang/komplex → Claude
- Config: thresholds per ENV-Var

### Phase 3: Claude-Setup Integration
**Goal:** matrix-claude + agents-admin nutzen nadirclaw als Router.
**Scope:** HTTP-Call zu nadirclaw statt direktem Provider-Aufruf
