---
title: "Google Accelerates Gemma 4 with Multi-Token Prediction Drafters: Up to 3x Faster Inference"
date: 2026-05-05
source_url: https://ai.google.dev/gemma/docs/mtp/overview
source: Google AI for Developers
type: article
topics: [ai-infra, genai-llm]
tags: [Google, Gemma, speculative-decoding, MTP, inference, open-source, throughput, latency, llama-cpp, vLLM, SGLang]
saved_at: 2026-05-06
---

## Summary

Google released Multi-Token Prediction (MTP) drafter checkpoints for the full Gemma 4 model family, promising up to 3x faster decoding with zero quality degradation. The approach integrates a smaller draft model that shares Gemma 4's embedding layer and uses activations from the target model's final layer — minimizing overhead while enabling parallel token verification. Drafters are available under Apache 2.0 on Hugging Face and Kaggle, with day-0 support across Transformers, vLLM, SGLang, Ollama, MLX, and AI Edge.

## Key Highlights

- Up to 3x faster text generation via speculative decoding, with guaranteed identical output quality vs. standard autoregressive generation
- Draft model shares the target model's embeddings and final-layer activations — minimal additional overhead
- Available for all Gemma 4 sizes: 31B-it, 26B-A4B-it, E4B-it, E2B-it; the E2B drafter is only 78M parameters
- Broad ecosystem day-0 support: Transformers, vLLM, SGLang, Ollama, MLX, AI Edge, and llama.cpp (beta via PR #22673)
- llama.cpp MTP tests show ~75% acceptance rate with 3 draft tokens and >2x throughput on Qwen3 27B/35B
- Speedups vary by hardware — 26B variant may not improve single-sequence latency on platforms without strong parallelism

## Why It Matters

Open-model speculative decoding with ecosystem-wide same-day support sets a new standard for inference efficiency in open-weight models, closing the latency gap between Gemma 4 and proprietary serving infrastructure.

---
[Source: Google AI for Developers](https://ai.google.dev/gemma/docs/mtp/overview)
