---
title: "How I AI: How to write AI agent loops in Claude Code and Codex + How Claude Mythos found a 15-year-old bug in Mozilla Firefox"
date: 2026-06-22
source_url: https://www.lennysnewsletter.com/p/how-i-ai-how-to-write-ai-agent-loops
source: Lenny's Newsletter
type: newsletter
newsletter: Lenny's Newsletter
topics: [newsletter, genai-llm, ai-infra]
tags: [agent-loops, Claude-Code, Codex, Mozilla, Firefox, security, memory-safety, harness, goal-loops, verification]
saved_at: 2026-06-25
---

## Summary

This "How I AI" episode covers two practical segments: Claire (chatprd.ai) gives a tutorial on AI agent loops using Claude Code and Codex, covering heartbeat/cron/goal-based loop patterns; and Brian Grinstead (distinguished engineer at Mozilla) explains how his team used Claude Mythos agents to ship 423 Firefox security fixes in one month by building a custom harness around the Claude agent SDK.

## Key Highlights

- **Agent loops 101 (Segment 1):** "A loop is just a prompt that fires itself." Goal loops run until an outcome is validated, not until a timer fires. Fuzzy success criteria cause infinite loops — fix by letting Codex write its own goals via OpenAI's goal-writing guide
- **Spawning subagents in loops:** The ceiling is loops that spawn subagent loops — Claire's Codex demo had a weekly skills-identification loop spawn two named subagents that each ran their own goal loops to validate skills in real time
- **Mozilla's approach (Segment 2):** Custom harness around Claude Mythos (agent SDK) that scores files on likelihood of memory safety issues + ease of webpage access, then runs goal loops with verifier subagents. Brian calls it "a reasonably simple wrapper"
- **423 Firefox security fixes in one month** — agents try 14–20 different approaches to trigger a bug without losing focus: "Cognitive energy declines over time in a way that agents don't"
- **Two-stage verification** (agent triggers crash in fuzzing build, verifier checks bug report) eliminates nearly all false positives before a human sees the result
- **Human role shifts** to pattern recognition across the codebase — agents fix specific vulnerable locations but miss adjacent similar spots, requiring human sweeps for related patterns
- **Tooling recommendation:** Use vendor-provided harnesses (Claude agent SDK, OpenAI agent SDK) over third-party frameworks; run multiple models/harnesses since different models find different vulnerability classes

## Why It Matters

Mozilla's use of Claude Mythos to ship hundreds of real security fixes demonstrates that agentic verification loops at scale are production-ready today — the constraint is harness design, not model capability.

---
[Source: Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-i-ai-how-to-write-ai-agent-loops)
