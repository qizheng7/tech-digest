---
title: "Announcing vime: A Simple, Stable, and Efficient RL Framework for LLMs"
date: 2026-06-09
source_url: https://vllm.ai/blog/2026-06-09-announcing-vime
source: vLLM
type: article
topics: [ai-infra, genai-llm]
tags: [vLLM, vime, RL, post-training, GRPO, PPO, MoE, slime, GB200, H200, routing-replay, open-source, training-inference-alignment]
saved_at: 2026-06-15
---

## Summary

vLLM announced vime, a unified RL post-training framework that merges slime's training stack with vLLM's inference engine. The framework supports GRPO and PPO algorithms across architectures including Qwen3 and GLM-4.5, and solves the training-inference alignment problem for MoE models via R3 (routing replay), which ensures logprob consistency across training and rollout steps.

## Key Highlights

- Three core principles: **Simple** (adopts slime conventions + vLLM arg passing), **Stable** (R3 routing replay for MoE alignment), **Flexible** (multi-hardware support with abstracted training/rollout resources)
- R3 routing replay reduces logprob drift: from 0.019 to 0.013 on Qwen3-30B-A3B MoE
- Baseline drift without R3: logprob differences reach 0.77; with vime alignment held to ~0.011
- GB200 vs H200: ~1.72× faster step speeds for Qwen3-30B-A3B MoE
- Supports GRPO and PPO; tested on Qwen3 and GLM-4.5 families

## Why It Matters

vime directly addresses one of the core pain points in LLM post-training — training-inference distribution mismatch — by unifying the two stacks, making RL fine-tuning more reliable and accessible for production teams.

---
[Source: vLLM](https://vllm.ai/blog/2026-06-09-announcing-vime)
