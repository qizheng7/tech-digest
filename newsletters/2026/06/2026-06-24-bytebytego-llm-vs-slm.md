---
title: "Large Language Models vs Small Language Models"
date: 2026-06-24
source_url: https://blog.bytebytego.com/p/large-language-models-vs-small-language
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm, ai-infra]
tags: [LLM, SLM, KV-cache, Chinchilla, knowledge-distillation, speculative-decoding, GQA, Phi, Gemma, on-device]
saved_at: 2026-06-25
---

## Summary

ByteByteGo explains that the LLM vs. SLM distinction is a downstream consequence of three converging constraints — deployment target, inference economics, and training budget — rather than an arbitrary size choice. The article traces how those constraints drive divergent decisions in architecture, training methodology, and deployment strategy, closing with the argument that production systems in 2026 nearly always compose both model classes rather than picking one.

## Key Highlights

- **Parameter size in 2026:** SLMs = 0.5B–14B parameters; LLMs = tens to hundreds of billions. Both use transformer decoder stacks trained with pretraining → SFT → RLHF
- **KV cache is the critical SLM constraint:** grows linearly with sequence length and often dominates memory more than model weights. Grouped-query attention (GQA) reduces cache footprint by ~4x (32 query heads share 8 KV groups) with "minimal quality loss" — used in Llama, Qwen, Gemma, and most modern SLMs
- **Chinchilla overtraining:** 2022 Chinchilla showed ~20 tokens/parameter as compute-optimal, but modern SLMs deliberately train on "many trillions of tokens" — trading higher training cost for lower per-request inference cost at deployment scale
- **Data quality over volume (Phi lineage):** Microsoft's 2023 "Textbooks Are All You Need" trained a 1.3B parameter coding model on ~7B tokens of curated/synthetic data and matched models trained on hundreds of billions of raw tokens
- **Knowledge distillation:** Gemma 2 9B was trained by mimicking a larger teacher's output distribution; 27B version trained from scratch. Richer training signal helps small students learn patterns they'd miss from raw text
- **Three hybrid production patterns:** Routing (small handles easy, escalates hard); Guardrails (small filters inputs/outputs around large core); Speculative decoding (small drafter generates candidates, large model verifies in batch). Apple's on-device system uses speculative decoding

## Why It Matters

Production AI systems are converging on compositions of SLMs and LLMs rather than choosing one — the architectural choices made at training time (GQA, overtraining, distillation) directly determine where in a hybrid stack each model can cost-effectively serve.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/large-language-models-vs-small-language)
