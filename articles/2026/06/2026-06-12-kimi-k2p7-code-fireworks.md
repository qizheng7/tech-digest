---
title: "Kimi K2.7 Code on Fireworks: Better Agents, Lower Cost per Task, Available Day-0"
date: 2026-06-12
source_url: https://fireworks.ai/blog/kimi-k2p7-code
source: Fireworks AI
type: article
topics: [ai-infra, genai-llm]
tags: [Fireworks, Moonshot, Kimi, K2-7-Code, coding-agent, MoE, token-efficiency, agentic, benchmark, pricing]
saved_at: 2026-06-15
---

## Summary

Moonshot released Kimi K2.7 Code on June 12, 2026 with Day-0 availability on Fireworks AI. The model uses a 1T parameter / 32B active MoE architecture with a 256K context window, and achieves substantially higher benchmark scores than its predecessor K2.6 while using ~30% fewer reasoning tokens per task. The token efficiency gain is especially impactful in agent workflows where verbose reasoning re-enters context across multiple turns, compounding costs.

## Key Highlights

- Architecture: 1T total parameters, 32B active per token, 256K context window
- 30% fewer reasoning tokens vs K2.6 — reduces per-task cost significantly in agent loops
- Benchmark gains over K2.6: +21.8% Kimi Code Bench v2, +11.0% Program Bench, +31.5% MLS Bench Lite
- Pricing on Fireworks: $0.95/M input, $4.00/M output, $0.19/M cache hits
- Practical cost advantage: lower token consumption per task, not lower per-token rates

## Why It Matters

K2.7 Code's efficiency-through-reasoning-compression approach is a signal of where coding model competition is heading — benchmark scores matter less than cost-per-task in production agentic deployments.

---
[Source: Fireworks AI](https://fireworks.ai/blog/kimi-k2p7-code)
