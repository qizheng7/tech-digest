---
title: "[AINews] New AI Infra Decacorns: Fireworks, Baseten (with OpenRouter on the Way)"
date: 2026-05-27
source_url: https://www.latent.space/p/ainews-new-ai-infra-decacorns-fireworks
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, ai-infra, ai-startup, genai-llm]
tags: [roundup, twitter-recap, community-signals, Fireworks, Baseten, OpenRouter, inference-decacorn, harness, DeepSWE, vLLM-Rust, Claude-Mythos, MiniMax-M3, Huawei]
saved_at: 2026-06-01
---

## Top Stories

- Fireworks AI reportedly raising at $15B valuation (3.75x in 7 months); Baseten "is raising" at $11B (2.2x in 3 months); OpenRouter closes $113M Series B (5x volume growth to 25T tokens/week in 6 months) — inference infra is the new unicorn-to-decacorn track
- Harness engineering is becoming the main differentiator: model + harness + eval loop now beats stronger base model; DeepSWE benchmark framed as "first code bench that actually aligns with how it feels to use these models"
- vLLM merged Rust frontend: ~837 req/s vs ~162 req/s on preprocess-heavy workload in a single process — CPU-API server bottleneck solved
- Claude Mythos reportedly solved Erdős problem #90, with Sébastien Bubeck noting that with an appropriate harness both Mythos and GPT-5.5 can reproduce what an internal model had done one-shot
- "Language Models Need Sleep" paper got notable attention — sleep-like consolidation phase converts recent context into persistent fast weights before clearing KV cache; alternative to ever-growing KV caches for agents
- MiniMax M3 teased as open source: 9.7× prefilling and 15.6× decoding at 1M tokens vs M2; block-sparse two-stage attention path different from DeepSeek's compressed-attention variants

## Community Signals (AI Twitter Recap)

Agent Harnesses, Coding Benchmarks, and the Shift Beyond "Just the Model"
Harness engineering is becoming the main differentiator for coding agents: Several posts converged on the same thesis: the winning stack is now model + harness + eval loop, not just a stronger base model. A long Zhihu summary argued that DeepSeek is explicitly building a harness team to close the loop between model outputs, runtime feedback, validation, and correction, with a claimed cached-input cost advantage that would support tighter interaction/verification loops. In parallel, Google's Gemini Managed Agents guide framed agent infra as a single API call to a managed harness with sandboxing, persistence, and mounts, while LangChain's updated create_agent docs and dair.ai's "harness" paper summary formalized the same stack: context governance, trustworthy memory, dynamic skill routing.
Benchmarks are getting closer to real developer experience: DeepSWE, introduced as a new benchmark for agentic coding, got strong endorsement from practitioners; @theo called it "the first code bench that actually aligns with how it feels to use these models coding." It also created more separation at the top end than public SWE leaderboards often show. Related benchmark signals: Qwen3.7 Max debuted at #4 on Code Arena: Frontend, roughly on par with Claude Opus 4.6 on agentic webdev tasks. Anthropic shipped a security-guidance plugin for Claude Code and reported a 30–40% reduction in security-related PR comments in internal use.

Research Agents, Long-Horizon Reasoning, and "Sleep" for Context Compression
Math/science agents showed more evidence of capability overhang — conditional on the right harness: The strongest cluster of tweets was around models tackling old open problems. A mathematician reported Claude Mythos solving Erdős problem #90, with follow-up detail that the model often converged to a different, cleaner proof path than OpenAI's earlier route. This was echoed by @_sholtodouglas and @kimmonismus, then sharpened by Sébastien Bubeck: with an appropriate harness, both Mythos and GPT-5.5 can reproduce what an internal model had done one-shot, implying a large amount of latent capability not exposed by vanilla chat UX.
Long-horizon memory is resurfacing as a core bottleneck: The paper "Language Models Need Sleep" got notable attention. The mechanism is a sleep-like consolidation phase where recent context is converted into persistent fast weights before clearing the KV cache, moving compute into an offline pass while preserving wake-time latency. dair.ai's summary emphasized the systems angle: this is an alternative to ever-growing KV caches for agents with long trajectories. This theme connected neatly with ongoing discussion about memory systems in agents, including Omar's pointer to Anthropic's memory talk and Dream feature.
Open deep-research agents and science forecasting also advanced: QUEST, a family of open 2B–35B models for long-horizon fact-seeking, citation grounding, and report synthesis, was released as a general-purpose deep research agent.

Model, Optimizer, and Architecture Updates
Optimizer work remains lively, especially around Muon variants and schedule-free training: AMUSE proposes Anytime MUon with Stable gradient Evaluation, combining Muon with schedule-free-style gradient evaluation for stable anytime training without LR decay, reporting gains at 124M / 720M / 1B scale and on ViT/ImageNet fine-tuning.
Sparse attention design space continues to diversify: MiniMax teased M3 as open source, and follow-on technical commentary suggested a new block-sparse two-stage attention path. @kimmonismus summarized the reported speedups: 9.7× prefilling and 15.6× decoding at 1M tokens versus M2. @eliebakouch added that M3 appears to move back to GQA-based sparse attention with block selection on real KV, distinct from DeepSeek's compressed-attention variants.
Vision/open model releases and ranking updates: PrismML released Bonsai Image 4B, including 1-bit and ternary variants intended to run locally on laptops and phones; a follow-up noted browser-local execution was possible at ~3GB footprint. Microsoft's MAI-Image-2.5 debuted at #3 on the Image Arena. Artificial Analysis measured Gemini 3.5 Flash at up to ~280 output tok/s with materially stronger agentic performance, but at ~5× the cost of Gemini 3 Flash.

Infra, Systems, and the Semiconductor Stack
Huawei's "τ scaling" paper was read mostly as an engineering roadmap, not a new law: A very detailed thread argued Huawei's "A Time Scaling Theory for Multi-Layer Electronic Systems" should be interpreted as a strategic manifesto / white paper. The core proposal is to treat time constant τ, not process node, as the unifying metric across device, chip, and datacenter scales. The most concrete claims: LogicFolding on a future Kirin design, including +55% density, +41% energy efficiency, and +13% frequency at fixed node. The same thread was careful to note missing validation artifacts — die photos, SEMs, workload details, yield curves — and to interpret the most eye-catching numbers as promising but unverified.
Datacenter power and inference supply constraints are becoming first-order concerns: SemiAnalysis published on the 800VDC transition (recommended by John Carmack), highlighting crossovers from EV power electronics into datacenter design. Epoch AI estimated a possible inference compute crunch: demand appears to be growing faster than serving capacity, especially for long-context workloads — throughput degrades sharply with longer contexts and demand growth may already be outrunning supply.

Production Tooling and Developer Infrastructure
Serving/inference stacks got meaningful performance and observability updates: vLLM merged a Rust frontend as a drop-in alternative to the Python API server, with early numbers showing ~837 req/s vs ~162 req/s on a preprocess-heavy workload in a single process. W&B launched an MCP server to let coding agents inspect experiments and training runs, with a schema-first redesign aimed at avoiding context-window blowups. Unsloth added support for running GPT, Claude, and other APIs inside its local UI, including prompt caching and code execution.
Cloudflare, OpenRouter, and vector/retrieval vendors pushed the "productionization" layer: OpenRouter announced a $113M Series B and said weekly volume had grown from 5T to 25T tokens over six months. Cloudflare relaunched its startups program with up to $350k in credits. On retrieval infra, Booking.com discussed scaling to 100M+ embeddings, including filtered vector search, reads-during-writes, concurrency, and human-in-the-loop evals for partner messaging agents.

Top tweets (by engagement)
- Codex / agentic coding in practice: @bunkaich showing Codex help reverse-engineer and patch firmware on a cheap MP3 player, spanning chip inspection, OS extraction, binary analysis, and flashing a modified image
- DeepSWE benchmark launch: @serenaa_ge's DeepSWE announcement became the main reference point for "does this match real coding experience?" discussion
- Claude Code security plugin: @ClaudeDevs' release paired a concrete product launch with an internal metric: 30–40% fewer security-related PR comments
- OpenRouter financing + production token growth: @OpenRouter's $113M Series B is one of the clearer market signals that routing and multi-model infra are now seen as durable platform layers
- vLLM Rust frontend: @vllm_project's merge announcement mattered for anyone hitting CPU/API-server bottlenecks in high-throughput serving

## Why It Matters

Inference infra is completing the same VC maturation cycle as databases and CDNs — Fireworks, Baseten, and OpenRouter simultaneously crossing decacorn thresholds signals that the serving layer is now a standalone, defensible market, not a commodity attached to model providers.

---
[Source: AINews](https://www.latent.space/p/ainews-new-ai-infra-decacorns-fireworks)
