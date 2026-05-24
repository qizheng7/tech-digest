---
title: "MCP 2026-07-28 Release Candidate: Stateless Protocol, MCP Apps, and Tasks Extension"
date: 2026-05-21
source_url: https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/
source: Model Context Protocol
type: article
topics: [ai-infra, genai-llm]
tags: [MCP, protocol, stateless, MCP-Apps, Tasks, OAuth, deprecation, agent-infrastructure, developer-tools, Anthropic, SDK]
saved_at: 2026-05-23
---

## Summary

Anthropic published the release candidate for MCP specification version 2026-07-28 — the largest protocol revision since launch. The headline change is that MCP is now stateless at the protocol layer: the `initialize` handshake, session IDs, and `Mcp-Session-Id` header are all removed, enabling any request to land on any server instance behind a plain round-robin load balancer. The final specification ships July 28, 2026, giving SDK maintainers a ten-week validation window.

## Key Highlights

- **Stateless core**: eliminates the `initialize` handshake and `Mcp-Session-Id` header; removes sticky routing, shared session stores, and deep packet inspection requirements for horizontal deployments
- **MCP Apps extension**: servers can now render interactive HTML UIs directly, making server-rendered interfaces a first-class MCP primitive
- **Tasks extension**: restructured for stateless operation; enables long-running work as a first-class concept in the protocol
- **Authorization hardening**: six OAuth 2.0 / OpenID Connect alignment proposals including issuer validation and clearer credential binding
- **Formal deprecation policy**: Roots, Sampling, and Logging deprecated with minimum 12-month removal window; prevents the ecosystem churn that hurt early protocol adopters
- New caching headers (`ttlMs`, `cacheScope`) and trace context standardization improve observability at scale
- Tier 1 SDKs expected to ship support within the ten-week RC window before the July 28 final spec

## Why It Matters

Stateless MCP removes the biggest operational barrier to running MCP servers at scale — sticky sessions and shared state — making it significantly easier to deploy agent-connected tools behind standard load balancers, which unblocks broader enterprise and cloud adoption of the protocol.

---
[Source: Model Context Protocol](https://blog.modelcontextprotocol.io/posts/2026-07-28-release-candidate/)
