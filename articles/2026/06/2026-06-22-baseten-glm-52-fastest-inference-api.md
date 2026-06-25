---
title: "How we built the world's fastest API for GLM-5.2"
date: 2026-06-22
source_url: https://www.baseten.co/blog/how-we-built-the-worlds-fastest-api-for-glm-52/
source: Baseten
type: article
topics: [ai-infra]
tags: [GLM-5.2, inference, Blackwell, NVFP4, speculative-decoding, disaggregation, KV-cache, MTP, DSA]
saved_at: 2026-06-25
---

## Summary

Baseten details how they achieved 280+ tokens/second for GLM-5.2 — the fastest deployment measured by Artificial Analysis — using a stack of optimizations on NVIDIA Blackwell GPUs. The post covers four key techniques: NVFP4 quantization, KV-aware routing, prefill/decode disaggregation, and Multi-Token Prediction speculative decoding, plus custom runtime support for GLM-5.2's unique DSA (Distributed Sparse Attention) architecture.

## Key Highlights

- **280+ tok/s** for GLM-5.2, fastest on Artificial Analysis leaderboard at time of publication
- **NVFP4 quantization** from original FP8 weights using dual scale factors; quality validated on BFCL function calling benchmark
- **KV-aware routing** via NVIDIA Dynamo: routes requests to replicas with cached relevant context, reducing prefill cost and improving TTFT
- **Prefill/decode disaggregation** achieved 2x higher tokens/second vs unified approaches; NVIDIA Dynamo handles orchestration and KV transfer
- **Multi-Token Prediction (MTP) heads** enable multiple tokens per forward pass with lossless verification
- Custom runtime updates to support GLM-5.2's DSA (Distributed Sparse Attention) shared weights

## Why It Matters

This post demonstrates that production-grade optimization of frontier open models now requires deep hardware-software co-optimization — the same engineering discipline previously only applied to proprietary model serving is increasingly necessary for open-weight deployments.

---
[Source: Baseten](https://www.baseten.co/blog/how-we-built-the-worlds-fastest-api-for-glm-52/)
