---
title: "DeepSeek Releases DSpark: Semi-Autoregressive Speculative Decoding, 60–85% Faster V4 Generation"
date: 2026-06-27
source_url: https://www.marktechpost.com/2026/06/27/deepseek-releases-dspark-a-speculative-decoding-framework-that-accelerates-deepseek-v4-per-user-generation-60-85-over-mtp-1/
source: DeepSeek / MarkTechPost
type: article
topics: [ai-infra, genai-llm]
tags: [DeepSeek, DSpark, speculative-decoding, inference, DeepSpec, Eagle3, DFlash, MTP, Qwen3, open-source, throughput, latency, confidence-head, semi-autoregressive]
saved_at: 2026-06-30
---

## Summary

DeepSeek (with Peking University) open-sourced DSpark on June 27, 2026 — a new speculative decoding framework that accelerates DeepSeek-V4 per-user generation by 60–85% over the MTP-1 baseline, and raises accepted token length 27–31% over Eagle3 and 16–18% over DFlash. DSpark introduces a semi-autoregressive architecture (parallel backbone + sequential Markov head) and a hardware-aware prefix scheduler that dynamically adjusts verification length based on GPU load. The accompanying **DeepSpec** codebase (MIT-licensed) provides a complete training and evaluation toolkit. No target model retraining is required.

## Key Highlights

- **Semi-autoregressive design**: parallel backbone generates base logits for all positions simultaneously; a sequential Markov head (rank 256) adds prefix-dependent bias before sampling to fix "multi-modal collision" and suffix decay
- **Confidence head**: estimates per-position token survival probability, calibrated via Sequential Temperature Scaling (reduces calibration error from 3–8% to ~1%)
- **Load-aware prefix scheduler**: verifies more tokens when GPU is idle, fewer under congestion — maintains lossless output via early-stopping rules; overhead only 0.2–1.3% latency when scaling 4→16 tokens
- **Benchmarks vs Eagle3** (macro-avg accepted length): +30.9% on Qwen3-4B, +26.7% on Qwen3-8B, +30.0% on Qwen3-14B
- **Benchmarks vs DFlash**: +16.3% on Qwen3-4B, +18.4% on Qwen3-8B, +18.3% on Qwen3-14B
- **Production on V4**: 60–85% per-user speedup (Flash), 57–78% (Pro) vs. MTP-1 baseline
- **Open-sourced**: `DeepSeek-V4-Pro-DSpark` and `DeepSeek-V4-Flash-DSpark` checkpoints + DeepSpec MIT-licensed training/eval codebase on Hugging Face; no fine-tuning of the target model required

## Why It Matters

DSpark sets a new single-GPU speculative decoding benchmark and ships a complete open-source toolkit (DeepSpec) for training custom draft models on any target — making frontier-grade speculative decoding accessible to anyone serving open-weight models, not just labs running proprietary inference stacks.

---
[Source: MarkTechPost](https://www.marktechpost.com/2026/06/27/deepseek-releases-dspark-a-speculative-decoding-framework-that-accelerates-deepseek-v4-per-user-generation-60-85-over-mtp-1/)
