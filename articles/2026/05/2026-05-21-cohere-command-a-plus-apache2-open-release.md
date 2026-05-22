---
title: "Cohere Releases Command A+: 218B Apache 2.0 Open Model for Sovereign Enterprise AI"
date: 2026-05-21
source_url: https://venturebeat.com/technology/cohere-cracks-lossless-quantization-and-native-citations-with-first-full-apache-2-0-licensed-open-model-command-a
source: VentureBeat
type: article
topics: [genai-llm, ai-infra]
tags: [Cohere, Command-A-plus, open-source, Apache-2.0, MoE, quantization, enterprise, sovereign-AI, multimodal, vLLM, citation, RAG, open-weights]
saved_at: 2026-05-21
---

## Summary

Cohere released Command A+, its first fully open-weight model under the Apache 2.0 license. The 218B parameter sparse Mixture-of-Experts model (25B active parameters per token) runs on as few as two NVIDIA H100 GPUs at W4A4 quantization or a single NVIDIA B200, making it the most hardware-accessible frontier-class enterprise model yet from the company. Command A+ supports 48 languages, multimodal document processing, and introduces native citation generation via embedded "grounding spans" that link every claim to its source. vLLM shipped day-0 support on release.

## Key Highlights

- **218B MoE / 25B active parameters** — Apache 2.0 license, available on HuggingFace; Cohere's first fully open model.
- **Runs on 2× H100s at W4A4** or 1× NVIDIA B200 — achieved via Quantization-Aware Distillation (QAD) that keeps attention layers at full precision while quantizing MoE experts to 4-bit with nearly lossless accuracy.
- **Native citation generation:** generates explicit grounding spans linking claims to source documents — purpose-built for RAG and document-processing workflows.
- **48 language support** (up from 23), with improved translation and multilingual reasoning.
- **Artificial Analysis Intelligence Index score: 37** — around Claude 4.5 Haiku territory, with strong non-hallucination but weaker scientific reasoning and coding than top-tier models.
- **Unusual architecture:** parallel transformer blocks, large shared expert usage, LayerNorm over RMSNorm, and relatively shallow 32-layer depth drew significant community analysis.

## Why It Matters

Command A+ is the most significant move yet toward permissively-licensed, production-deployable enterprise frontier models — putting Apache 2.0 open weights in a class that was previously closed-weights-only, and targeting the sovereign AI market where data cannot leave on-premise infrastructure.

---
[Source: VentureBeat](https://venturebeat.com/technology/cohere-cracks-lossless-quantization-and-native-citations-with-first-full-apache-2-0-licensed-open-model-command-a)
