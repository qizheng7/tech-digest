---
title: "How CockroachDB Built Vector Indexing at Scale"
date: 2026-05-25
source_url: https://blog.bytebytego.com/p/how-cockroachdb-built-vector-indexing
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [ai-infra]
tags: [CockroachDB, vector-search, C-SPANN, distributed-database, ANN, HNSW, IVF, K-means, RaBitQ, quantization, multi-tenancy, RAG, semantic-search]
saved_at: 2026-05-25
---

## Summary

CockroachDB's engineering team built C-SPANN, a purpose-built vector index for distributed SQL databases, after evaluating and rejecting HNSW, IVF, and other standard algorithms for failing key architectural requirements. The system treats the index as ordinary table data inside CockroachDB, inheriting its existing sharding, replication, range-splitting, and multi-region infrastructure for free. The article walks through C-SPANN's hierarchical K-means tree structure, its RaBitQ quantization scheme (94% size reduction), and its novel approach to multi-tenant isolation via prefix columns.

## Key Highlights

- Standard vector indexes (HNSW, IVF, pgvector) fail at least one of CockroachDB's six distributed requirements: no central coordinator, no large in-memory caches, minimal network hops, sharding-compatible layout, no hot spots, incremental real-time updates
- C-SPANN borrows from Microsoft's SPANN/SPFresh (tree partitioning + incremental updates) and Google's ScaNN (quantization), combined into a distributed SQL architecture
- Index lives on disk as ordinary key-value rows — nodes serve queries immediately after restart with no warm-up phase; automatically inherits all distributed machinery
- RaBitQ compression: 1,536-dimension OpenAI embeddings (3KB full) compressed to ~200 bytes (94% reduction) with a reranking step to recover accuracy
- Multi-tenancy via prefix columns: each user/tenant gets a separate K-means subtree; query performance scales with per-tenant data size, not total index size
- Supports REGIONAL BY ROW tables for geographic data domiciling (EU data stays in EU region)

## Why It Matters

C-SPANN demonstrates how vector search can be embedded natively in a distributed transactional database — avoiding the operational complexity of running a separate vector store — which is the right architectural pattern for multi-tenant enterprise RAG and agentic applications.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-cockroachdb-built-vector-indexing)
