# Architecture — PulseForge

## High-Level Design (HLD)
PulseForge profiles every model call for tokens, latency, and cost, then routes and caches to cut spend — an observability-plus-optimization layer for an AI product’s model usage.

```mermaid
%%{init: {'theme':'base','themeVariables':{'primaryColor':'#ffffff','lineColor':'#2563eb','mainBkg':'#ffffff'}}}%%
graph LR
    A([LLM Calls])
    B([Token / Latency Profiler])
    C([Smart Router + Cache])
    D([Cost Report])
    A --> B
    B --> C
    C --> D
    style A fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style B fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style C fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
    style D fill:#eff6ff,stroke:#2563eb,stroke-width:2px,color:#1e40af
```

**Flow:** LLM Calls → Token / Latency Profiler → Smart Router + Cache → Cost Report

## Low-Level Design (LLD)
- **Components:** `OpenAI`, `Redis`, `Prometheus`
- **Interfaces / contracts:** to be finalized during implementation.
- **Data model:** to be defined per component.

## Decision Log
- **Why this stack:** **OpenAI** — cloud llm reasoning; **Redis** — in-memory store / cache / queue; **Prometheus** — metrics & alerting.
- **Antigravity constraint:** run logic/state/UI locally; offload heavy reasoning to cloud APIs; target modest hardware.

## Concept Deep Dive
Turning raw model telemetry into routing and caching decisions that measurably lower cost.
