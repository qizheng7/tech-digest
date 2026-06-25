---
title: "Qwen-AgentWorld: Language World Models for Reliable AI Agents"
date: 2026-06-23
source_url: https://qwen.ai/research
source: Alibaba Qwen
type: article
topics: [genai-llm, ai-infra]
tags: [Qwen, AgentWorld, language-world-model, MoE, open-source, agents, benchmark, vLLM, SGLang, Apache-2]
saved_at: 2026-06-25
---

## Summary

Alibaba Qwen released Qwen-AgentWorld, a language world model that simulates what tools and environments return when an agent takes an action — across seven domains: MCP, Search, Terminal, Software Engineering (SWE), Android, Web, and OS. Rather than training directly as an agent, the model learns to predict environment observations, and this world-modeling capability transfers to improved multi-turn agent performance. Qwen-AgentWorld-35B-A3B (35B total / 3B active MoE, Apache-2.0) is the open release; the 397B-A17B flagship outperforms GPT-5.4 and Claude Opus 4.8 on AgentWorldBench.

## Key Highlights

- Two variants: Qwen-AgentWorld-397B-A17B (flagship, outperforms GPT-5.4 and Claude Opus 4.8 on AgentWorldBench) and Qwen-AgentWorld-35B-A3B (practical open release, Apache-2.0)
- 35B-A3B: 35B total / 3B active MoE, 262K-token context, compatible with vLLM and SGLang
- Trained to simulate 7 environments (MCP, Search, Terminal, SWE, Web, OS, Android) in a single model
- Key finding: single-turn environment prediction training transfers to multi-turn agent task performance gains across both in-domain and out-of-domain benchmarks
- Includes AgentWorldBench evaluation set: scores format, factuality, consistency, realism, and quality — not just answer correctness
- Full release package: model weights, benchmark, technical report, and vLLM/SGLang/Transformers deployment examples

## Why It Matters

Qwen-AgentWorld introduces a new training paradigm where world modeling (predicting environment responses) is used as a scalable path to agent capability — potentially more generalizable than task-specific agent fine-tuning.

---
[Source: Alibaba Qwen](https://qwen.ai/research)
