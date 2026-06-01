---
title: "vLLM on the DGX Spark: Architecture, Configuration, and Local Evaluation"
date: 2026-06-01
source_url: https://vllm.ai/blog/2026-06-01-vllm-dgx-spark
source: vLLM
type: article
topics: [ai-infra]
tags: [vLLM, NVIDIA, DGX-Spark, Blackwell, sm_121, unified-memory, NVFP4, local-inference, MoE, Nemotron, KV-cache]
saved_at: 2026-05-31
---

## Summary

vLLM published a detailed technical evaluation of running inference on NVIDIA's DGX Spark, which uses Blackwell (sm_121) silicon with a unified 128GB CPU-GPU memory pool. The key finding is that the DGX Spark is best suited as a local single-user or small-batch inference target for large NVFP4 MoE models in the 100-130B parameter range (10-15B active), where the shared memory architecture allows hosting models up to 200B parameters locally. Testing Nemotron-3-Super-120B yielded 22.7–23.7 tokens/second decode throughput, with near-linear prefill scaling from 140 to 1,880 tok/s as prompt length grew. A critical operational note: pre-warm the JIT compiler to avoid a ~25-second cold-start latency on the first request.

## Key Highlights

- **DGX Spark architecture**: sm_121 Blackwell, unified 128GB CPU-GPU memory pool — fundamentally changes serving strategies
- **Best model class**: 100-130B MoE NVFP4 with 10-15B active params; can host up to 200B parameters locally
- **Nemotron-3-Super-120B**: 22.7–23.7 tok/s decode, prefill scales 140→1,880 tok/s linearly with prompt length
- **TTFT**: 0.42s (58 tokens) to 3.85s (7,234 tokens)
- **Three critical flags**: `--gpu-memory-utilization 0.85`, `--max-num-seqs 4`, `--max-model-len 131072`
- **JIT pre-warming** required to avoid 25-second first-request cold start

## Why It Matters

DGX Spark brings datacenter-class MoE inference to local workstations — this guide establishes the correct mental model (single-user throughput target, not a mini-cluster) and the exact configuration to achieve it without trial-and-error.

---
[Source: vLLM](https://vllm.ai/blog/2026-06-01-vllm-dgx-spark)
