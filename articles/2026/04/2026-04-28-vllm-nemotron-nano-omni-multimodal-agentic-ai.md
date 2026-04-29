---
title: "Run Highly Efficient Multimodal Agentic AI with NVIDIA Nemotron 3 Nano Omni Using vLLM"
date: 2026-04-28
source_url: https://vllm.ai/blog/nemotron-omni
source: vLLM Blog
type: article
topics: [ai-infra]
tags: [inference, multimodal, NVIDIA, MoE, open-source, vLLM]
saved_at: 2026-04-28
---

## Summary

NVIDIA released Nemotron 3 Nano Omni, a 30B MoE model (3B active parameters) with 256K context, now supported by vLLM. The model handles text, image, video, and audio in a single unified reasoning loop, replacing fragmented multi-model stacks. Benchmarks show 9x higher throughput versus comparable open omni models, with the model topping six industry leaderboards including MMlongbench-Doc, OCRBenchV2, and VoiceBench.

## Key Highlights

- 30B total / 3B active MoE with hybrid Transformer-Mamba architecture; 256K token context
- 9x higher throughput than other open omni models; 7.4x for multi-document, 9.2x for video use cases
- 20% higher multimodal accuracy over best open alternatives
- Supports BF16, FP8, and NVFP4 quantization on B200, H100, H200, A100, L40S, RTX 6000, and DGX Spark
- Topped six leaderboards: MMlongbench-Doc, OCRBenchV2, WorldSense, DailyOmni, VoiceBench, MediaPerf

## Why It Matters

A single efficient model replacing fragmented multimodal pipelines dramatically reduces latency, cost, and orchestration complexity for enterprise agentic workflows that must simultaneously process screens, documents, audio, and video.

---
[Source: vLLM Blog](https://vllm.ai/blog/nemotron-omni)
