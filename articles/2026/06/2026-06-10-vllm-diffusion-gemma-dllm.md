---
title: "DiffusionGemma: The First Diffusion LLM (dLLM) Natively Supported in vLLM"
date: 2026-06-10
source_url: https://vllm.ai/blog/2026-06-10-diffusion-gemma
source: vLLM
type: article
topics: [ai-infra, genai-llm]
tags: [vLLM, DiffusionGemma, diffusion-LLM, dLLM, Gemma4, architecture, parallel-decoding, FP8, throughput, inference, open-source]
saved_at: 2026-06-15
---

## Summary

vLLM announced native support for DiffusionGemma, a 26B-parameter discrete diffusion language model built on the Gemma4 backbone — the first dLLM integrated into a major inference engine. Unlike autoregressive models that generate tokens left-to-right, DiffusionGemma denoises a fixed 256-token canvas simultaneously using bidirectional attention and entropy-bound sampling. This architecture eliminates sequential token dependencies, enabling dramatically higher throughput at low batch sizes while maintaining generation quality.

## Key Highlights

- Architecture: iterative refinement over a 256-token canvas; uncertain tokens replaced with random tokens and re-denoised
- FP8 quantized on H200: **1,288 tokens/second** — roughly 6× faster than autoregressive baselines, 3× faster than multi-token prediction
- FP8 quantized on H100: **1,008 tokens/second** — ~5× and 2.6× improvements respectively
- Bidirectional attention during denoising: every position attends to every other position within the canvas
- Self-conditioning: model conditions on its own previous predictions between denoising steps
- Particularly efficient at low batch sizes, trading compute for reduced memory bandwidth pressure

## Why It Matters

Diffusion LLMs challenge the autoregressive paradigm for text generation — their native integration into vLLM signals that dLLMs are mature enough for production serving and may become a serious alternative for latency-sensitive applications.

---
[Source: vLLM](https://vllm.ai/blog/2026-06-10-diffusion-gemma)
