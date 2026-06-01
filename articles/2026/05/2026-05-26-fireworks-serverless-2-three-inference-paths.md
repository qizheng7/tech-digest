---
title: "Fireworks Serverless 2.0: Three Ways to Run Inference, One API"
date: 2026-05-26
source_url: https://fireworks.ai/blog/serverless-2
source: Fireworks AI
type: article
topics: [ai-infra]
tags: [Fireworks, serverless, inference, API, SLA, rate-limiting, priority-queuing, throughput, agentic, developer-tools]
saved_at: 2026-05-31
---

## Summary

Fireworks AI launched Serverless 2.0, offering three distinct serving paths through a single API with no reserved capacity requirements: Standard (cost-efficient shared infra), Priority (enhanced admission control, ~1.5x Standard pricing, 0% rejection vs 0.082% for Standard in testing), and Fast (100+ tokens/second optimized path using the same model weights). The update also splits the previously opaque single 429 error code into three precise signals — 429 for rate limits, 503 Service Overloaded for temporary saturation, and 503 Service Unavailable for platform issues — enabling teams to apply the correct retry or escalation logic. A Background async tier (preview, ~¼ Standard pricing) is also available.

## Key Highlights

- **Three serving paths**: Standard / Priority / Fast — one API, no capacity commitment required
- **Priority tier**: 0% rejection rate vs 0.082% for Standard under load; ~1.5x Standard pricing
- **Fast tier**: targets 100+ tokens/second for high-throughput workloads
- **Improved error taxonomy**: 429 (rate limit), 503 Overloaded (temporary), 503 Unavailable (platform) — replaces single 429
- **Background tier** (preview): async processing at ~¼ Standard pricing for latency-insensitive jobs
- Designed for bursty agentic workloads where traffic is unpredictable during development

## Why It Matters

Serverless 2.0 plugs the gap between cheap-but-unreliable shared inference and expensive dedicated deployments, giving developers the right escalation ladder for production agentic systems without upfront capacity bets.

---
[Source: Fireworks AI](https://fireworks.ai/blog/serverless-2)
