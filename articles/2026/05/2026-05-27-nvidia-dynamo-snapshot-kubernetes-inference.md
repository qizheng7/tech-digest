---
title: "NVIDIA Dynamo Snapshot: 21x Faster Cold Start for Inference on Kubernetes"
date: 2026-05-27
source_url: https://developer.nvidia.com/blog/nvidia-dynamo-snapshot-fast-startup-for-inference-workloads-on-kubernetes/
source: NVIDIA
type: article
topics: [ai-infra]
tags: [NVIDIA, Dynamo, Kubernetes, inference, cold-start, CRIU, checkpoint-restore, elastic-scaling, GPU, KV-cache]
saved_at: 2026-05-31
---

## Summary

NVIDIA released Dynamo Snapshot, a checkpoint/restore system for AI inference workloads on Kubernetes that uses CRIU (Checkpoint/Restore in Userspace) combined with CUDA driver checkpointing to serialize CPU and GPU process states. The system achieves up to 21x startup time reduction on large models like gpt-oss-120b, directly addressing the production pain point where cold-starting inference workers can take several minutes while GPUs are allocated but idle. Three combined optimizations drive the speedup: KV cache deallocation to minimize checkpoint size, CRIU enhancements (parallel restoration + async I/O), and a GPU Memory Service that decouples weight restoration from process-state recovery via faster transfer channels.

## Key Highlights

- **Up to 21x startup time reduction** on gpt-oss-120b
- Uses **CRIU + CUDA driver checkpointing** to serialize full CPU + GPU state
- **KV cache deallocation** before checkpoint reduces checkpoint size significantly
- **GPU Memory Service**: decouples weight restoration from process-state recovery for concurrent transfers
- Enables elastic scaling without minutes of GPU idle time during traffic spikes
- Addresses SLA violation risk when inference demand spikes unexpectedly on Kubernetes

## Why It Matters

Eliminating inference cold-start latency makes serverless and elastic GPU deployments economically viable at production scale — GPUs no longer sit idle during startup, and systems can absorb traffic spikes without pre-warming large fleets.

---
[Source: NVIDIA](https://developer.nvidia.com/blog/nvidia-dynamo-snapshot-fast-startup-for-inference-workloads-on-kubernetes/)
