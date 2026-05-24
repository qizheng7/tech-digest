---
title: "[AINews] New AI Infra unicorns: Exa, Modal, TurboPuffer"
date: 2026-05-22
source_url: https://www.latent.space/p/ainews-new-ai-infra-unicorns-exa
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [roundup, twitter-recap, Modal, TurboPuffer, Exa, Codex, Gemini, RAEv2, MoE, vLLM, agent-infra, funding, robotics]
saved_at: 2026-05-23
---

## Top Stories

- Modal raises $355M Series C at $4.65B valuation; 5x growth since September, surpassing $300M ARR — AI-native cloud rebuild positioned as category winner
- TurboPuffer crosses $100M ARR in March 2026, profitable, having raised < $1M — "boring" vector DB infra generating extreme capital efficiency
- Exa closes $250M Series C at $2.2B — search infrastructure for agents gaining momentum alongside Parallel Web Systems ($100M at $2B)
- OpenAI Codex Thursday updates: Appshots, remote Mac use from locked phone, team plugin sharing, org analytics — product surface expanding from IDE to persistent cross-device operator
- Gemini 3.5 Flash tops APEX-Agents-AA benchmark, outperforming larger models; community mixed on whether benchmark gains translate to real-world utility
- MCP 2026-07-28 release candidate announced: stateless protocol (no handshake, no session ID), MCP Apps, Tasks extension, OAuth hardening

## Community Signals (AI Twitter Recap)

Model, Benchmark, and Research Updates: RAEv2, Gated DeltaNet-2, Data Filtering, and Open Math
RAEv2 and representation-first tokenization: Several researchers highlighted RAEv2 as a meaningful follow-on to Representation Autoencoders for unified vision understanding and generation. @1jaskiratsingh says the update yields >10x faster convergence, better reconstruction, and better generation, with tests extending to text-to-image and world models. A Chinese summary from @recatm usefully extracts the three main findings: summing the last K encoder layers instead of only the final layer improves both reconstruction and generation without added inference cost; RAE and REPA are complementary across semantics vs. spatial structure; and REPA can be reformulated as an internal self-guidance mechanism, avoiding extra weak-model guidance passes. @sainingxie also points to new evaluation views beyond FID, arguing there is still underexplored headroom in representation-powered pixel decoders.

Alternatives to standard attention and tokenizer assumptions: NVIDIA's Gated DeltaNet-2 decouples erase and write operations in linear attention with channel-wise gates, outperforming KDA and Mamba-3 at 1.3B parameters on language modeling and commonsense reasoning, with notable long-context retrieval gains on RULER; @rasbt called it one of the more interesting hybrid-attention directions. On tokenization, @NousResearch released a controlled study of why subword tokenization helps, simulating seven hypothesized benefits inside a 1.7B byte-level pipeline; only three of seven interventions moved validation loss at that scale. Separately, @tatsu_hashimoto reported a surprising scaling result on DCLM: with enough compute, the best data filter may be no filter, with projections suggesting the crossover for internet-scale pools lands around 1e30 FLOPs.

Mechanistic interpretability and geometry: @GoodfireAI argues the dominant "models think in curved manifolds, SAEs use straight-line features" critique is only partly right. Their proposed fix is to cluster SAE features by joint firing patterns, recovering geometry through feature groups rather than isolated atoms. This is a useful update to the current SAE discourse: not a rejection of sparse features, but a warning that interpretation should move from single features to structured ensembles.

Math as an AI research domain: The biggest scientific discussion centered on OpenAI's reported result on an Erdős unit-distance problem. @markchen90 framed it as evidence that mathematics is currently the domain most amenable to AI-assisted research breakthroughs, while @wtgowers noted that if the reported low human interaction level holds, the result is genuinely interesting. The discourse was immediately shaped by skepticism and benchmark/gameability concerns.

Agents, Harnesses, and Developer Tooling: Codex, Gemini, Devin, and Agent Infrastructure
Harnesses are still a major source of capability gains: @lvwerra released physics-intern, a science-problem harness that boosts models like Gemini 3.1 Pro from 17.7 to 31.4, surpassing GPT 5.5 Pro in that setup. The notable nuance is that GPT 5.5 Pro itself did not benefit from the harness, suggesting model-specific absorption of scaffolding tricks.

Agent design patterns are maturing from "single agent first" to explicit subagent orchestration: @cwolferesearch gives a practical synthesis: start with single-agent systems, and only move to manager/sub-agent or decentralized multi-agent topologies when tool sprawl or prompt bloat becomes unmanageable.

Codex shipped a substantial product layer on top of the model: OpenAI's "Codex Thursday" updates — Appshots (screenshot + text from Mac app windows), team plugin sharing, org analytics. The more important systems shift is remote computer use: Codex can now securely use apps on your Mac from your phone even when the Mac is locked. Strong signal that agent product surface is moving from chat IDEs to persistent cross-device operator workflows.

Gemini's agent/tool story is broadening quickly: @OfficialLoganK highlighted that Gemini 3.5 Flash ranks #1 on APEX-Agents-AA, outperforming larger models. Google expanded action surfaces: Daily Brief and connected-app actions with OpenTable, Canva, and Instacart.

Developer infra is converging around retrieval, streaming, sandboxes, and security boundaries: Weaviate shipped a built-in MCP server inside the database for hybrid BM25 + vector retrieval. LangChain introduced a sandbox Auth Proxy and a new typed streaming protocol for rendering tools, subagents, media, and interrupts as first-class projections. vLLM's Elastic Expert Parallelism enables live resizing of MoE DP/EP topology without full restarts, using direct GPU-to-GPU transfers over NVLink/RDMA.

Infrastructure, Compute, and AI Business Signals: Modal, Turbopuffer, Hark, and the Compute Race
The infra layer had one of its clearest "this is where the money is" days: @Sirupsen said turbopuffer crossed $100M run-rate in March, just 19 months after $1M, while being profitable and raising < $1M. @swyx summarized: "boring" AI infrastructure, not only glamorous frontier research, is where wealth creation is accruing.

Modal raised big and continues to look like a core AI cloud winner: @bernhardsson announced a $355M Series C at a $4.65B valuation. Investors emphasized the thesis: rebuilding the cloud stack for AI workloads from the ground up, with strong performance and developer experience.

Compute remains the strategic bottleneck, and the market appears tiered: @AymericRoucher sketched a useful compute taxonomy: US leaders (OpenAI, Anthropic, Google, with Meta/xAI joining) in the multi-gigawatt class; Chinese giants scaling from hundreds of MW toward multi-GW; European contenders such as Mistral at around 90 MW today aiming for 1 GW by 2029. @EpochAIResearch reports HBM grew from 52% to 63% of total AI chip component spending from Q1 2024 to Q4 2025.

Capital is flowing to interface/hardware bets as well as infra: @adcock_brett announced Hark raised $700M at a $6B valuation, aimed at GPU infrastructure, future model development, hardware, and multimodal/personal intelligence products.

Multimodal, Video, Biology, and Robotics: Runway, Carbon, Earth Models, and Open Humanoids
Video editing and generation are getting more compositional: Runway launched Aleph 2.0 and the new Edit Studio, letting users edit a single frame and propagate that edit through the rest of the video.

Foundation models for biology and Earth observation continue to become more usable: Hugging Face Bio's Carbon DNA model family got follow-on demos. For geospatial modeling, @cgeorgiaw reported OlmoEarth v1.1 is 3x cheaper/faster by changing the tokenization of multi-resolution Sentinel-2 inputs.

Open robotics is getting more buildable: Hugging Face's LeRobot Humanoid drew attention as a genuinely full-stack open release. @robotsdigest and @lukas_m_ziegler both emphasize: roughly $2.5k, 3D-printed, complete hardware/CAD, calibration/runtime, simulation, identification tools, and training pipelines.

Top tweets (by engagement)
- OpenAI / Codex product expansion: Codex can securely use apps on your Mac from your phone, even when the Mac is locked, plus Appshots for richer app context
- Infrastructure winners: turbopuffer at $100M run-rate, profitable, < $1M raised; Modal raises $355M Series C at $4.65B; Hark raises $700M at $6B
- Research discussions with broad technical resonance: OpenAI's Erdős-related math result discussion; RAEv2 release; "no filter" scaling result for LM data curation
- Agent capability trendlines: Gemini 3.5 Flash tops APEX-Agents-AA; Gemma 4 E4B driving an iOS simulator on-device via Argent; Devin for Windows

## Why It Matters

AI infrastructure is crystallizing into a distinct, high-value category separate from model labs — with TurboPuffer and Modal demonstrating that unglamorous compute primitives can generate the AI era's most capital-efficient businesses.

---
[Source: AINews](https://www.latent.space/p/ainews-new-ai-infra-unicorns-exa)
