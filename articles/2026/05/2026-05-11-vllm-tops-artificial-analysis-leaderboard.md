---
title: "vLLM Tops the Artificial Analysis Leaderboard"
date: 2026-05-11
source_url: https://vllm.ai/blog/2026-05-11-vllm-tops-artificial-analysis
source: vLLM Blog
type: article
topics: [ai-infra]
tags: [vLLM, inference, benchmark, open-source, throughput, DeepSeek, Qwen, MiniMax, EAGLE3, speculative-decoding]
saved_at: 2026-05-17
---

## Summary

vLLM achieved top rankings on the Artificial Analysis leaderboard across three frontier models — DeepSeek V3.2, Qwen 3.5 397B, and MiniMax-M2.5 — demonstrating that open-source inference can match or beat proprietary serving solutions in production. For DeepSeek V3.2, kernel fusion cut per-layer GPU launches from ~33 to ~10, delivering 1.28× speedup and 230 tok/s output throughput (4x most providers). For Qwen 3.5 397B, targeted allreduce/linear-attention kernel fixes yielded a 10% throughput boost and sub-1s TTFT on 10K-token prompts. For MiniMax-M2.5, a custom EAGLE3 speculative draft model hit 326 tok/s under optimal conditions.

## Key Highlights

- DeepSeek V3.2: 230 tok/s output — over 4× the majority of inference providers; kernel fusion reduced GPU kernel launches ~3×
- Qwen 3.5 397B: #1 among 12 measured providers, sub-1-second TTFT on 10K-token prompts; +10% throughput from allreduce_rms fusion fix
- MiniMax-M2.5: custom EAGLE3 draft model trained with TorchSpec framework reached 326 tok/s at peak
- All optimizations merged or in-flight to vLLM main branch — gains are broadly accessible
- Validates that "the fastest inference in the world is open source"

## Why It Matters

Open-source inference has closed the gap with hosted proprietary providers at the frontier, removing a key justification for using closed serving stacks for cost-sensitive production deployments.

---
[Source: vLLM Blog](https://vllm.ai/blog/2026-05-11-vllm-tops-artificial-analysis)
