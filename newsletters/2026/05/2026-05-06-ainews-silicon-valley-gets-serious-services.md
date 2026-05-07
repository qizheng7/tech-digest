---
title: "[AINews] Silicon Valley gets Serious about Services"
date: 2026-05-06
source_url: https://www.latent.space/p/ainews-silicon-valley-gets-serious
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [roundup, twitter-recap, community-signals, Anthropic, OpenAI, services, GPT-5.5, Gemma-4, RadixArk, SGLang, agents, harness-engineering, ProgramBench, Cursor]
saved_at: 2026-05-06
---

## Top Stories

- **Anthropic + Blackstone/HF/GS services JV**: Anthropic launched an unnamed joint venture with Blackstone, Hellman & Friedman, and Goldman Sachs, funded with $1.5B ($300M each from main participants), to build and deploy Claude-powered enterprise systems with an embedded professional services model
- **OpenAI "The Deployment Company"**: OpenAI announced a parallel services vehicle backed by 19 investors (TPG, Brookfield, Advent, Bain Capital), raising ~$4B at $10B pre-money; Brad Lightcap shifts from COO to lead special projects overseeing the PE-backed enterprise deployment push
- **GPT-5.5 Instant becomes ChatGPT default**: OpenAI rolled out GPT-5.5 Instant as the new default model for ChatGPT and API (`gpt-5.5-chat-latest`), bundling stronger personalization (saved memories, past chats, Gmail integration, "memory sources" visibility)
- **Gemma 4 MTP drafters released**: Google released multi-token prediction drafter checkpoints for Gemma 4, claiming up to 3x faster decoding with zero quality loss; day-0 support in vLLM, SGLang, Transformers, Ollama, MLX, and AI Edge
- **RadixArk $100M seed**: SGLang/Miles commercialization company RadixArk raised $100M seed (Accel, Spark Capital, NVIDIA, AMD), with backers including OpenAI co-founder John Schulman, PyTorch creator Soumith Chintala, and Hugging Face co-founder Thomas Wolf
- **Anthropic Financial Services event + Perplexity Computer for Finance**: Both companies pushed vertical products — Claude with FactSet/S&P/Morningstar integrations, Perplexity with 35 analyst-workflow templates and licensed financial data

## Community Signals (AI Twitter Recap)

**OpenAI's GPT-5.5 Instant, personalization rollout, and voice/agent infrastructure updates**

GPT-5.5 Instant becomes ChatGPT's new default: OpenAI rolled out GPT-5.5 Instant to ChatGPT and the API as gpt-5.5-chat-latest, positioning it as a broad upgrade in factuality, baseline intelligence, image understanding, and tone. The launch also bundled stronger personalization: ChatGPT can now use saved memories, past chats, files, and connected Gmail, while exposing "memory sources" so users can see what context influenced a reply.

OpenAI also published more infra detail around real-time products: @OpenAIDevs shared a writeup on rebuilding the WebRTC stack for ChatGPT voice and the Realtime API using a thin relay plus a stateful transceiver to reduce latency and keep conversations at speech pace. This fits the broader signal around an imminent voice refresh noted by multiple community members.

Developer-side OpenAI agent tooling keeps expanding: @OpenAIDevs announced the Agents SDK for TypeScript, including sandbox agents and an open-source harness. OpenAI continued pushing Codex UX and automation, including task progress UI and Auto Review for lower-friction approvals. Community sentiment suggests 5.5 is especially strong for high-token-budget coding and non-coding workflows.

---

**Coding agents, harness design, and benchmark pressure**

Harness quality is becoming a first-class differentiator: A recurring theme was that model quality alone no longer explains agent performance. @Vtrivedy10 argued the field is mixing incompatible assumptions about native post-trained harnesses, open harnesses, and "AGI-like" model generalization; the practical takeaway is that Model–Harness–Task fit matters more than abstract benchmark narratives. A complementary post emphasized that talking to base or minimally wrapped models makes clear how much productized agents depend on instructions, tools, context packing, and measurement loops. @masondrxy argued for ACP-style decoupling so teams can swap CLI/TUI/GUI/IDE frontends without changing the underlying harness.

Agent coding UX is fragmenting, with real disagreement on winners: @0xSero ranked Droid above Pi, Amp, OpenCode, and Codex CLI. @teortaxesTex said Hermes currently beats deepseek-tui and OpenCode on success rate, speed, and cost. On the commercial side, @kimmonismus cited TickerTrends data claiming Codex surpassed Claude Code in downloads after late-April releases, while several developers reported that Claude Code utility feels relatively flat versus last fall.

New coding benchmark — ProgramBench shows how far "whole-repo from scratch" still is: Meta researchers introduced ProgramBench, a 200-task benchmark asking models to generate substantial software artifacts (SQLite, FFmpeg, a PHP compiler) from an executable spec, without starter code or internet access. Headline result: top accuracy is 0%. Discussion split on whether the all-tests criterion is too harsh — models can pass >50% of tests per task on average, but @OfirPress defended the strict criterion as necessary to prevent partial-implementation gaming.

Practical coding automation moving into CI/security: @cursor_ai launched agents that monitor GitHub and automatically fix CI failures. @cognition introduced Devin for Security, including automated vulnerability remediation at enterprise scale and a claimed early detection of a malicious axios release before public disclosure.

---

**Inference, systems, and efficiency: Gemma 4 drafters, SGLang/RadixArk, and provider economics**

Gemma 4 gets multi-token prediction drafters across the open stack: Google released Gemma 4 MTP drafters, promising up to 3× faster decoding with no quality degradation. Day-0 or near-day-0 support in Transformers, vLLM, MLX, SGLang, Ollama, and AI Edge. @vllm_project specifically announced a ready Docker image for Gemma 4 on vLLM. The E2B drafter is only 78M parameters.

RadixArk raises a massive seed around SGLang + Miles: @BanghuaZ framed RadixArk as spanning inference, training, RL, orchestration, kernels, and multi-hardware systems; the goal is making frontier-grade infrastructure open and production-grade rather than forcing every team to rebuild scheduling, KV-cache management, and rollout systems from scratch. Community endorsements were strong.

Inference economics are now highly provider-specific: @ArtificialAnlys compared MiniMax-M2.7 across six providers and found major differences in tokens/sec, cache discounting, and blended cost. SambaNova led raw speed at 435 output tok/s, while Fireworks looked stronger on the speed/price frontier. Separately, @teortaxesTex highlighted how cache-hit rates dominate cost on some agent workloads, calling cache optimization "the main axis of cost reduction with V4."

Cold-start and distributed training remain active systems bottlenecks: @kamilsindi described a system that cut model cold starts 60×, from minutes to seconds, by serving weights from GPUs already holding them rather than cloud storage. Google DeepMind's Decoupled DiLoCo reportedly achieved 88% goodput vs. 27% for standard data parallel at scale while using ~240× less inter-datacenter bandwidth.

---

**Agents, RL environments, observability, and long-horizon research**

RL infra is shifting from "single generation + reward" to long-running action systems: @adithya_s_k released a guide comparing RL environment frameworks for the LLM era, focusing on what scales to thousands of environments. A detailed survey contrasted traditional RLVR with agentic RL, pointing to systems such as Forge, ROLL, Slime, and Seer and recurring concerns like TITO consistency, rollout latency, prefix-tree merging, and global KV caches.

Long-horizon failures are increasingly framed as horizon problems, not just capacity problems: @dair_ai summarized a Microsoft Research paper arguing that goal horizon alone can be the training bottleneck, with macro actions / horizon reduction stabilizing training and improving long-horizon generalization.

Observability is maturing into a feedback-driven improvement loop: @hwchase17 and @LangChain argued that traces alone are insufficient; the key is attaching direct, indirect, or generated feedback so observability becomes a learning system. @benhylak launched Raindrop Triage, an agent dedicated to finding and investigating bad agent behavior.

---

**Enterprise verticalization: finance, legal, and proactive assistants**

Anthropic and Perplexity both pushed hard into finance workflows: Anthropic launched financial-services agent templates for pitch generation, valuation review, KYC screening, and month-end close, with integrations into FactSet, S&P Global, and Morningstar. Perplexity announced Perplexity Computer for Professional Finance with licensed data and 35 dedicated workflows for repeat analyst work. Both launches reflect a move from generic copilots to workflow-packaged vertical products.

Perplexity expanded into medical/professional health sources: Added premium access to NEJM, BMJ, and additional medical journals/databases for "deep and wide research" on trusted clinical sources.

Proactive assistant surfaces becoming a product category: @kimmonismus reported a leak around Anthropic Orbit, described as a proactive assistant that synthesizes data from Gmail, Slack, GitHub, Calendar, Drive, and Figma without explicit prompting. Manus added recommended connectors that are suggested in context when needed.

---

**Top tweets (by engagement)**

- Anthropic's finance template launch: @claudeai reached 22.9K engagement — one of the biggest clearly technical/AI-product posts in the set
- OpenAI's GPT-5.5 Instant launch: main rollout thread exceeded 8.2K engagement, follow-on personalization details also strong
- Gemma 4 speedups: @googledevs on 3× faster Gemma 4 and @googlegemma both broke through, reflecting strong interest in open-model inference improvements
- Perplexity's finance launch: @perplexity_ai reached 2.5K engagement

---

**AI Reddit Recap — /r/LocalLlama + /r/localLLM**

1. **Gemma 4 MTP released** (Activity: 1116): Google released MTP drafter checkpoints for Gemma 4 (gemma-4-31B-it-assistant, gemma-4-26B-A4B-it-assistant, gemma-4-E4B-it-assistant, gemma-4-E2B-it-assistant). MTP adds a smaller/faster draft model for speculative decoding — several draft tokens proposed, verified in parallel by target model. E2B drafter is only 78M parameters. Claims "up to 2x" decoding speedups while preserving identical output quality.

2. **llama.cpp MTP support in beta** (Activity: 1103): llama.cpp beta MTP support via PR #22673, initially targeting Qwen3.x MTP models. The PR loads the MTP component from the same GGUF with its own context/KV cache. Reported Qwen3.6 27B / 35B-A3B tests show ~75% steady-state acceptance with 3 draft tokens and usually >2× token-generation throughput over baseline. Community frames this as potentially one of the largest llama.cpp performance improvements to date, especially for dense models.

## Why It Matters

The dominant signal this week is that both major frontier labs — Anthropic and OpenAI — are moving simultaneously from model-only plays to model-plus-services, while the inference stack is undergoing its own bifurcation into commercial (RadixArk/SGLang) and proprietary (Mooncake/vLLM) distributed caching approaches.

---
[Source: AINews](https://www.latent.space/p/ainews-silicon-valley-gets-serious)
