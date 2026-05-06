---
title: "Understanding the Gemma 4 Family"
date: 2026-04-15
source_url: https://hfviewer.com/
source: HFViewer
type: article
topics: [genai-llm, ai-infra]
tags: [Gemma, Google, LLM, edge-inference, MoE, model-architecture, visualization, Hugging-Face]
saved_at: 2026-05-06
---

## Summary

HFViewer is a browser-based tool that lets users paste a Hugging Face URL and instantly explore an interactive architecture graph — no local setup required. Its featured article by researcher Hannes von Essen breaks down Google's Gemma 4 family across four variants (E2B, E4B, 31B, 26B-A4B), each targeting a different deployment bottleneck from flagship phones to workstations. The analysis highlights shared architectural innovations — interleaved local/global attention, per-layer embeddings in edge models, and proportional RoPE — that distinguish Gemma 4 from prior generations. The core thesis is that model selection should be driven by deployment constraints, not raw parameter count.

## Key Highlights

- **E2B / E4B edge models**: multimodal (image + audio) with per-layer text embeddings; E2B hits 52–57 GPU tokens/sec on flagship phones; E4B reaches 22–25 tokens/sec; E4B scores MMLU Pro 69.4 / GPQA 58.6
- **31B dense model**: 30.7B params, 60 layers, 256K context window — optimized for long-document processing; MMLU Pro 85.2 / GPQA 84.3
- **26B-A4B MoE model**: 25.2B total params but only 3.8B active per token (128 experts, 8 active); MMLU Pro 82.6 / GPQA 82.3 — workstation-class quality at a fraction of compute
- **Attention design**: interleaved sliding-window local attention (1024-token) + full global attention across all variants
- **Vision encoder**: flexible token budget (70–1,120 tokens) to balance image fidelity vs. latency
- **HFViewer tool**: supports overview vs. detail granularity modes; works directly from any Hugging Face model URL

## Why It Matters

Gemma 4's range from sub-5B edge models to MoE workstation variants signals that the "right" frontier model is increasingly defined by where it runs, not just how it scores on benchmarks.

---
[Source: HFViewer](https://hfviewer.com/)
