---
title: "How Amazon Uses LLMs to Recommend Products"
date: 2026-04-27
source_url: https://blog.bytebytego.com/p/how-amazon-uses-llms-to-recommend
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm]
tags: [LLM, recommendation, knowledge-graph, RAG, Amazon, commonsense-AI, systems]
saved_at: 2026-04-28
---

## Summary

ByteByteGo profiles COSMO, Amazon's commonsense knowledge graph built using OPT-175B to bridge the semantic gap between shopper intent and product catalog. Starting from 30,000 human annotations, COSMO scales to 6.3M nodes and 29M edges across 18 product categories. A distilled COSMO-LM (LLaMA 7B/13B) serves fresh commonsense knowledge in production at a fraction of the original cost. A/B tests on 10% of US traffic showed a 0.7% relative sales lift, projected to reach billions at full scale.

## Key Highlights

- COSMO knowledge graph: 6.3M nodes, 29M edges, 18 product categories — from 30,000 human annotations
- OPT-175B (not GPT-4) for data privacy; only 35% of search-buy explanations and 9% of co-purchase explanations met quality bar
- 15 relationship types mined from LLM output (e.g., used_for_function, used_for_audience, xWant)
- COSMO-LM: LLaMA 7B/13B fine-tuned for generation + plausibility/typicality prediction in one model
- Production: 2-tier caching (pre-loaded for yearly-frequent searches; batch for daily queries)
- A/B test (10% US traffic): +0.7% relative product sales; +8% navigation engagement
- Projected revenue impact of billions if deployed across full US traffic for navigation alone

## Why It Matters

COSMO demonstrates how targeted LLM distillation can convert 30K human labels into 29M production-quality knowledge edges — a leverage ratio that shows the real power of LLM-assisted knowledge graph construction for any domain requiring commonsense reasoning.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-amazon-uses-llms-to-recommend)
