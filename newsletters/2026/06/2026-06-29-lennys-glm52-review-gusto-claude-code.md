---
title: "How I AI: GLM-5.2 review & How Gusto built a new product line with Claude Code"
date: 2026-06-29
source_url: https://www.lennysnewsletter.com/p/how-i-ai-glm-52-review-and-how-gusto
source: Lenny's Newsletter
type: newsletter
newsletter: Lenny's Newsletter
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [GLM-5.2, open-weights, Claude-Code, Cursor, agentic-engineering, Z.ai, Gusto, no-process, cost-optimization, production-workflow]
saved_at: 2026-06-30
---

## Summary

Two episodes this week: Claire (ChatPRD) does a live review of GLM-5.2 inside her production codebase (including a 45-minute autonomous bug-hunting session), and Eddie Kim (Gusto CTO) shares how a 5-person team shipped a new product line in 10 weeks using Claude Code with no PM, no Figma, no Jira, and no standups. Both converge on the same theme: AI has crossed a threshold where workflow design matters more than model selection.

## Key Highlights

- GLM-5.2 setup in Cursor: route via OpenRouter, set base URL to `openrouter.ai/api/v1/cursor` (undocumented suffix), add `z-ai/glm-5.2` as custom model; Claude Code requires two env var changes + `claude/settings.json` edit — total ~30 minutes
- 45-minute autonomous GLM-5.2 bug-triage session: pulled 72hr Sentry errors + Vercel logs, produced dark-mode engineering canvas with 20 Sentry errors, 5 Vercel signals, 14 planned fixes including 2 P0s not found through normal monitoring
- Cost: **$3.36 for 6M tokens** (72% cache rate); open-weight inference through OpenRouter offers structurally different cost curve vs Opus/GPT-5.5 for long-context agentic sessions
- GLM-5.2 ceiling: strong on HTML/CSS and long-running tasks; shakier on React under multi-step agentic pressure — the friction point to test before committing to critical paths
- Gusto: 5-person team, zero pre-existing code → tier-one production launch in 10 weeks with Claude Code; no standups, no ticket system, no async threads — shared context held inside the AI loop replaced coordination overhead
- Eddie Kim's stack: Cloudflare Workers + Vercel AI SDK, nothing else; "an agent is an AI SDK running somewhere in the cloud, able to look up files and call tools — that's the full definition"
- Key design insight: build coordination model *around* AI as primary contributor from day one, not grafted onto a human-scaled workflow; the result gets faster as the AI improves

## Why It Matters

GLM-5.2 and Claude Code together demonstrate that the frontier model access bottleneck is increasingly separable from production capability — and that process design around AI, not the model choice itself, is the new primary differentiator.

---
[Source: Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-i-ai-glm-52-review-and-how-gusto)
