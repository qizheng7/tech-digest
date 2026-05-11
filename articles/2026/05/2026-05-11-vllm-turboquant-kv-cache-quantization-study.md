---
title: "A First Comprehensive Study of TurboQuant: Accuracy and Performance"
date: 2026-05-11
source_url: https://vllm.ai/blog/turboquant
source: vLLM Blog
type: article
topics: [ai-infra]
tags: [vLLM, KV-cache, quantization, TurboQuant, FP8, BF16, inference, benchmark, accuracy, throughput]
saved_at: 2026-05-11
---

## Summary

vLLM published the first comprehensive evaluation of TurboQuant, a KV-cache quantization technique that compresses key-value storage to 3–4 bits while dequantizing back to BF16 for attention computation. The study benchmarks six TurboQuant variants (k8v4, 4bit-nc, k3v4-nc, 3bit-nc, etc.) against FP8 and BF16 baselines across accuracy and throughput dimensions, finding that aggressive 3-bit variants show meaningful accuracy degradation — up to 20 points on reasoning benchmarks — while FP8 remains the recommended default for production deployments.

## Key Highlights

- FP8 provides 2x KV-cache capacity with negligible accuracy loss and no throughput cost — the recommended default for most deployments
- TurboQuant variants add 10–68% latency overhead and reduce throughput to 66–80% of BF16, due to dequantization costs not present in FP8
- Aggressive 3-bit variants show drastic accuracy drops on math and coding benchmarks; quantization errors accumulate with sequence length
- k8v4 (8-bit keys, 4-bit values) offers no advantage over FP8 with only modest additional memory savings
- 4bit-nc provides a viable memory-throughput tradeoff for memory-constrained deployments but requires per-model validation
- In memory-constrained scenarios, TurboQuant reduces queuing delays significantly by fitting more sequences in memory

## Why It Matters

This is the first rigorous, multi-model study of TurboQuant's real production tradeoffs, providing practitioners with concrete guidance on when sub-FP8 quantization is worth the accuracy and throughput costs.

---
[Source: vLLM Blog](https://vllm.ai/blog/turboquant)
