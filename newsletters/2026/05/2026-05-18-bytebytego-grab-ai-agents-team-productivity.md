---
title: "How Grab Is Using AI Agents to Boost Team Productivity"
date: 2026-05-18
source_url: https://blog.bytebytego.com/p/how-grab-is-using-ai-agents-to-boost
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm, ai-infra]
tags: [Grab, multi-agent, LangGraph, LangChain, FastAPI, Redis, PostgreSQL, data-engineering, agent-architecture, production, enterprise, LLM-ops, tool-use]
saved_at: 2026-05-19
---

## Summary

Grab's Analytics Data Warehouse (ADW) team built a multi-agent AI system to reclaim hundreds of engineer-hours spent weekly answering routine data questions. Managing 15,000+ tables queried by ~1,000 people monthly, the team faced a pattern: questions varied, but the investigation playbook (search catalog → trace lineage → validate SQL → check logs) was always the same. They built a multi-agent system using LangGraph, FastAPI, and PostgreSQL, separating read-only investigation (four agents + supervisor) from write operations (one enhancement agent with human gates). After shipping to production, six things broke — and the team's solutions to those failures are the real engineering lesson.

## Key Highlights

- **Brain/hands separation**: LLM (reasoning) strictly separated from specialized agents/tools (fetching, querying, interacting with systems) — makes failures traceable
- **Five agents**: Classifier → Data Agent + Code Search Agent + On-call Agent → Summarizer; plus a separate Enhancement Agent for write operations
- **Tech stack**: FastAPI + LangGraph (stateful multi-agent) + Redis (caching/sessions) + PostgreSQL (conversation history) + Hubble/Genchi/Lighthouse (internal data platforms)
- **Production challenge #1 — context overflow**: tiktoken real-time token tracking, auto-summarization of early messages, tool output pruning before handoffs
- **Production challenge #2 — tool bloat**: 30+ tools with verbose descriptions degraded speed/quality; aggressive simplification to concise, actionable descriptions fixed it
- **Production challenge #3 — risky code execution**: 4-layer defense: input classification → SQL validation (PII/DROP/partition checks) → timeout protection → human review gates for all write operations
- **Feedback loop**: human annotations → test cases → pattern analysis → targeted prompt/guardrail improvements; system now autonomously handles majority of standard inquiries

## Why It Matters

Grab's case study shows that production multi-agent systems spend most engineering effort on hardening — context management, tool design, safety layers, trust-building — not on the agents themselves, and that investing in a deliberate feedback loop is what separates a demo from a durable system.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-grab-is-using-ai-agents-to-boost)
