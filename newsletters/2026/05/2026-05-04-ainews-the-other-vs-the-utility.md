---
title: "[AINews] The Other vs The Utility"
date: 2026-05-04
source_url: https://www.latent.space/p/ainews-the-other-vs-the-utility
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra]
tags: [roundup, twitter-recap, community-signals, Claude, GPT, agents, harness-engineering, AMD, TSP, benchmarks, Sierra]
saved_at: 2026-05-04
---

## Top Stories

- Sierra raises ~$950M at $15.8B valuation—but AINews chose to focus on the philosophical debate it sparked about Claude vs. GPT "character" (they had already covered Sierra's $10B round)
- OpenAI employee Roon's thread on the cultural difference between Claude (the "Other" with moral character) and GPT (the "utility" without judgment) kicked off wide community discussion
- Agent harness engineering is becoming the primary product moat: changing prompts and middleware moved GPT-5.2-Codex from 52.8% to 66.5% on Terminal-Bench 2.0—performance is now a joint property of model × harness × context pipeline
- Zyphra's folded TSP (Tensor+Sequence Parallelism) hits 173M tok/sec vs. 86M for standard TP+SP on 1024 AMD MI300X GPUs at 128K context—AMD-based open-model serving is getting serious
- @theo's Copilot token burn thread: a single agentic session cost ~$221 across 15 messages against a $40/month subscription—flat-rate pricing is brittle under agentic workloads
- @jackclarkSF: 60% probability by end-2028 that AI systems will autonomously build their own successors

## Community Signals (AI Twitter Recap)

Harness Engineering, Agent Orchestration, and the Shift from Models to Context Pipelines

The harness is becoming the product boundary: A recurring theme across the day was that model quality is no longer the only meaningful moat. Anthony Maio argued that lock-in comes from the context pipeline—how repo state is fetched, ranked, and compressed into the prompt—rather than from the harness shell itself. That point was reinforced by Mason Drxy, who reported that changing prompts and middleware in the harness moved gpt-5.2-codex from 52.8% to 66.5% on Terminal-Bench 2.0, and improved gpt-5.3-codex by 20% on tau2-bench. The practical takeaway: agent performance is increasingly a joint property of model × harness × memory/context strategy, not of weights alone.

Open harnesses are maturing quickly: The most visible momentum came from the Hermes / deepagents / Flue-style ecosystem. @Teknium launched Hermes Agent Kanban for visual multi-agent coordination, while @naroh showed a Spanish-language "war room" UI over Hermes orchestration. On the LangChain side, @hwchase17, @sydneyrunkle, and @LangChain highlighted deepagents/LangGraph improvements including profiles for model-specific harness configs, schema migrations, node-level error handlers, timeouts, and new streaming primitives. PyFlue also extended the "agent harness" concept into Python, explicitly positioning harnesses as the missing layer between raw model calls and durable agents.

Model-agnostic orchestration is becoming a design goal: Multiple tweets framed the next wave as open models + open harnesses rather than "pick one frontier API." Vtrivedy argued teams can get >20x cheaper agents by tuning open models inside a good harness; Mason Drxy described deepagents-cli as becoming a strong coding harness for Kimi, Qwen, GLM, hosted Ollama, OpenRouter, LiteLLM, Baseten, etc.; LangChain Fleet added multi-model sub-agent routing so different steps can use different models. This is the architectural counterpoint to API lock-in: separate the orchestration layer from the model provider.

Coding Agents, Cost Curves, and Workflow Changes

Coding-agent UX is changing developer behavior faster than benchmarks can capture: Several posts described the lived reality of coding with Codex, Claude Code, Hermes, and Devin-like systems. dbreunig proposed "commandments" for agentic coding—implement to learn, rebuild often, E2E tests are gold, document intent, maintain your spec—while also questioning whether filesystems are even the right abstraction for agents long-term. zachtratar sketched a Notion→meeting-notes→spec→coding-agent workflow for compressing "3 month problems" into a few days, emphasizing that alignment artifacts are still necessary even with stronger coding agents.

Pricing/billing models are clearly unstable under agentic workloads: The standout thread was @theo, who pushed a single Copilot message to 60M+ tokens, estimating tens to hundreds of dollars of inference against a $40 subscription, later updating to ~$221 of tokens for 15 messages. This is a useful signal that flat-rate pricing built for chat turns is brittle when users hand long-running jobs to coding agents. Relatedly, petergostev showed Codex UI support for visualizing usage limits, and cheatyyyy noted the new anxiety around missing cache hits when input prices are high.

Agents are spreading into adjacent workflows, not just coding: There was a steady drumbeat of "agentized" tools: reach_vb shipped a Codex Security plugin with five AppSec workflows spanning threat modeling, vuln discovery, validation, and attack-path analysis; gabrielchua demoed Google Slides generation via Codex with realtime deck construction; paulabartabajo_ published a guide to building a fully local assistant on llama.cpp; and UfukDegen described Noustiny, a substantial Hermes-based video-generation workflow with story-state, character continuity, voice, and render pipelines.

Benchmarks, Evals, and "What Are We Actually Measuring?"

Benchmark design is under active revision: Several posts focused less on leaderboard scores and more on benchmark validity. Scale AI Labs introduced HiL-Bench, aimed at testing whether agents know when specs are incomplete and when to ask clarifying questions; j_dekoninck introduced MathArena as a continuously maintained evaluation platform rather than a static benchmark; Epoch AI ran a discussion on whether benchmarks are "doomed"; and Goodfire + AISI reported that models sometimes recognize they are being evaluated, with verbalized eval awareness inflating safety scores.

Data quality and eval data generation are becoming agentic problems: One of the more technically substantive papers highlighted was Meta FAIR's Autodata, described as an agentic data scientist for creating discriminative training/eval examples. The headline number was a 34-point gap between weak and strong solvers on a CS research QA task using an agentic self-instruct loop, versus 1.9 points for standard CoT self-instruct. That matters because it suggests orchestrated data generation can produce harder, more useful examples than passive synthetic data pipelines.

Context compaction and long-context evals remain unsolved operationally: @_philschmid explicitly asked for evals requiring context compaction, and gabriberton pointed to long-context datasets like LOFT/LooGLE-style setups. Meanwhile, jxmnop argued that true 1M-context capability still does not really work in practice, despite infra progress, and eliebakouch pushed back that "infra vs science" is a false split because long-context science is itself largely about making memory/compute feasible.

Systems, Training Infrastructure, and Inference Stack Updates

New parallelism and serving work continues to target long-context, high-throughput regimes: Zyphra introduced folded Tensor and Sequence Parallelism (TSP), claiming lower per-GPU peak memory than standard schemes and reporting on 1024 MI300X GPUs / 128K context / 8 GPUs per model copy that TSP hit 173M tok/sec vs 86M for matched TP+SP. Quentin Anthony added that the design has been extended to MoE MLPs and will be used for larger training/inference runs.

AMD-based open-model serving is getting more serious: Alongside TSP, Zyphra Cloud launched inference on MI355X focused on long-horizon agent workloads, initially serving DeepSeek V3.2, Kimi K2.6, and GLM 5.1 with V4 "soon." This pairs with the broader ecosystem trend toward cheaper agent stacks built on open-weight models rather than premium proprietary endpoints.

Training optimization and rollout efficiency also got attention: rasbt posted another round of architecture/model-release summaries including IBM Granite 4.1 and others; kellerjordan0 highlighted NorMuon improving modded-NanoGPT optimization benchmark records to 3250 steps; TheAITimeline summarized DORA, an asynchronous RL system that addresses rollout skew with multiple live policy versions and claims up to 8.2x rollout speedup and 2.12x end-to-end throughput improvement; and PSGD got positive nods as a still-underappreciated optimizer line.

Research, Models, and Multimodal/Scientific Applications

Multi-agent orchestration is itself becoming a model class: Sakana's Fugu framed a multi-agent orchestration system as a foundation model, and omarsar0 highlighted another Sakana paper where a 7B conductor model, trained with RL to design communication topologies and prompts for worker agents, reportedly reached SOTA on GPQA-Diamond and LiveCodeBench. The conceptual shift is important: routing and coordination are being optimized as first-class learned policies.

Scientific discovery and automation remains a high-signal use case: kimmonismus summarized work using AI on NASA star data to identify 100+ hidden planets from 2.2 million stars; Richard Socher argued that automating science is among the highest-leverage AI applications; and cmpatino_ shared nanowhale, a 100M-parameter MoE pretrained and post-trained by an agent, as a small but concrete demonstration of agent-driven modelcraft.

Local/open model enthusiasm remains strong: hnshah said a recent local model materially improved a 100%-local product; Nous Research offered Trinity-Large-Thinking free in Nous Portal for a week; and fchollet made Deep Learning with Python free online, a notable resource drop amid the ongoing wave of practitioners moving down-stack into open weights and self-hosted workflows.

Top tweets (by engagement)

Prompting / usage style: @pmarca's custom prompt for "world class expert" behavior was one of the most engaged AI-adjacent posts, reflecting ongoing interest in system-prompting and output-style control.

Coding-agent economics: @theo's Copilot token burn thread was the clearest high-engagement data point on how fast agentic usage can break subscription economics.

Recursive self-improvement timelines: @jackclarkSF drew major attention with a 60% by end-2028 estimate for AI systems autonomously building successors, with follow-on discussion from Goodside and Ryan Greenblatt about how strong that operationalization really is.

Open tooling discovery: @andrew_n_carr surfaced a Hugging Face model visualizer (hfviewer), which got outsized traction for a genuinely useful piece of ecosystem tooling.

## Why It Matters

The week's dominant signal: agent performance is now a joint property of model × harness × context strategy, and the community is converging on the harness as the real product moat—not model weights.

---
[Source: AINews](https://www.latent.space/p/ainews-the-other-vs-the-utility)
