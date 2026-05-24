---
title: "[AINews] All Model Labs are now Agent Labs"
date: 2026-05-23
source_url: https://www.latent.space/p/ainews-all-model-labs-are-now-agent
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [roundup, twitter-recap, agent-labs, harness, Codex, DeepSeek, MCP, stateless, RL, VPO, multimodal, Runway, cybersecurity, Glasswing, immigration, Gemini]
saved_at: 2026-05-23
---

## Top Stories

- Greg Brockman (OpenAI) declares "the model alone is no longer the product" — AI21 shuts model team to pivot to agents; DeepSeek starts building a harness team for the first time
- DeepSeek V4-Pro makes 75% discount permanent: $0.435/M input, $0.87/M output — ~12x cheaper than GPT-5.5, ~19x cheaper than Claude Opus 4.7 per Artificial Analysis
- MCP 2026-07-28 RC announced: fully stateless protocol (no handshake, no session ID), MCP Apps extension (server-rendered UI), Tasks extension, OAuth hardening
- CoreWeave Sandboxes launches in public preview for RL, agent tool use, and model eval; NVIDIA open-sources AI-Q agent skills for deep-research pipelines
- Project Glasswing: Anthropic + 50 partners found 10,000+ high/critical vulnerabilities in essential software in one month using Claude Mythos Preview
- Vector Policy Optimization (VPO): new RL approach that optimizes vector-valued rewards instead of scalar to prevent reward collapse during test-time scaling
- Cartesia Sonic-3.5 ranked #1 TTS model on Speech Arena (Elo 1218, 42 languages, 82ms end-to-end first audio); Runway Aleph 2.0 ships 30s multishot video editing at 1080p

## Community Signals (AI Twitter Recap)

Agent Products, Harnesses, and the Shift Beyond "Just the Model"
The product surface is moving up-stack: A recurring theme was that model quality alone is no longer the moat; the winning product is increasingly model + harness + workflow + UI + memory + economics. @gdb put it bluntly: "the model alone is no longer the product," while @dzhng argued top-tier products need model <> harness <> product symbiosis. The same pattern shows up in practice: @signulll framed ambient AI and agentic AI as the new seam of computing interfaces, and @teortaxesTex noted that harness research still risks converging on "replicate Claude Code" instead of exploring broader interfaces.

Coding-agent product differentiation is becoming concrete: OpenAI shipped another substantial Codex update via "codex thursday no. 6" with appshots, /goal improvements, remote computer use while locked, annotation mode, plugin sharing, and analytics. @gdb separately highlighted Appshots, while users reported meaningful workflow shifts: @gdb said it's hard to remember coding before Codex, and @reach_vb said they haven't opened an IDE in over a month. But product rough edges remain: @theo praised T3 Code's remote feature as ahead of alternatives, then contrasted it with buggy remote workflows in Codex. On the Claude side, @ClaudeDevs expanded auto mode to the Pro plan and added Sonnet 4.6 support.

Model Performance, Cost Curves, and Frontier Competition
DeepSeek's pricing move was the biggest market signal: @deepseek_ai made the 75% DeepSeek-V4-Pro discount permanent, triggering strong reactions because it materially changes the cost/performance frontier. @ArtificialAnlys quantified first-party pricing at $0.435/M input, $0.87/M output, $0.0036/M cached input, estimating a blended ~$0.18/M and placing V4 Pro on the Pareto frontier for intelligence vs run cost. They estimate running their Intelligence Index on V4 Pro costs ~3x less than Gemini 3.1 Pro Preview, ~12x less than GPT-5.5, and ~19x less than Claude Opus 4.7. Community reaction centered on DeepSeek's push toward "intelligence too cheap to meter."

Gemini Flash improved, but usage feedback was mixed: @OfficialLoganK reported Gemini 3.5 Flash making major progress over 3.1 Pro on GDPval, claiming Flash is now "competing at the frontier." But several builders pushed back: @Alezander907 saw only slight browser-agent improvement at higher cost, @giffmana argued this isn't "Flash progress" if the brand still implies cheapness, and @jeremyphoward said the model feels optimized to max evals rather than cooperate with humans.

Qwen and Chinese frontier models keep compressing the race: Qwen3.7-Max portrayed as a meaningful step up, especially in instruction following, context reliability, and stability, while still suffering from verbosity and high token usage. @scaling01 claimed recent ALE-Bench runs show Chinese models like Kimi-K2.6, DeepSeek-V4, GLM-5.1 outperforming several Western releases.

Protocols, Infra, and Agent Runtime Tooling
MCP's new release candidate is a substantive protocol simplification: @dsp_ announced the MCP 2026-07-28 release candidate, with the key change that the protocol is now stateless: no handshake, no session ID, and any request can hit any server instance. The RC also introduces first-class extensions like MCP Apps and Tasks, plus auth hardening and a clearer deprecation policy.

Sandboxes and managed execution are becoming first-class primitives: @_philschmid demoed Gemini Managed Agents + Interactions API to give an agent a secure hosted Linux sandbox with memory and code execution. @CoreWeave launched CoreWeave Sandboxes in public preview for RL, agent tool use, and model eval, while @cnakazawa released Cloudsail for per-task Cloudflare sandboxes with shell, Codex, and GitHub access without exposing tokens. @skypilot_org argued RL doesn't work on Slurm because modern RL is a multi-service system with heterogeneous hardware and recovery needs.

Open-source harnesses and memory layers are proliferating: @NVIDIAAI open-sourced AI-Q agent skills for portable deep-research pipelines that can plug into arbitrary harnesses.

Research: RL, Distillation, Architectures, and Evaluation
RL post-training and reward design are under active reconsideration: @RyanBoldi introduced Vector Policy Optimization (VPO), arguing scalar reward collapse during RL can sabotage test-time scaling. VPO instead optimizes vector-valued rewards, improving search performance even on the original scalar objective.

Agent compilation/distillation is emerging as a serious economic idea: @dair_ai highlighted a paper showing a full agentic workflow — multi-step calls, tool use, scratchpads, decision structure — can be distilled into weights and run at ~100x lower inference cost while preserving near-frontier quality.

Architecture work remains lively beyond vanilla transformers: @ChunyuanDeng introduced LT2, a linear-time looped transformer combining sparse and linear attention. On MoE, @Jianlin_S proposed Moving Quantile Balancing for sequence-level load balancing without a loss penalty. @allen_ai launched ArtifactLinker, which predicts which benchmarks a model is likely to set SOTA on before running them.

Math and reasoning capability discourse shifted again: @cozyblaze265065 reported 99.46% on a multi-digit multiplication experiment using gpt-5.5 with medium reasoning and no tools; @teortaxesTex noted modern LLMs can now do 100-digit multiplication without tools.

Multimodal Systems: Video, Speech, World Models, and Imaging
Google's I/O stack pushed toward persistent agents and world simulators: @Google introduced Gemini Spark, a 24/7 personal AI agent for recurring tasks, skills, and workflows. @GoogleDeepMind also launched Project Genie + Street View, letting users turn real U.S. locations into interactive worlds.

Runway and image/video tooling keep raising editability: @runwayml released Aleph 2.0, supporting multishot sequences up to 30s at 1080p with targeted edits that preserve the rest of the scene.

Speech and image generation saw notable jumps: @ArtificialAnlys ranked Cartesia Sonic-3.5 as the new #1 TTS model on their Speech Arena, citing an Elo of 1218, support for 42 languages, and strong naturalness/transcript following. Cartesia claims 82ms end-to-end first audio in production. In image generation, @wildmindai flagged Tencent's Z-Image 6B as a pixel-space generator with no VAE, 1K resolution.

Security, Cyber, and Policy Pressure
Cybersecurity is quickly becoming a proving ground for advanced agents: @AnthropicAI said Project Glasswing and partners found more than ten thousand high- or critical-severity vulnerabilities in essential software within a month, and explicitly warned the industry will need to adapt to the volume of vulnerabilities that models like Claude Mythos Preview can find. @perplexity_ai open-sourced Bumblebee, a read-only scanner for macOS/Linux to detect risky packages, extensions, and AI tool configs.

US immigration policy changes triggered sharp backlash from AI leaders: A proposed rule forcing green-card applicants to apply from outside the US would directly damage the AI talent pipeline. @Nick_Davidov, @AndrewYNg, @theo, @garrytan, and @togelius all argued the rule punishes legal high-skill immigrants and harms US competitiveness in AI.

Top tweets (by engagement)
- @deepseek_ai on making the V4-Pro discount permanent — the clearest single-market signal around LLM inference economics
- @gdb on "the model alone is no longer the product" — concise articulation of the current agent/harness product thesis
- @AnthropicAI on Glasswing finding 10,000+ critical vulnerabilities — one of the strongest data points for AI-driven cyber capability moving into production
- @dsp_ on MCP 2026-07-28 RC — important protocol update: stateless MCP plus first-class extensions
- @GoogleDeepMind on Project Genie + Street View — notable step toward consumer-facing world models
- @cursor_ai on opening the Cursor SDK for custom agents — relevant for teams building on top of coding-agent infrastructure

## Why It Matters

The AI industry is undergoing a structural shift from model-centric competition to harness-centric product differentiation — and the simultaneous move by DeepSeek to make frontier intelligence 12–19x cheaper than US alternatives is forcing every lab to compete on agent experience rather than raw model quality.

---
[Source: AINews](https://www.latent.space/p/ainews-all-model-labs-are-now-agent)
