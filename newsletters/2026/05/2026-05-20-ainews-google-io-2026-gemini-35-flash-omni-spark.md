---
title: "[AINews] Google I/O 2026: Gemini 3.5 Flash, Omni (NanoBanana for Video), Spark (background agents), and Antigravity"
date: 2026-05-20
source_url: https://www.latent.space/p/ainews-google-io-2026-gemini-35-flash
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra]
tags: [roundup, twitter-recap, Google, Gemini, Gemini-3.5-Flash, Gemini-Omni, Antigravity, Spark, background-agents, Google-IO, Karpathy, Anthropic, Arena, multimodal, video-generation, agentic]
saved_at: 2026-05-20
---

## Top Stories

- **Gemini 3.5 Flash launched GA**: Google's strongest agentic/coding model, with 1M token context, 65k max output, 4 thinking levels, and "thought preservation" across turns. Priced at $1.50/$9.00 per 1M tokens; 4x faster than comparable frontier models (up to 12x in Antigravity). Hits #9 in Text Arena and #9 Code Arena: Frontend.
- **Gemini Omni (video generation)**: New model family merging Gemini reasoning with generative media via Omni Flash — takes text/image/video/audio as input, produces video creation/editing. Available to paid Gemini users in Flow now, YouTube Shorts rolling out free.
- **Antigravity 2.0 agent stack**: Google's answer to Codex/Claude Code — desktop app, CLI, SDK, and Managed Agents in the Gemini API (hosted Linux sandbox, files, browsing, GCS mounts). Demo: an OS built in 12 hours using 93 parallel sub-agents, 2.6B tokens, under $1K in API credits.
- **Gemini Spark — background agents**: Long-running personal AI agents on Google Cloud VMs that continue working when user devices are closed; check in before major actions.
- **Google Search transformation**: AI-powered generative UI/simulations on the fly (Antigravity + Gemini 3.5 Flash); persistent "information agents" for background monitoring of web/news/social signals, rolling out to Pro/Ultra users.
- **Andrej Karpathy joins Anthropic**: The day's most-engaged AI tweet — Karpathy announced joining Anthropic "to get back to R&D," reportedly to work on RSI/autoresearch and a new pretraining-focused effort.

## Community Signals (AI Twitter Recap)

AI Twitter Recap

Google used I/O to reposition Gemini as both a consumer AI surface and a developer/agent platform, with three core technical announcements: Gemini 3.5 Flash for fast agentic/coding workloads, Gemini Omni for multimodal generation/editing starting with video, and a broader Antigravity agent stack spanning desktop/CLI/SDK/API. Official posts emphasized scale — Google says it now processes over 3.2 quadrillion tokens/month, up 7x YoY from 480T/month, while the Gemini app has 900M+ monthly users and is available in 230+ countries and 70+ languages (Google, Google, GeminiApp). The most technically substantive release was Gemini 3.5 Flash, framed by Google as its strongest agentic/coding model yet, GA immediately, with 1M-token context, 65k max output, 4 thinking levels ("minimal/low/medium/high"), and "thought preservation" across turns (GoogleDeepMind, Google, _philschmid). Google paired that with Gemini Omni, a new family combining Gemini reasoning with generative media, initially via Omni Flash, capable of taking text/image/video/audio inputs and producing video edits/generation in Gemini, Flow, Shorts, and later APIs (GoogleDeepMind, Google, GeminiApp). Around those models, Google launched or expanded Antigravity 2.0 desktop, CLI, SDK, Managed Agents in the Gemini API, Search-native generative UI/coding, Gemini Spark background agents on cloud VMs, and a long list of Gemini-app/Workspace/commerce/media integrations (Google, Google, Google).

Facts vs. opinions

Facts / directly claimed by official or third-party benchmark sources

- Google says it now processes 3.2 quadrillion tokens/month, up from 480 trillion a year earlier (Google).
- Google says Gemini has 900M+ monthly users (Google).
- Google says Gemini 3.5 Flash is GA today across Gemini app, Search AI Mode, Gemini API, AI Studio, Antigravity, Android Studio, and enterprise surfaces (Google, GeminiApp).
- Google says Gemini 3.5 Flash has 1M context, 65k max output, 4 thinking levels, and "thought preservation" across turns (_philschmid).
- Google says 3.5 Flash beats Gemini 3.1 Pro on Terminal-Bench 2.1, GDPval-AA, and MCP Atlas (GoogleDeepMind, Google).
- Google says 3.5 Flash runs 4x faster than comparable frontier models, and up to 12x faster in Antigravity (Google, JeffDean).
- Independent benchmarker Artificial Analysis reports Gemini 3.5 Flash scores 55 on its Intelligence Index, +9 vs Gemini 3 Flash, at >280 output tok/s, with MMMU-Pro 84%, GDPval-AA Elo 1656, and pricing of $1.50 / $9.00 per 1M input/output tokens; it also reports the model is 5.5x costlier to run than Gemini 3 Flash on its suite and 75% costlier than Gemini 3.1 Pro (ArtificialAnlys).
- Arena reports Gemini 3.5 Flash reached #9 overall in Text Arena and #9 in Code Arena: Frontend, scoring 1507, a +70 jump over Gemini 3 Flash, and becoming the top score in its price tier (arena).
- Google says Gemini Omni Flash is available in Gemini/Flow today for paid users, in Shorts/Create starting this week for free, and via APIs in coming weeks (Google).
- Google says Spark runs on dedicated Google Cloud virtual machines, allowing long-running tasks while user devices are closed (Google).
- Google claims an Antigravity + Gemini 3.5 Flash demo built a functioning OS in 12 hours using 93 parallel sub-agents, 15k+ model requests, 2.6B tokens, and < $1K API credits (Google).
- Google says Search will use Antigravity + 3.5 Flash to generate custom visual tools/simulations on the fly (Google).

Opinions / interpretations / skepticism

- Positive takes: "Google is back," "insane evals for a Flash model," "world model towards AGI," "mind blowing" for Search + Antigravity, etc. (kimmonismus, Kseniase_, demishassabis).
- Neutral caution: some posters explicitly avoided overhyping due to self-reported benchmarks and noted pricing/perf concerns (scaling01, simonw).
- Negative/skeptical takes focused on:
  - Price inflation relative to earlier Flash models (enricoros).
  - Comparisons where GPT-5.5-medium may be smarter/cheaper/faster end-to-end (scaling01, scaling01).
  - Benchmark caveats such as weak TerminalBench-Hard, mediocre MRCR / ARC-AGI-2, or not clearly beating Kimi/GLM on some slices (scaling01, teortaxesTex, scaling01).
  - Product naming/UX confusion around Gemini CLI vs Antigravity CLI and broader interface design criticism (zachtratar, kchonyc, teortaxesTex).

## Why It Matters

Google I/O 2026 marks Google's most assertive push into the agent layer yet — Antigravity, Spark, and the Gemini 3.5 Flash launch together signal that Google is repositioning from search infrastructure company to agentic computing platform, directly competing with OpenAI Codex and Anthropic Claude Code.

---
[Source: AINews](https://www.latent.space/p/ainews-google-io-2026-gemini-35-flash)
