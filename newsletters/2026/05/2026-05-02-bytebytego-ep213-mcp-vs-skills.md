---
title: "EP213: MCP vs Skills, Clearly Explained"
date: 2026-05-02
source_url: https://blog.bytebytego.com/p/ep213-mcp-vs-skills-clearly-explained
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm]
tags: [MCP, agent-skills, agents, prompt-injection, architecture, JSON-RPC, LLM-security]
saved_at: 2026-05-02
---

## Summary

ByteByteGo EP213 covers two core AI agent architecture topics: (1) MCP vs Agent Skills — five dimensions that determine which pattern to use for extending agent capabilities; and (2) five layered defenses against prompt injection attacks.

## Key Highlights

**MCP vs Skills (5 dimensions):**
- Integration: MCP is a client-server protocol connecting N agents to M backends through one interface; Skills are directories with a SKILL.md the agent loads on trigger
- Architecture: MCP runs as a separate process (JSON-RPC); a Skill is just a directory with SKILL.md, optional scripts, references, and assets
- Invocation: MCP tools called with typed, schema-validated parameters (chainable); Skills invoked by agent reading SKILL.md and running described commands (bash, python, curl)
- Runtime: MCP servers run in their own container/service; Skills run in the agent's own environment with no extra infra
- Rule of thumb: use MCP to connect agents to live systems/data; use Skills to give agents reusable know-how and instructions

**5 Defenses Against Prompt Injection:**
- Spotlighting: wrap untrusted text in `<UNTRUSTED>...</UNTRUSTED>` tags, telling model to treat as data not instructions
- Instruction Hierarchy: fine-tune model to rank developer system prompt > user message > third-party content
- Least-Privilege Tools: give the agent only the minimum tools it needs
- Human-in-the-Loop: require explicit user approval before sensitive actions
- Planner/Executor Split: two separate LLMs — planner has tool access but never sees untrusted content; executor reads untrusted content but has no tools

## Why It Matters

As agent systems proliferate, the MCP-vs-Skills distinction defines where integration complexity lives (server vs. local), and layered prompt injection defenses are now a production requirement rather than an academic exercise.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/ep213-mcp-vs-skills-clearly-explained)
