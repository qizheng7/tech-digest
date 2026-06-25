---
title: "EP219: 12 Open-source LLMs"
date: 2026-06-20
source_url: https://blog.bytebytego.com/p/ep219-12-open-source-llms
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm, ai-infra]
tags: [open-source, LLM, SLM, Claude-Code, multi-agent, single-agent, DeepSeek, GLM, Kimi, OLMo, Nemotron]
saved_at: 2026-06-25
---

## Summary

ByteByteGo's weekly digest covers four topics: a curated list of 12 open-source LLMs with one standout strength each, an SLM vs. LLM comparison across production dimensions, a decision framework for single-agent vs. multi-agent architectures, and a breakdown of Claude Code's 7 permission modes.

## Key Highlights

- **12 open-source LLMs highlighted:** DeepSeek V4 (MoE, MIT, native 1M-token context, near-frontier perf); GLM 5.1 (first open-weight to top SWE-Bench Pro, MIT); Kimi K2.6 (competitive with closed models on coding, Modified MIT); OLMo 2 / AI2 (most complete open-source reproducibility — weights, data, code, recipes, Apache 2.0); Nemotron 3 Super (NVIDIA hybrid MoE, 1M context, fully open, strong agentic coding)
- **SLM production profile:** <10B parameters, laptop/phone deployment, low latency, low cost, privacy-sensitive workloads; LLMs 10B+, GPU-required, complex math and multi-step reasoning
- **Single vs. multi-agent rule:** Single agent when the task is linear and fits in one context window; multi-agent when subtasks can parallelize, independent verification is needed, or the problem is too large. "Start with a single agent. Move to multi-agent only when context or reliability become the bottleneck."
- **Claude Code permission modes (5 user-selectable):** `plan`, `default`, `acceptEdits`, `dontAsk`, `bypassPermissions`; plus `auto` (feature-flagged) and `bubble` (internal subagent escalation only)
- Claude Fable 5 referenced in the digest as a recent major release

## Why It Matters

This week's digest captures the moment when open-source LLMs became genuinely competitive with closed frontier models for production agentic workloads, making the build-vs-buy decision for inference infrastructure significantly more nuanced.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/ep219-12-open-source-llms)
