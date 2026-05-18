---
title: "How Pinterest Built a Production MCP Ecosystem"
date: 2026-05-11
source_url: https://blog.bytebytego.com/p/how-pinterest-built-a-production
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [ai-infra, genai-llm]
tags: [MCP, Pinterest, enterprise, auth, registry, deployment, agent-infra, security, two-layer-auth, SPIFFE, Envoy]
saved_at: 2026-05-17
---

## Summary

Pinterest built a production MCP ecosystem that connects 5 AI surfaces (internal chat, IDE plugins, chatbots, CLI agents, autonomous agents) to 10+ internal tools (Presto, Spark, Airflow, documentation, ticketing) using Model Context Protocol as the backbone. Beyond the protocol itself, Pinterest engineered a central registry, a two-layer auth system (Envoy coarse-grained + tool-level decorator), and a unified deployment pipeline. As of Jan 2025: 66,000 invocations/month across 844 MAU, saving ~7,000 hours/month.

## Key Highlights

- **N×M → N+M**: Without MCP, 5 surfaces × 10 tools = 50 custom integrations; MCP reduces this to 15 (5 clients + 10 servers) — gap widens with scale
- **Three architectural bets**: Cloud-hosted servers (not local), many small domain-specific servers (not monolithic), and a unified deployment pipeline that turned multi-day setup into hours of business-logic work
- **MCP Registry**: Central catalog serving as governance backbone; web UI for humans (status, ownership, support channels) + API for programmatic server discovery and authorization checks; only registered servers are approved for production
- **Two-layer auth**: Layer 1 = Envoy proxy validates JWT (OAuth session), checks group memberships, enforces coarse-grained network-edge policies (e.g., "production AI chat may talk to Presto, not dev-namespace servers"); Layer 2 = `@authorize_tool(policy='...')` decorator inside each server enforces business-group gating per tool (e.g., only Ads/Finance groups can call `get_revenue_metrics`)
- **SPIFFE for service-to-service**: Automated calls with no human in the loop use cryptographic certificates from the service mesh instead of JWTs; reserved for low-risk read-only scenarios
- **Human-in-the-loop governance**: Agents propose sensitive/expensive actions; humans approve (optionally in batches) before execution; elicitation required for dangerous operations like overwriting data
- **Observability baked in**: Shared library functions in the server framework provide logging, invocation counts, and exception tracing by default; north-star metric = "minutes saved per invocation" × invocation count
- **Heaviest servers**: Presto (universal data access), Spark (job debugging + log summarization + root-cause recording), Knowledge (institutional Q&A)

## Why It Matters

Pinterest's MCP deployment is one of the most detailed public blueprints for enterprise AI agent infrastructure — the real engineering work was everything the protocol doesn't specify: registry, layered auth, deployment pipeline, and observability, which together turned a promising protocol into 7,000 hours/month of verified productivity savings.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-pinterest-built-a-production)
