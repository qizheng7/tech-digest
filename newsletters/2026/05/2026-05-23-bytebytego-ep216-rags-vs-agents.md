---
title: "EP216: RAGs vs Agents"
date: 2026-05-23
source_url: https://blog.bytebytego.com/p/ep216-rags-vs-agents
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, ai-infra, genai-llm]
tags: [RAG, agents, Claude-Code, context-management, proxy, API-gateway, agentic-loop, tool-use]
saved_at: 2026-05-23
---

## Summary

ByteByteGo's EP216 covers two foundational AI architecture patterns (RAGs vs Agents), Claude Code internals — including how requests travel through the agent loop and how context is managed across long sessions — plus a primer on forward/reverse proxies and API gateways for completeness.

## Key Highlights

- **RAG vs Agents rule of thumb**: Use RAG when the answer lives in your documents (one retrieval → one generation, cheap and debuggable); use agents when the answer requires action on other systems (reasoning loop + tools, more flexible but harder to debug across steps)
- **Claude Code request path** (8 steps): prompt → interface wraps with repo context → agent loop plans → permission system checks → tool call dispatched → execution in shell/sandbox → tool result returned → streamed to user; the loop repeats until the model stops requesting tools
- **Claude Code context management** (5 strategies in escalation order): Budget Reduction (caps tool result size) → Snip (trims oldest history) → Microcompact (prunes by tool_use_id to keep prompt cache warm) → Context Collapse (read-time projection) → Auto-compact (full model summary as last resort)
- The pattern is "lazy degradation" — apply the least disruptive shaper first; escalate only when cheaper layers are insufficient
- Forward proxy represents the client (corporate filtering, caching); reverse proxy represents the server (load balancing, TLS termination); API gateway is a reverse proxy that adds auth, rate limits, versioning, and request shaping across microservices

## Why It Matters

ByteByteGo's clear RAG vs Agents framework and the Claude Code internals breakdown (both request flow and context management) give builders a concrete mental model for choosing architectures and debugging the most common failure modes in production agentic systems.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/ep216-rags-vs-agents)
