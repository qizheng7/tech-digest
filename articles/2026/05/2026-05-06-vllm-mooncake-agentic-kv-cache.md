---
title: "Serving Agentic Workloads at Scale with vLLM x Mooncake"
date: 2026-05-06
source_url: https://vllm.ai/blog/mooncake-store
source: vLLM Blog
type: article
topics: [ai-infra]
tags: [vLLM, inference, agentic, KV-cache, RDMA, distributed, Mooncake, throughput, serving]
saved_at: 2026-05-06
---

## Summary

vLLM integrated Mooncake's distributed KV cache storage system to dramatically improve serving efficiency for agentic (multi-turn, tool-using) AI workloads. Instead of each vLLM instance managing its own isolated KV cache, the system introduces a cluster-wide Mooncake Store that all instances share, enabling cache reuse across different servers when routing agentic requests. The key insight is that agentic workloads have an unusually high input-to-output ratio (~131:1) with heavily repeated prefixes, making distributed caching the dominant lever for efficiency at scale.

## Key Highlights

- **3.8x throughput improvement**, 46x reduction in time-to-first-token (TTFT), and 8.6x lower end-to-end latency on realistic agentic traces with 12 GB200 GPUs
- Cache hit rate jumped from 1.7% (standard round-robin) to 92.2% with Mooncake distributed caching
- At 60 GPUs with round-robin routing, maintained >95% cache hit rates with near-linear scaling
- Uses GPUDirect RDMA for SM-free data transfer — KV blocks move directly between GPU memory and CPU storage without consuming GPU streaming multiprocessors
- All RDMA operations run on a dedicated background I/O thread, keeping the main execution path non-blocking
- A master metadata server tracks cache locations and health across worker nodes

## Why It Matters

Agentic workloads are fundamentally different from single-turn inference — the massive input reuse means a distributed cache pool can deliver near-linear scaling gains that isolated per-node caches simply cannot achieve.

---
[Source: vLLM Blog](https://vllm.ai/blog/mooncake-store)
