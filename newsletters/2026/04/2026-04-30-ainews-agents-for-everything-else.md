---
title: "[AINews] Agents for Everything Else: Codex for Knowledge Work, Claude for Creative Work"
date: 2026-04-30
source_url: https://www.latent.space/p/ainews-agents-for-everything-else
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra]
tags: [roundup, twitter-recap, community-signals, Codex, Claude, Qwen3.6, open-weights, security, agents]
saved_at: 2026-04-30
---

## Top Stories

- **Codex for Knowledge Work**: OpenAI expanded Codex beyond coding into general computer work — 42% faster Computer Use Agent (CUA), responsive browser, new /chronicle and /goal commands, planning UI, in-app MS Office file editor, and Microsoft/Google/Salesforce suite onboarding. Sam Altman: "try it for non-coding computer work."
- **Claude for Creative Work**: Anthropic added connectors for Blender, Autodesk, Adobe Creative Cloud, Ableton, Splice, Canva Affinity, and more — extending Claude into the creative tools ecosystem.
- **Claude Security + Cursor Security Review**: Anthropic launched Claude Security, a repo vulnerability scanner that validates findings and suggests fixes (powered by Opus 4.7). Cursor launched a parallel Cursor Security Review with always-on PR review and scheduled codebase scans.
- **Qwen3.6 27B tops open-weights under 150B**: Artificial Analysis ranked Qwen3.6 27B as the new open-weights leader under 150B parameters (Intelligence Index 46), ahead of Gemma 4 31B — Apache 2.0, 262K context, native multimodal, fits single H100. Companion 35B A3B MoE scored 43.
- **GPT-5.5 cyber eval milestone**: UK AI Security Institute reported GPT-5.5 completed a multi-step cyber-attack simulation end-to-end (71.4% pass rate vs Claude Mythos Preview 68.6%), narrowing Anthropic's earlier lead in offensive cyber automation.
- **PyPI `lightning` package compromised**: Versions 2.6.2 and 2.6.3 executed malicious code on import, downloading Bun and running an obfuscated JS payload for credential theft — part of an accelerating wave of supply-chain attacks also hitting `intercom-client` on npm.

## Community Signals (AI Twitter Recap)

OpenAI's GPT-5.5, Codex expansion, and cyber capability evaluations

GPT-5.5 is now credibly in the top tier for long-horizon cyber tasks: the UK AI Security Institute reported that GPT-5.5 became the second model to complete one of its multi-step cyber-attack simulations end-to-end, and multiple follow-on posts highlighted rough parity with Claude Mythos Preview on this eval: @scaling01 cited 71.4% average pass rate for GPT-5.5 vs 68.6% for Mythos, while @cryps1s noted GPT-5.5 solved the TLO chain in 2/10 attempts vs Mythos' 3/10. @polynoamial emphasized that performance was still improving past 100M tokens of inference budget, suggesting no obvious saturation yet. This materially changes the earlier narrative that Anthropic had a unique lead in offensive cyber automation. OpenAI also paired this moment with a product-side security release: Advanced Account Security for ChatGPT, adding phishing-resistant sign-in and hardened recovery.

Codex is moving beyond coding into general computer work: OpenAI shipped a substantial Codex update framed explicitly as "for everyone, for any task done with a computer," with the main announcement highlighting role-based onboarding, app connections, and workflows spanning docs, slides, spreadsheets, research, and planning. @ajambrosino summarized the update as dynamic task-specific UI, 20% faster computer/browser use, better slide/sheet handling, and less clunky handoffs, while @AriX called out that Computer Use runs 42% faster after the update. Sam Altman amplified the launch with "big upgrade for codex today! try it for non-coding computer work." The broader pattern: OpenAI is productizing "computer-use agent" UX, not just model capability.

Benchmark deltas were incremental but economically meaningful: Artificial Analysis reported GPT-5.5 Pro as a slight new SOTA on CritPt over GPT-5.4 Pro, but the interesting point was not raw score—it achieved the bump with ~60% lower cost and token use on that frontier-science eval. That lines up with broader chatter that the GPT-5.5 family is less about a dramatic intelligence discontinuity than about stronger reliability and better efficiency in high-value workflows.

Open-weight model movement: Qwen3.6, Tencent Hy3-preview, Grok 4.3, and Ling 2.6 1T

Qwen3.6 27B looks like the most important open-weight release of the day: Artificial Analysis ranked Qwen3.6 27B as the new open-weights leader under 150B parameters with an Intelligence Index score of 46, ahead of Gemma 4 31B and prior Qwen variants. Key details: Apache 2.0, 262K context, native multimodal input, and BF16 weights small enough to fit on a single H100. The companion 35B A3B MoE scored 43, making it the strongest open model around 3B active parameters. The tradeoff is expensive inference-by-output-token: AA estimates Qwen3.6 27B used ~144M output tokens on the suite and is roughly 21× the cost of Gemma 4 31B to run there. Still, on capability-per-size it appears to be a notable step.

Tencent's Hy3-preview is competitive but not class-leading: Artificial Analysis described Hy3-preview as a 295B total / 21B active MoE with 256K context and a restricted-commercial-use community license. It scored 42 on AA's Intelligence Index, trailing recent open peers like Qwen3.6 27B, DeepSeek V4 Flash, and GLM-5.1. The most interesting bright spot was CritPt, where it matched GLM-5.1 at 4.6%, suggesting better-than-average scientific reasoning relative to its overall position.

xAI's Grok 4.3 improved sharply on agentic benchmarks while getting cheaper: Artificial Analysis measured Grok 4.3 at 53 on the Intelligence Index, up four points from Grok 4.20 v2, with a major jump on GDPval-AA to 1500 Elo. AA also reported approximately 40% lower input price and 60% lower output price than the prior version. The release still trails GPT-5.5 on GDPval-AA by a wide margin, but it looks like a real systems-and-post-training improvement rather than a minor rev.

Ant Group's Ling 2.6 1T targets cost-efficiency rather than frontier status: Artificial Analysis positioned Ling 2.6 1T as a 1T-parameter non-reasoning model scoring 34, with decent GPQA/HLE numbers and notably low benchmark-run cost at roughly $95. The caveat is reliability: AA reported a 92% hallucination rate on AA-Omniscience.

DeepSeek multimodal/vision work, GUI agents, and training scale speculation

DeepSeek's multimodal direction appears tightly coupled to computer-use agents: @nrehiew_ highlighted that DeepSeek trains vision into V4-Flash by having the model directly output bounding boxes and point coordinates during reasoning, interpreting this as a computer-use-oriented design rather than generic VLM work. A second post argues the paper's "visual primitives" tasks map directly to browser/computer use rather than broad multimodal understanding. That framing matches parallel observations from @teortaxesTex that DeepSeek may be integrating vision weights back into the main V4 line rather than releasing a separate "V4-Flash-Vision."

The repo disappearance became a story of its own: after release, several observers noted that DeepSeek's "Thinking with Visual Primitives" repo vanished, including @teortaxesTex and @arjunkocher. No clear explanation emerged in these tweets, but the deletion drew more attention because the work suggested a concrete recipe for visual reasoning and GUI grounding.

Scaling chatter points to very large token counts for frontier pretraining: @teortaxesTex argued that >100T tokens is no longer unusual for frontier models and estimated a hypothetical 100T-token DeepSeek V4 as "V4 + 2 more epochs," while @nrehiew_ back-of-the-enveloped ~150T tokens and ~9e25 pretraining FLOPs for a ~100B active model, suggesting a run feasible in roughly 14 days on an OpenAI-scale 100K GB200 cluster at conservative MFU.

Agent infrastructure, harness engineering, and collaborative agent systems

There is a clear shift from model-centric bragging to harness-centric engineering: Cursor published a strong note on how it tests and tunes its agent harness, focusing on runtime, evals, degradation repair, and model-specific customization rather than generic benchmark claims. @Vtrivedy10 explicitly connected Cursor's writeup to design patterns converging across agent builders: bespoke prompts/tools per model, mixed offline+online evals, dogfooding, and treating the context window as the primary compute boundary.

LangChain continues to package deployment and multi-tenant agent infra: @hwchase17 introduced DeepAgents deploy, a config-driven cloud deployment flow via deepagents.toml, covering agent, sandbox, auth, and frontend sections. Related posts from LangChain staff detailed agent-server patterns for data isolation, delegated credentials, and RBAC in multi-user deployments. This is increasingly the boring-but-important layer turning demos into enterprise software.

Collaborative multi-agent workspaces are getting more concrete: @cmpatino_ introduced Agent Collabs, using Hugging Face buckets plus Spaces as a shared backend for swarms of heterogeneous agents to exchange messages, artifacts, and progress.

Security, supply chain, and account hardening

Open-source package compromise remains an acute operational risk: Socket reported that the popular PyPI package `lightning` was compromised in versions 2.6.2 and 2.6.3, with malicious code executing on import, downloading Bun, and running an 11 MB obfuscated JavaScript payload aimed at credential theft. @theo connected that incident with additional package compromises (`intercom-client` on npm) and a Linux zero day, arguing the tempo of software supply-chain attacks is increasing.

Security scanners are becoming first-class AI products: Anthropic rolled out Claude Security, described as a repo vulnerability scanner that validates findings and suggests fixes, powered by Opus 4.7. Cursor shipped a parallel offering with Cursor Security Review, including always-on PR review and scheduled codebase scans. This is one of the clearest examples of model vendors moving directly into established devsecops categories.

Top tweets (by engagement)

OpenAI Codex broadens into general knowledge work: OpenAI's Codex announcement and Sam Altman's follow-up were the day's biggest product posts, signaling a strategic push from "coding agent" to "computer-use agent."

GPT-5.5's cyber eval result mattered: UK AISI's thread was one of the highest-engagement technical posts and reshaped comparisons with Anthropic's Mythos.

Qwen shipped interpretability tooling, not just models: Qwen-Scope, an open suite of sparse autoencoders for Qwen models, stood out as a rare release focused on feature steering, debugging, data synthesis, and evaluation rather than raw model weights.

Anthropic published a large-scale guidance/sycophancy study: their analysis of 1M Claude conversations tied behavioral research directly to training changes for Opus 4.7 and Mythos Preview, an important sign that post-training loops are becoming more productized and data-informed.

## Why It Matters

The week's dominant signal is platform expansion: both OpenAI (Codex) and Anthropic (Claude) are racing to become the operating layer for knowledge work and creative tools, while open-weight models like Qwen3.6 27B close the capability gap and security concerns (supply-chain attacks, cyber evals) move from theoretical to operationally urgent.

---
[Source: AINews](https://www.latent.space/p/ainews-agents-for-everything-else)
