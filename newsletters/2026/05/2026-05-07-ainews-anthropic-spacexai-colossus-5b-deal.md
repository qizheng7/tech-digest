---
title: "[AINews] Anthropic-SpaceXai's 300MW/$5B/yr Deal for Colossus I, ARR Growth is 8000% Annualized"
date: 2026-05-07
source_url: https://www.latent.space/p/ainews-anthropic-spacexais-300mw5byr
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [roundup, twitter-recap, community-signals, Anthropic, SpaceX, xAI, Colossus, compute, Claude-Code, MRC, OpenAI, Genesis-AI, Zyphra, Windsurf, Cursor, harness, MTP, llama-cpp]
saved_at: 2026-05-07
---

## Top Stories

- Anthropic secured access to SpaceX/xAI's Colossus 1 (~300MW, ~220K NVIDIA GPUs) in an estimated $5B/yr deal; Claude Code 5-hour rate limits doubled immediately for Pro/Max/Team, peak-hour throttling removed for Pro/Max, Opus API rate limits substantially increased — driven by 80x unexpected usage growth (8000% annualized ARR growth)
- Anthropic's "Code with Claude" developer event announced managed agent features: Dreaming (cross-session memory/context) and Outcomes (rubrics/grading for agent quality control); Dario predicted 2026 as the year of one-person billion-dollar companies
- OpenAI released MRC (Multipath Reliable Connection), an open OCP Ethernet networking protocol for 100K+ GPU clusters, co-developed with AMD, Broadcom, Intel, Microsoft, NVIDIA; already deployed on GB200 supercomputers
- Zyphra released ZAYA1-8B, a reasoning MoE with <1B active parameters under Apache 2.0, claiming strong math/reasoning at minimal compute; backed by AMD partnership
- llama.cpp landed beta MTP (Multi-Token Prediction) support targeting Qwen3.x models — ~75% acceptance rate with 3 draft tokens, typically >2x token-generation throughput over baseline
- ProgramBench (Meta): top models score 0% on whole-repo-from-scratch generation (SQLite, FFmpeg, PHP compiler); Terminal-Bench 2.1 patched 28/89 tasks with up to 12-point score shifts

## Community Signals (AI Twitter Recap)

Top Story: Anthropic and Claude announcements/commentary

Anthropic had a dense news cycle centered on compute, Claude Code limits, and agent platform direction. 

Officially, Anthropic announced a new compute partnership with SpaceX that will "substantially increase" capacity and immediately translate into higher limits for Claude products: @claudeai said the deal boosts compute enough to raise usage limits, followed by specifics from @claudeai: Claude Code's 5-hour rate limits are doubled for Pro, Max, Team, and seat-based Enterprise; peak-hours limit reductions are removed for Pro and Max; Opus API rate limits are substantially increased. 

xAI framed the deal as Anthropic getting access to Colossus 1 via SpaceXAI for "additional capacity for Claude" @xai, while Anthropic CTO Tom Brown added that Claude inference would be ramped up on Colossus "in the next few days" @nottombrown. 

The company also ran its "Code with Claude" event, with a livestreamed keynote and sessions on Claude Code, GitHub-scale usage, and managed agents @ClaudeDevs, prompting substantial real-time commentary from developers and observers @simonw, @latentspacepod. 

Around this, discourse branched into four themes: 
(1) compute bottlenecks were more severe than many assumed, reportedly due to unexpected usage growth; 
(2) users welcomed the 5-hour limit increase but questioned unchanged weekly limits; 
(3) people debated whether Anthropic's new managed-agent features like memory/"Dreaming" and rubrics/"Outcomes" are real product differentiation or commoditizable harness features; and 
(4) Anthropic's safety/governance positioning continued to attract both praise and criticism, including claims from critics that some Anthropic employees project "only we can be trusted with AGI," and counterclaims from Anthropic-adjacent voices that the more common internal view is closer to "no one can be trusted with AGI" than "only us" @aidan_clark, @kipperrii.

Official facts and confirmed details

Anthropic announced a SpaceX compute partnership to increase capacity @claudeai.
Effective immediately, Anthropic says it is:
- Doubling Claude Code's 5-hour rate limits for Pro, Max, Team, and seat-based Enterprise
- Removing peak-hours limit reduction on Claude Code for Pro and Max
- Substantially increasing API rate limits for Opus models

Anthropic CTO Tom Brown said Claude inference would start ramping on Colossus within days @nottombrown.
Anthropic product/eng lead Amol Avasare clarified that weekly limits were not increased yet because only a small percentage of users hit weekly limits, while a much larger percentage hit 5-hour limits; more changes may come as compute lands @TheAmolAvasare.

Compute details and scale claims

Several tweets added quantitative claims about the scale of the SpaceX/xAI arrangement. These are not from Anthropic's main announcement tweets, but they were widely circulated:
- @arohan cited "more than 300 megawatts of new capacity" and "over 220,000 NVIDIA GPUs within the month."
- @scaling01 claimed Colossus 1 includes ~150,000 H100s, 50,000 H200s, and 30,000 GB200s.
- @Yuchenj_UW repeated the 220,000 GPU figure and added an unverified claim that Anthropic had committed $200B on Google TPUs.
- Elon Musk later said SpaceXAI was comfortable leasing Colossus 1 because xAI had already moved training to Colossus 2 @elonmusk, and @eliebakouch claimed Colossus 2 is already at ~500k Blackwells.

These numbers are best treated as partly official-adjacent but not fully canonized. The broad factual takeaway: Anthropic secured a very large, near-term external inference capacity expansion.

Evidence the bottleneck was real

@kimmonismus summarized remarks from a Dario/Daniela interview: usage grew ~80x unexpectedly, which purportedly caused the compute shortage, and the SpaceX deal is the first major attempt to address it.
@czajkadev explicitly interpreted the update as proof that compute was the bottleneck.
@scaling01 generalized to a macro thesis: frontier labs are compute constrained enough to rent datacenters from competitors.

Product implications: Claude Code, API, and managed agents

The event also highlighted Anthropic's broader platform ambitions around agents:
- Dreaming = memory / cross-session context
- Outcomes = rubrics / grading / objective tracking
- Agent orchestration / managed agents direction

@RichNwan argued Anthropic is "building out their managed agents platform" with Dreaming and Outcomes, but questioned whether these are meaningfully differentiated versus open harnesses.
@latentspacepod quoted Anthropic speakers emphasizing verification, "routines are higher-order prompts," and the idea that the remaining gap is often deployment/operationalization, not raw capability.

Different opinions in the discourse

1) Positive / supportive: @alexalbert__ "More chips, more Claude." @_sholtodouglas "More compute -> straight to you."

2) Mixed / pragmatic: @btibor91 and @kimmonismus immediately noted the likely caveat: weekly caps unchanged. @sbmaruf reported still seeing rate limits after the change, implying rollout and reliability tuning were ongoing.

3) Competitive / strategic critique: @scaling01 argued Anthropic blundered its growth advantage by waiting too long, possibly conceding billions in ARR to OpenAI. @Yuchenj_UW read the move as Dario getting aggressive because of OpenAI Codex's growth.

4) Governance / safety / culture critique: @aidan_clark criticized what he says he repeatedly hears from Anthropic colleagues: a belief they alone should be trusted to build AI. @kipperrii partially agreed the "only we can be trusted" framing would be bad, but argued the real majority view is closer to "no one can be trusted with AGI."

Infrastructure, inference, and systems

OpenAI and partners released MRC (Multipath Reliable Connection), an open networking protocol for large AI training clusters, already deployed on OpenAI's biggest supercomputers @OpenAI. Commentary emphasized multipath routing, microsecond failover, and the shift of networking into a primary frontier bottleneck @kimmonismus, @gdb.

Perplexity said it built an in-house inference engine, ROSE, covering models from embeddings to trillion-parameter LLMs, and uses CuTeDSL to accelerate specialized kernel development on Hopper and Blackwell @perplexity_ai.

vLLM + Mooncake presented a strong systems result for agentic workloads with reusable prefixes: 3.8x throughput, 46x lower P50 TTFT, 8.6x lower end-to-end latency, and cache-hit improvement from 1.7% to 92.2%, scaling to 60 GB200 GPUs @vllm_project.

Unsloth + NVIDIA published three training optimizations claimed to make home-GPU LLM training ~25% faster: packed-sequence metadata caching, double-buffered checkpoint reloads, and faster MoE routing @UnslothAI.

NVIDIA work on lossless speculative decoding inside RL was highlighted as giving up to ~2.5x faster end-to-end RL at 235B scale and ~1.8x faster rollout throughput at 8B without changing policy distribution @TheTuringPost.

Baseten launched Frontier Gateway as managed infra/API/auth/rate-limit/billing for closed-weight labs; Poolside reported going from kickoff to production in 7 weeks, with P50 TTFT 146ms for Laguna XS.2 and 605ms for Laguna M.1.

Benchmarks, evals, and agent harnesses

ProgramBench asks whether language models can rebuild programs from scratch, extending beyond repair-style SWE tasks @ComputerPapers, with Ofir Press arguing benchmarks are "treasure maps" that specify the future we want @OfirPress. Top accuracy: 0% (models can still pass >50% of tests per task on average, but the all-tests criterion is intentional to prevent gaming).

Terminal-Bench 2.1 patched 28/89 tasks in TB2.0; rankings held but absolute scores moved by up to 12 points, a useful reminder that agent benchmark maintenance materially matters @terminalbench, @ekellbuch.

OBLIQ-Bench emerged as a major IR benchmark release focused on hard first-stage retrieval, where current retrievers fail to surface subtly relevant documents from large corpora @dianetc_.

Harvey launched LAB, an open-source, long-horizon legal agent benchmark covering 1,200 tasks across 24 practice areas, with support/commentary from LangChain, Baseten, Artificial Analysis, and others @saranormous.

A major theme across multiple tweets was that harness engineering is a first-class variable, often worth 10–20 points on agent benchmarks even with the same base model @masondrxy, @LangChain, @Vtrivedy10.

Model releases and model performance

Zyphra released ZAYA1-8B, a reasoning MoE with <1B active parameters, open-weight under Apache 2.0, claiming strong math/reasoning efficiency and proximity to much larger systems with test-time compute @ZyphraAI. Commentary praised its architecture/post-training stack and AMD partnership @teortaxesTex, @eliebakouch.

Google's Gemma 4 moved the open-model Pareto frontier in Code Arena: Gemma-4-31B #13, Gemma-4-26B-A4B #17 among open models @arena, @_philschmid.

Qwopus3.6-35B-A3B-v1 claimed 162 tok/s on a single RTX 5090, targeting strong one-shot frontend/web generation on consumer hardware @KyleHessling1.

DeepSeek commentary was mixed: fundraising talks reportedly target a $45B valuation led by a major Chinese state-backed semiconductor fund @jukan05, while evaluators debated weak WeirdML performance for V4-Pro versus GLM/Kimi/open competitors.

Agents, tools, and developer workflows

Cursor added context usage breakdowns across rules, skills, MCPs, and subagents to help debug context issues @cursor_ai, and described bootstrapping future Composer generations with earlier Composer models.

Cognition shipped Devin Review and Quick Review / SWE-Check in Windsurf 2.0, explicitly targeting the new bottleneck of reviewing AI-generated code @cognition, @ypatil125.

OpenAI promoted Codex subagents, framing them as a way to split work across specialized agents and merge results back into one answer @reach_vb.

Perplexity added Finance Search to its Agent API with licensed data, live market data, and citations, claiming best cohort accuracy and lowest cost per correct answer on FinSearchComp T1 @perplexity_ai, @AravSrinivas.

Google's Gemini API added multimodal retrieval to File Search using gemini-embedding-2 for PDFs and images in a single retrieval pipeline @_philschmid.

Robotics, multimodality, and research notes

Genesis AI introduced GENE-26.5, describing a full-stack robotics program with a robotics-native foundation model, human-like hand, data glove, and simulator; the model is trained across language, vision, proprioception, tactile, and action @gs_ai_, @theo_gervet.

Meta FAIR released NeuralBench, an MIT-licensed unified benchmark framework for NeuroAI with 36 EEG tasks and 94 datasets, with MEG/fMRI support planned.

Microsoft Research work on agent-readable interpretability proposed "Agentic-imodels," where coding agents evolve models that are interpretable to other LLMs; reported gains on 65 tabular datasets and downstream BLADE improvements from 8% to 73% @dair_ai.

## Why It Matters

Compute capacity is now as strategically important as model quality — Anthropic's 80x usage surge and emergency xAI infrastructure deal signals that inference supply chains, not just training breakthroughs, will determine which labs win the developer platform wars.

---
[Source: AINews](https://www.latent.space/p/ainews-anthropic-spacexais-300mw5byr)
