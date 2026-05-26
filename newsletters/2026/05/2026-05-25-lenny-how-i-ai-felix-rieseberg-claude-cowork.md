---
title: "How I AI: Felix Rieseberg (Claude Cowork) on Building with Claude + Google I/O 2026 Recap"
date: 2026-05-25
source_url: https://www.lennysnewsletter.com/p/how-i-ai-how-the-engineer-behind
source: Lenny's Newsletter
type: newsletter
newsletter: Lenny's "How I AI"
topics: [newsletter, genai-llm, ai-infra]
tags: [Claude-Code, Claude-Cowork, Anthropic, Felix-Rieseberg, AI-workflow, live-artifacts, Opus-vs-Sonnet, Google-IO, Gemini-3.5-Flash, Antigravity-2, agentic, UX]
saved_at: 2026-05-25
---

## Summary

This issue bundles two podcast episodes: (1) Felix Rieseberg, engineering lead for Claude Cowork and Claude Code Desktop at Anthropic, walks through his personal Claude workflows — from building a 3D floor planner using email receipt data to creating a live personal dashboard and a $20 hardware AI "buddy." (2) Claire from ChatPRD tests Google I/O 2026's major launches live, covering Gemini 3.5 Flash, Antigravity 2.0, Omni video, Flow editor, Stitch, and Pomelli, and concludes that half the announced features weren't actually available during testing.

## Key Highlights

**Felix Rieseberg (Episode 1):**
- Core mental model: "go one abstraction layer up, then do it again" — whenever you're doing tedious work, ask how Claude could do it, then how Claude could figure out what to do without you telling it
- Email as personal database: Felix parsed years of furniture receipts from Gmail to build a 3D floor planner with his actual furniture dimensions
- Live artifacts refresh automatically with connected services (Gmail, Calendar, Notion); better than static Claude outputs for personal dashboards
- Model selection heuristic: use Sonnet for well-scoped tasks; reach for Opus when Claude needs to interpret *what you actually want*, not just what you said
- Debugging philosophy: when Claude makes mistakes, ask "here's what I expected — where did things go differently? How can we prevent this?" — frame as workflow debugging, not model failure
- Kids are better AI users because they haven't internalized 20 years of "computers can't do that" assumptions

**Google I/O 2026 Recap (Episode 2):**
- Gemini 3.5 Flash rivals frontier coding models in Google's benchmarks at 4x the speed — if benchmarks hold, could shift coding agent landscape
- Antigravity 2.0 adds projects, Cron-scheduled tasks, and subagents, reaching feature parity with Claude Code/Codex — but months behind
- Omni: 10-second videos with character consistency and conversational editing; tested successfully on animating a child's drawing
- Google AI Studio claims Workspace integration (Sheets, Gmail, Drive, Calendar) but Claire couldn't get it to work in testing
- Pattern across I/O: features announced that aren't actually available yet — eroding developer trust in Google's roadmap

## Why It Matters

Rieseberg's episode is a rare practitioner-level breakdown of how Anthropic's own engineers use Claude daily; the Google I/O recap surfaces a persistent tension between Google's launch scale and its execution reliability.

---
[Source: Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-i-ai-how-the-engineer-behind)
