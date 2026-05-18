---
title: "How I AI: Quests, Token Leaderboards, and the Elite AI Adoption Playbook"
date: 2026-05-11
source_url: https://www.lennysnewsletter.com/p/how-i-ai-quests-token-leaderboards
source: Lenny's Newsletter
type: newsletter
newsletter: Lenny's Newsletter
topics: [newsletter, genai-llm, ai-startup]
tags: [AI-adoption, enterprise, Sendbird, Notion, spec-driven-development, coding-agent, Codex, Claude-Code, workflow, token-tracking, gamification]
saved_at: 2026-05-17
---

## Summary

Two "How I AI" episodes in this issue: John Kim (Sendbird CEO) shares an enterprise AI adoption playbook built around a gamified internal marketplace ("Quests"), token-usage tiers from Beginner to "AI God," and non-technical teams shipping to production. Ryan Nystrom (Notion engineer) covers spec-driven development as an AI engineering workflow — using Markdown spec files as the source of truth, background agents that open PRs from a Notion comment, and fast CI as the mathematical limit on agent velocity.

## Key Highlights

**John Kim (Sendbird) — AI adoption playbook:**
- "Automators" internal marketplace: anyone posts a "quest" (automation request), engineers/agents build it, earn XP exchangeable for rewards; shows risk level, weeks saved, and beneficiaries
- Five token-usage tiers: Beginner (<1M/day) → Intermediate → Expert → Architect → Catalyst → AI God (>100M/day); managers see all team members' tier and tailor enablement
- Non-technical teams (marketing) shipped a full e-commerce swag store with Stripe integration, custom designs, and a Konami Code Easter egg — without engineering time
- Secure templates pre-configured with auth, databases, and InfoSec approval let non-engineers ship to production without fear
- Token usage smoothness as a metric: flat/smooth curves = AI working 24/7; dips = weekends/vacation where AI sits idle

**Ryan Nystrom (Notion) — spec-driven development:**
- Spec files: Markdown documents in the repo describing features in plain English with code pointers and verification steps; when feature changes, update the spec and point Codex at it — agent implements, runs verification, ships
- "Yap your spec": open Whisper, describe how a feature should work, give transcript to Codex with examples → gets back a comprehensive technical spec faster than writing
- Boxy system: @mention Codex from a Notion task → 20 minutes later get a PR with implementation, UI screenshots, and preview URL — no IDE, no local environment, no context switch
- Fast CI as the mathematical limit: if CI takes 1 hour, agents sit idle 1 hour between iterations; Notion is aggressively cutting CI to 25% of current time specifically to unlock agent productivity
- "Make AI defend its decisions": instead of "are you sure?", say "you're wrong; defend your argument with evidence" — forces cited reasoning

## Why It Matters

Both episodes converge on the same signal: the bottleneck in AI-powered engineering is no longer model capability but organizational infrastructure — gamified adoption systems, spec-driven workflows, fast CI, and secure non-engineer templates are what separates high-token-velocity orgs from the rest.

---
[Source: Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-i-ai-quests-token-leaderboards)
