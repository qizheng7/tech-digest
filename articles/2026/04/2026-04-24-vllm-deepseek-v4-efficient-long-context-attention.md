---
title: "DeepSeek V4 in vLLM: Efficient Long-context Attention"
date: 2026-04-24
source_url: https://vllm.ai/blog/deepseek-v4
source: vLLM Blog
type: article
topics: [ai-infra]
tags: [inference, vLLM, DeepSeek, long-context, KV-cache, MoE]
saved_at: 2026-04-28
---

## Summary

vLLM added support for DeepSeek V4 Pro (1.6T params) and Flash (285B params), both with 1M-token context windows. The implementation introduces novel KV cache compression techniques that reduce per-sequence memory at 1M context from a typical 84 GiB to just 9.62 GiB — an 8.7x reduction versus DeepSeek V3.2. Three kernel fusions cut memory round-trips by 1.4–20x.

## Key Highlights

- DeepSeek V4 Pro: 1.6T parameters; V4 Flash: 285B parameters; both support 1M token context
- KV cache at 1M context: 9.62 GiB with BF16 (8.7x smaller than DeepSeek V3.2); further 2x with FP4/FP8 quantization
- Four attention strategies: shared KV vectors (2x memory savings), c4a/c128a compression, DeepSeek Sparse Attention, 128-token sliding window
- Three kernel fusions reducing memory round-trips 1.4–20x
- 5–6% end-to-end latency reduction at low batch sizes via multi-stream parallelization
- Unified 256-token native logical block size consolidating five cache types into three page-size buckets

## Why It Matters

Practical systems engineering for 1M-token context inference demonstrates how architectural innovation plus low-level optimization can make extreme-length inference viable in production without requiring specialized hardware.

---
[Source: vLLM Blog](https://vllm.ai/blog/deepseek-v4)
