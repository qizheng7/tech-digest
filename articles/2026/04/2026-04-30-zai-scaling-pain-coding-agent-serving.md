---
title: "Scaling Pain of Coding Agent Serving"
date: 2026-04-30
source_url: https://z.ai/blog/scaling-pain
source: Z.AI Blog
type: article
topics: [ai-infra]
tags: [inference, KV-cache, coding-agents, race-condition, PD-disaggregation, HiCache, SGLang, GLM-5, speculative-decoding, throughput]
saved_at: 2026-04-30
---

## Summary

Z.AI's GLM-5 team shares a detailed production postmortem on inference stability failures encountered while serving hundreds of millions of Coding Agent requests daily. Users reported garbled outputs, repetition, and rare-character generation — bugs that appeared only under high-concurrency, long-context workloads and were nearly impossible to reproduce offline. After weeks of investigation, the team traced the failures to two independent low-level race-condition bugs — one in KV Cache management under PD disaggregation, one in HiCache's load pipeline — fixed both, and shipped a throughput optimization (LayerSplit) that yields 10–132% gains on long-context agent workloads.

## Key Highlights

- **Bug #1 — KV Cache race under PD disaggregation:** When Decode timed out and aborted a request, it reclaimed and reused KV Cache slots without properly notifying the Prefill side. In-flight RDMA writes from the original Prefill then overwrote the memory already assigned to a new request, corrupting its KV Cache. Fix: explicit synchronization requiring Prefill to confirm all writes are complete before Decode reclaims slots. Error rate dropped from ~0.1% to below 0.03%.
- **Bug #2 — Missing load-use ordering in HiCache:** The DSA-based HiCache implementation ran Load and Forward streams asynchronously without enforcing that the Indexer cache was fully loaded before the Forward stream began, causing read-before-ready access to uninitialized KV data. Fix: explicit synchronization constraint between the two streams.
- **Anomaly detection via speculative decoding:** The team repurposed speculative decoding metrics (`spec_accept_length` for garbled/rare-char outputs, `spec_accept_rate` for repetition) as a real-time quality signal — an elegant dual-use of a performance optimization technique.
- **LayerSplit optimization:** Coding Agent workloads average 70K+ token inputs with high prefix reuse, making Context Parallel (CP) the dominant Prefill strategy. The open-source SGLang CP implementation stored redundant KV Cache across layers; LayerSplit eliminates this by splitting KV Cache storage layer-wise. At 90% cache hit rate, throughput improves 10–132% across 40K–120K token contexts, with gains growing with context length.
- **Reproduction challenge:** Bugs only appeared at ~3–5 per 10,000 requests under simulated peak load (adjusted PD disaggregation ratio + high concurrency). Standard offline replay was insufficient; production-like pressure was required to trigger them.

## Why It Matters

A rare, rigorous production postmortem from a team running LLM inference at massive scale — directly relevant to anyone building high-concurrency agentic inference systems, and a concrete demonstration that Coding Agent workloads expose failure modes that don't surface in standard benchmarking environments.

---
[Source: Z.AI Blog](https://z.ai/blog/scaling-pain)
