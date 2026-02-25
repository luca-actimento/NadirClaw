I built an open-source proxy for this called NadirClaw. It sits between Claude Code and the API, classifies each prompt in ~10ms, and routes simple ones (file reads, quick questions) to a cheaper model like Gemini Flash. Complex stuff still goes to Claude.

Setup is basically two env vars and `nadirclaw serve`. In my usage about 60% of prompts end up on the cheap model. Streaming works, session persistence keeps you on the same model within a conversation.

It also works with Codex and anything that speaks the OpenAI API.

https://github.com/doramirdor/NadirClaw
