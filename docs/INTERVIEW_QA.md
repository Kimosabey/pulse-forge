# Interview Q&A — PulseForge

### "Tell me about this project."
PulseForge is aI cost and latency optimizer with real-time token profiling and smart routing. PulseForge profiles every model call for tokens, latency, and cost, then routes and caches to cut spend — an observability-plus-optimization layer for an AI product’s model usage.

### "What was the hardest part?"
Turning raw model telemetry into routing and caching decisions that measurably lower cost.

### "Why did you choose this stack?"
- **OpenAI** — cloud llm reasoning.
- **Redis** — in-memory store / cache / queue.
- **Prometheus** — metrics & alerting.

### "How does it fit the rest of your portfolio?"
It follows my "Antigravity" model — local logic/state/UI, cloud reasoning where it earns its cost — and shares the documentation and deployment conventions used across all my projects (AX-03).
