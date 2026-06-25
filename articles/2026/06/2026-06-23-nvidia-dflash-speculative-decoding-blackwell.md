---
title: "Boost Inference Performance up to 15x on NVIDIA Blackwell Using DFlash Speculative Decoding"
date: 2026-06-23
source_url: https://developer.nvidia.com/blog/boost-inference-performance-up-to-15x-on-nvidia-blackwell-using-dflash-speculative-decoding/
source: NVIDIA
type: article
topics: [ai-infra]
tags: [DFlash, speculative-decoding, Blackwell, vLLM, SGLang, inference, throughput, EAGLE-3, diffusion-drafter]
saved_at: 2026-06-25
---

## Summary

NVIDIA published results showing DFlash speculative decoding delivers up to 15x throughput improvement on Blackwell GPUs for GPT-oss-120B at high interactivity levels. DFlash replaces the traditional autoregressive drafter with a lightweight block-diffusion model that predicts entire token blocks in single forward passes, addressing the core bottleneck of sequential token generation in LLM serving.

## Key Highlights

- **15x throughput boost** for gpt-oss-120b on Blackwell at high interactivity (500–600 tok/s per user)
- **~2x improvement over EAGLE-3** for Llama 3.1 8B on interactivity metrics
- **5.8x speedup** for Gemma 4 31B on vLLM; **5.1x** for Qwen3 8B on SGLang
- Block-diffusion drafter predicts entire token blocks in single forward passes vs. one token at a time for autoregressive drafters
- Benchmarked across coding, reasoning, RAG, and multilingual tasks — not just synthetic workloads
- Enables serving more concurrent users while maintaining per-user latency SLAs critical for agentic workflows

## Why It Matters

DFlash marks a generational step for speculative decoding — moving from autoregressive to diffusion-based drafters unlocks Blackwell's parallel compute capabilities in a way prior approaches couldn't, making agentic AI serving at scale economically viable.

---
[Source: NVIDIA](https://developer.nvidia.com/blog/boost-inference-performance-up-to-15x-on-nvidia-blackwell-using-dflash-speculative-decoding/)
