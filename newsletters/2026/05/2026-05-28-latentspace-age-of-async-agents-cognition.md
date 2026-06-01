---
title: "The Age of Async Agents — Cognition's Walden Yan & OpenInspect's Cole Murray"
date: 2026-05-28
source_url: https://www.latent.space/p/cognition
source: Latent.Space
type: newsletter
newsletter: Latent.Space
topics: [newsletter, genai-llm, ai-startup, ai-infra]
tags: [Cognition, Devin, async-agents, agent-observability, OpenInspect, enterprise-coding-agents, agentic-workflows, harness]
saved_at: 2026-06-01
---

## Summary

Latent.Space podcast episode with Walden Yan (Cognition, makers of Devin) and Cole Murray (OpenInspect), recorded around the time of Cognition's $1B Series D at $26B valuation. The episode covers the evolution from synchronous to asynchronous agent architectures, why enterprise adoption of coding agents requires fundamentally different observability tooling, and how Cognition thinks about the harness-model interaction in long-horizon software engineering tasks. OpenInspect is building the observability layer for async agents — tracing, replay, and debugging tools for multi-turn agentic workflows that can run for hours or days.

## Key Highlights

- **Async agents** are the dominant production pattern for enterprise software engineering tasks — agents that run for hours/days without human-in-the-loop, with results reviewed after the fact
- **Harness quality** matters more than base model quality for enterprise coding tasks; Cognition's claimed 10x enterprise usage growth YTD is attributed partly to harness improvements, not just model upgrades
- **Cognition metrics at time of episode**: >$1B raised at $26B valuation, $492M ARR run-rate, enterprise usage up >10x YTD; customers include Exa and Modal
- **Observability gap**: debugging a 200-turn async agent run requires new tooling (replay, step-by-step inspection, diff views) that traditional software debugging tools don't provide — OpenInspect is building this
- **Trust and reliability** are the main enterprise adoption blockers: developers need to verify async agent outputs before merging, which requires agents to produce structured, inspectable artifacts (not just a PR)
- **Context management** is a persistent challenge: agent performance degrades past certain context lengths; strategies include periodic summarization checkpoints and session resets for long-horizon tasks

## Why It Matters

Cognition's trajectory — from $10B Series C (Sep 2025) to $26B Series D (May 2026) in 8 months — is the clearest data point that async coding agents are crossing the chasm from developer curiosity to enterprise budget line, and that observability/trust tooling is the next required layer.

---
[Source: Latent.Space](https://www.latent.space/p/cognition)
