---
title: "NVIDIA Achieves Leading Agentic Coding Performance on First Agentic AI Benchmark"
date: 2026-06-12
source_url: https://developer.nvidia.com/blog/nvidia-achieves-leading-agentic-coding-performance-on-first-agentic-ai-benchmark/
source: NVIDIA
type: article
topics: [ai-infra]
tags: [NVIDIA, GB300, NVL72, benchmark, agentic-coding, AA-AgentPerf, Artificial-Analysis, inference, MoE, WideEP, DeepEP, energy-efficiency]
saved_at: 2026-06-15
---

## Summary

NVIDIA's GB300 NVL72 achieved top results on AA-AgentPerf (Artificial Analysis AgentPerf), the industry's first benchmark specifically designed to profile real-world AI agent coding workflows. The benchmark measures performance under realistic agentic conditions with interleaved LLM calls and tool use — conditions that previous benchmarks did not capture. Key gains came from WideEP/DeepEP mixture-of-experts scaling, DeepGEMM kernels, and NVLink fabric connecting 72 GPUs for parameter and KV-cache sharing.

## Key Highlights

- **61,400 concurrent agents per megawatt** on GB300 NVL72 vs. 2,600 on H200 — a **20× improvement per megawatt**
- **57.5 concurrent agents per GPU** vs. 1.4 for H200 — a **41× per-GPU improvement**
- AA-AgentPerf benchmarks trajectories with non-deterministic interleaved LLM calls and tool use
- Optimization stack: WideEP/DeepEP for MoE scaling, DeepGEMM kernels, NVLink fabric across 72 GPUs
- Benchmark is multi-vendor and open — designed to become an industry standard for agentic evaluation

## Why It Matters

AA-AgentPerf fills a critical gap in AI infrastructure benchmarking; NVIDIA's massive efficiency lead on concurrent agentic workloads underscores how much the GB300 generation was co-designed for the multi-agent era.

---
[Source: NVIDIA](https://developer.nvidia.com/blog/nvidia-achieves-leading-agentic-coding-performance-on-first-agentic-ai-benchmark/)
