---
title: "Frontier AI at a fraction of the cost: open-source workers with a closed-source advisor"
date: 2026-06-24
source_url: https://fireworks.ai/blog/frontier-open-source-worker-with-closed-source-advisor
source: Fireworks AI
type: article
topics: [ai-infra, genai-llm]
tags: [Fireworks, open-source, GLM-5.2, Kimi-K2.6, Claude-Opus-4-8, cost-optimization, benchmark, SWE-bench, Terminal-Bench, advisor-pattern, hybrid-model]
saved_at: 2026-06-30
---

## Summary

Fireworks AI presents an architecture where an open-source model (worker) handles end-to-end task execution and decides when to consult a single closed-source frontier model (advisor) for a single review pass. The advisor is strictly an auditor — it reviews the worker's completed diff without editing. Results show +4–8 percentage point benchmark improvements across SWE-bench Pro, Terminal-Bench 2.1, and Legal Agent Benchmark, at 50–67% cost savings vs. using the closed-source model directly.

## Key Highlights

- Workers: Kimi-K2.6 and GLM-5.2 (open-source); Advisor: Claude Opus 4.8 (closed-source)
- The worker decides when to consult the advisor — after completing work and running its own verification
- **SWE-bench Pro**: +4 pp (Kimi), +7 pp (GLM) with advisor vs. worker alone
- **Terminal-Bench 2.1**: +8 pp (Kimi), +4 pp (GLM) with advisor vs. worker alone
- **Legal Agent Benchmark**: +1 pp (Kimi), +4 pp (GLM)
- GLM-5.2 + advisor matches Opus-only performance on Terminal-Bench at ~half the cost; achieves 67% savings on SWE-bench Pro at same quality level
- Advisor role is strictly auditing with no editing capability — keeps expensive compute on the cheaper open-source worker

## Why It Matters

The open-source worker + closed-source advisor pattern gives teams a practical path to frontier-quality results at open-weight prices, which becomes increasingly attractive as frontier model access gets gated or priced out of reach.

---
[Source: Fireworks AI](https://fireworks.ai/blog/frontier-open-source-worker-with-closed-source-advisor)
