---
title: "How the NVIDIA Vera Rubin Platform Is Solving Agentic AI's Scale-Up Problem"
date: 2026-05-14
source_url: https://developer.nvidia.com/blog/how-the-nvidia-vera-rubin-platform-is-solving-agentic-ais-scale-up-problem/
source: NVIDIA Developer Blog
type: article
topics: [ai-infra]
tags: [NVIDIA, Vera-Rubin, Groq-LPX, inference, agentic, hardware, throughput, disaggregation, MoE, HBM4]
saved_at: 2026-05-17
---

## Summary

NVIDIA's Vera Rubin platform combines Vera Rubin NVL72 GPUs (3,600 PFLOPS, 20.7 TB HBM4) with the Groq 3 LPX accelerator via NVIDIA Dynamo orchestration to address agentic AI's non-deterministic compute patterns. The key innovation is Attention-FFN Disaggregation: separating prefill/attention from FFN decode across specialized hardware to optimize latency-throughput tradeoffs. The platform claims 400 tok/s per user on trillion-parameter MoE models, 35× higher throughput per megawatt versus GB200 NVL72, and 10× more revenue opportunity for agentic workloads.

## Key Highlights

- 640 TB/s scale-up bandwidth at 256-LPU rack level; 128 GB unified SRAM per rack
- 400 tok/s per user on trillion-parameter MoE models with 400K-token context
- 35× higher throughput per megawatt vs GB200 NVL72
- Groq 3 LPX: 96 high-radix C2C links at 112 Gbps; compiler-scheduled data movement; hardware-driven plesiosynchronous timing
- Attention-FFN Disaggregation: Vera Rubin NVL72 handles prefill/attention; LPX handles FFN decode
- NVIDIA Dynamo orchestration layer manages the disaggregated serving pipeline

## Why It Matters

Agentic workloads with non-deterministic trajectories and variable context lengths stress standard GPU serving in ways that batch training does not — Vera Rubin's co-designed architecture is NVIDIA's answer to the inference efficiency era at extreme scale.

---
[Source: NVIDIA Developer Blog](https://developer.nvidia.com/blog/how-the-nvidia-vera-rubin-platform-is-solving-agentic-ais-scale-up-problem/)
