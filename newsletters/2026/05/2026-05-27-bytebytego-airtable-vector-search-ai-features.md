---
title: "How Airtable Built the Search Layer Behind Their AI Features"
date: 2026-05-27
source_url: https://blog.bytebytego.com/p/how-airtable-built-the-search-layer
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, ai-infra, genai-llm]
tags: [Airtable, vector-search, Milvus, HNSW, RAG, semantic-search, multi-tenancy, hot-cold-data, embedding, distributed-systems]
saved_at: 2026-06-01
---

## Summary

Airtable built semantic search for their AI features (Omni NL-to-data and linked record recommendations) on top of Milvus with HNSW indexing, using a one-partition-per-base isolation model. The key insight that drove all architectural decisions: 75% of bases are idle in any given week, so they implemented hot/cold partition offloading — keeping only active bases in memory and reloading cold ones in seconds. The system hits sub-500ms p99 latency with high recall while managing millions of customer bases across hundreds of thousands of embeddings.

## Key Highlights

- **Partitioning**: one Milvus partition per customer base for strong physical isolation and simple deletion; hit a wall at ~100,000 partitions per collection (250ms creation latency, 30s+ load time); fixed with hierarchical capping: 400 collections × 1,000 partitions per cluster = 400,000 bases max per cluster; add clusters as needed
- **Index selection**: chose HNSW (99–100% recall, fully in-memory) over DiskANN (disk-based, higher latency) and IVF-SQ8 (compressed, lower recall); 500ms p99 latency requirement and high-recall needs ruled out alternatives
- **Hot/cold data**: only 25% of bases active per week; cold partitions offloaded to storage, reload in seconds on access — makes HNSW economically viable (otherwise memory bill would be prohibitive)
- **Permission model**: Milvus handles similarity search only; authorization happens at the application layer when fetching actual rows from Airtable's primary database
- **Disaster recovery**: re-embed from source rather than backup/restore; most-used bases re-embedded first, rest rebuilt lazily; works because async embedding pipeline already existed for normal writes
- **Embeddings are ~10× the size of source data** — requires a separate vector store, not storage alongside the source

## Why It Matters

Airtable's design shows that for multi-tenant AI features, understanding actual access patterns (bursty, bimodal, mostly-idle) is more important than picking the "best" vector database — the entire architecture is only economical because they measured first.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-airtable-built-the-search-layer)
