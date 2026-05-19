---
title: "How Snapchat Serves a Billion Predictions Per Second"
date: 2026-05-19
source_url: https://blog.bytebytego.com/p/how-snapchat-serves-a-billion-predictions
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, ai-infra]
tags: [Snapchat, Snap, Bento, ML-platform, recommendation, ranking, inference, feature-store, GPU-CPU-split, serialization, train-serve-skew, Kubeflow, TensorFlow, incremental-training]
saved_at: 2026-05-19
---

## Summary

ByteByteGo breaks down Snap's "Bento" ML platform — the system serving over a billion predictions per second for 474 million daily users across content ranking, ad serving, friend suggestions, and AR lenses. The core architectural insight is that ranking workloads are fundamentally asymmetric: one user request expands into hundreds/thousands of (user, candidate) model evaluations before collapsing back to a ranked list. Every decision in Bento flows from managing that fanout at billion-user scale while keeping latency under 100ms, maintaining freshness, and allowing hundreds of ML experiments per day.

## Key Highlights

- **Scale**: 1B+ predictions/second; 1 TB/s of feature reads; 10 trillion events/day; 800 TB online feature store; 100,000+ GPU training hours/day
- **GPU/CPU compute split at export time**: dense matrix math → GPU, embedding lookups + feature parsing → CPU; the same trained model exports to hardware-specific versions
- **Feature store dual existence**: offline (Apache Iceberg via Spark/Robusta) + online (key-value store) must stay in sync; train/serve skew is "the central operational concern of every mature ML team"
- **High-fanout strategies**: (1) co-locate document features on inference instances to eliminate network fanout; (2) dedicated Retrieval service with ANN search for corpora too large for per-instance memory
- **Biggest optimization**: redesigning APIs to transfer features as raw bytes with deserialization only inside the inference engine → **2× lower latency, 10× cheaper data plane costs**
- **Continuous feedback loop**: every prediction + user response feeds incremental retraining; model deployment via Kubernetes-style reconciliation (desired vs. actual state)
- **Growth headroom**: over 2 years, ranking model size grew 20×, training data grew 40× — platform absorbed it in normal operation

## Why It Matters

Bento's architecture shows that at scale, the boring machinery — serialization, RPC framing, feature transport — often dominates cost more than the model itself, and investing in the feedback loop is what lets the platform absorb order-of-magnitude growth without rewrites.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-snapchat-serves-a-billion-predictions)
