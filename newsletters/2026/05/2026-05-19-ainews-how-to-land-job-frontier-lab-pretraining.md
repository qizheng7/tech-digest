---
title: "[AINews] How to land a job at a frontier lab (on Pretraining)"
date: 2026-05-19
source_url: https://www.latent.space/p/ainews-how-to-land-a-job-at-a-frontier
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [roundup, twitter-recap, Cursor, Composer-2.5, SpaceXAI, Qwen3.7, Anthropic, Stainless, SDK, MCP, llama.cpp, MTP, ByteDance, Lance, multimodal, RL, MoE, agent-eval, LangSmith, Devin, coding-agents, pretraining, kernel-dev]
saved_at: 2026-05-19
---

## Top Stories

- **Cursor Composer 2.5 + SpaceXAI**: Cursor released Composer 2.5 (Kimi K2.5 base, 25× more RL training, matches Opus 4.7/GPT-5.5 at 1/10 cost) and disclosed training a much larger model with SpaceXAI using Colossus 2's ~1M H100-equivalents and 10× more compute
- **Vlad Feinberg on landing a frontier lab job**: Google/TPU-centric guide focused on pretraining — kernel work is the most direct path; hire test: derive Chinchilla laws for dense vs MoE, write a Pallas kernel that beats jax.lax.ragged_dot for F > D
- **Qwen3.7 Preview on Chatbot Arena**: Qwen3.7 Max Preview reaches #13 overall in text (#7 Math, #9 Expert, #10 Coding); Alibaba now ranked #6 lab in text and #5 in vision
- **Anthropic acquires Stainless**: SDK and MCP server platform that has generated all official Anthropic SDKs; signals vertical integration around developer ergonomics and agent connectivity
- **ByteDance open-sources Lance**: Unified multimodal model for image/video understanding, generation, and editing — 3B video + 3B image + 3B decoder components
- **llama.cpp MTP support for Qwen3.6**: Georgi Gerganov ships multi-token prediction for Qwen3.6; community reports 78% throughput gain (25 → 45 tok/s) on Qwen3.6-27B dense on A10G

## Community Signals (AI Twitter Recap)

Coding Agents, Agent Ops, and the Move from Chat to Automation
Agent infrastructure is converging on observability + automation loops: Several posts point to a maturing stack for production agents. LangSmith Engine is framed as the missing CI/CD loop for agents, automatically detecting failures from production traces, clustering issues, and drafting fixes/evals, with LangChain also highlighting SmithDB as a purpose-built data layer for agent observability/eval workloads with low-latency querying over large traces and self-hosting/multi-cloud requirements @krishdpi, @LangChain. In parallel, Cognition launched Devin Auto-Triage, positioning it as an always-on "first responder" for bugs, alerts, and incidents with long-term memory, manager/subagent structure, and PR generation; early users like Modal describe it as more useful than typical homegrown triage automations @cognition, @walden_yan, @russelljkaplan. The common pattern is less "chat with an agent" and more persistent automation tied to traces, memory, and evals.

Operational patterns for coding agents are getting more concrete: Anthropic published best practices for running Claude Code across multi-million-line monorepos, legacy systems, and microservices, while adding prompt cache diagnostics and making Fast mode default to Opus 4.7 for lower-latency coding workflows @ClaudeDevs. OpenAI expanded Codex workflows with a Zoom plugin, mobile/desktop remote execution, and "keep your Mac awake" support so longer-running jobs continue from the phone app @coreyching, @OpenAIDevs. Microsoft pushed remote control for GitHub Copilot CLI and VS Code to GA @code. Across these, the product direction is clear: background execution, remote supervision, and agent fan-out, not just interactive completions.

Practitioners are converging on the same mental model: constrain, verify, decompose: François Chollet's framing of coding agents as "blind squirrels" that need carefully placed verifiable constraints succinctly matches a broader shift toward harness-centric engineering @fchollet. Related advice includes using asserts heavily in Python/ML code to fail fast @gabriberton, building both end-to-end and incremental evals for long-running agents @palashshah, and structuring multi-agent systems in staged maturity levels rather than maximizing agent count prematurely @shannholmberg. The practical consensus: agent quality depends more on verification surfaces, decomposition, and feedback loops than on prompt cleverness alone.

Model Releases, Ranking Shifts, and Frontier Coding Models
Cursor's Composer 2.5 is the standout model launch in this batch: Cursor announced Composer 2.5 as its strongest model yet, emphasizing better sustained work on long-running tasks and more reliable instruction following, then disclosed a deeper strategic move: training a much larger model from scratch with "SpaceXAI," using 10× more total compute and access to Colossus 2's million H100-equivalents @cursor_ai. Community reactions centered on its efficiency/cost-performance profile and strong coding quality, with users calling it a major step up from Composer 2 and noting better collaboration behavior in messages/updates, not just raw benchmark gains @mntruell, @jonas_nelle, @kimmonismus.

Alibaba's Qwen line continues to climb: Qwen3.7 Preview landed on Arena with Qwen3.7 Max Preview at #13 overall in text, including #7 Math, #9 Expert, #9 Software & IT, and #10 Coding; Qwen3.7 Plus Preview reached #16 overall in vision, making Alibaba the #6 lab in text and #5 in vision by Arena's counts @arena, @Alibaba_Qwen. That reinforces the broader trend of Chinese labs steadily improving across both general and specialist arenas rather than only headline chat benchmarks.

Open model and multimodal releases continue below the mega-frontier: ByteDance open-sourced Lance, described as a unified multimodal model for image/video understanding, generation, and editing, with 3B video + 3B image + 3B decoder components @bdsqlsz. Perplexity released a small open multilingual ColBERT model as a continued-training variant of pplx-embed-0.6b, with notes on using the MaxSim kernel @bo_wangbo. These are not frontier-scale launches, but they are technically meaningful because they target retrieval quality and native multimodal unification, two areas where open tooling still matters.

Inference, Deployment, and Local/Enterprise Serving
Local inference got a notable speed boost via MTP in llama.cpp: Georgi Gerganov announced MTP support for the Qwen3.6 family in llama.cpp, calling it a significant milestone for local AI @ggerganov. Follow-on reports showed meaningful throughput gains, including a Qwen3.6-27B dense jump from 25 tok/s to 45 tok/s (+78%) on an A10G using draft-MTP flags @victormustar. This matters because it narrows the usability gap between local and hosted coding/general assistants on commodity hardware.

Enterprise/on-prem deployment momentum remains strong: Hugging Face and Dell promoted one-click access to models including Kimi K2.6, DeepSeek V4 Pro/Flash, GLM 5.1, and MiniMax M2.7 through Dell Enterprise Hub optimized for PowerEdge XE9780 with NVIDIA B300 @jeffboudier. Clement Delangue argued that on-prem/local AI based on open-source models will be an important answer to GPU shortages, with advantages in cost, latency, and safety/data control @ClementDelangue.

Cross-hardware inference optimization is becoming more sophisticated: Zyphra published end-to-end inference benchmarks on AMD Instinct MI355X, claiming strong outperformance over AMD's baseline and a narrowed gap to NVIDIA B200 when serving Kimi K2.6, GLM 5.1, and DeepSeek V3.2 @ZyphraAI. Complementing that, Quentin Anthony posted a useful thread on why benchmarking needs to distinguish hardware ceilings vs current software state, arguing that many cross-stack comparisons conflate vendor maxes, achievable GEMM performance, and software maturity @QuentinAnthon15.

Research: MoEs, RL/Data Mixing, Architecture Search, and Agent Evaluation
Several papers this week focused on better training signals rather than bigger models: A summary of LeCun/Timor et al.'s "On Training in Imagination" highlighted that in model-based RL, smoother world/reward models with low Lipschitz constants tighten error bounds; reward models often scale faster than dynamics models; and many noisy reward labels can beat fewer high-quality ones, while biased rewards are especially dangerous @TheTuringPost. A separate thread on Pedagogical RL argued that even correct reasoning traces can be poor training data if they are too surprising relative to the student policy; the method uses a privileged teacher plus spike-aware rewards and surprisal-gated imitation to generate trajectories the student can actually learn from @blc_16, @NoahZiems.

Architecture and scaling studies remain highly actionable: Meta's AIRA work on agentic neural architecture discovery drew attention because it beats Llama 3.2 at 350M, 1B, and 3B scales within a 24-hour compute budget by splitting search into a planning agent (AIRA-Compose) and an implementation agent (AIRA-Design) @omarsar0, @dair_ai. Separately, "Slicing and Dicing MoEs" reports training 2,000+ MoE LMs and concludes that much of the design space reduces to expert size and expert count rather than the noisier discourse around MoE configuration knobs @margs_li.

Data selection/eval methodology are emerging as first-class research problems: On-Policy Mix targets the unsolved problem of finding the right data mix as data distributions keep shifting, with applicability across pretraining, midtraining, and instruction tuning @michahu8. On evals, Cameron Wolfe published a guide to agent evaluation, and a longer Zhihu summary argued that the agent era requires measuring delegation intelligence—when to search, code, reason, or call tools—rather than only static knowledge or internal chain-of-thought prowess @cwolferesearch, @ZhihuFrontier.

Ecosystem Moves: SDKs, Revenue Capture, and Open Tooling
Anthropic acquired Stainless: Anthropic announced the acquisition of Stainless, the SDK and MCP server platform that has powered Anthropic SDKs since early API days @AnthropicAI. Strategically, this points to continued vertical integration around developer ergonomics, SDK generation, and protocol surfaces, not just model quality.

Revenue concentration around foundation model providers appears to be increasing: One post claimed that Anthropic and OpenAI's share of AI model/application revenues generated by 34 top AI startups is rising, a signal that the ecosystem may be consolidating economically even as model choices proliferate @amir.

Tooling and deployment curation remains in demand: The Turing Post's roundup of 13 open-source tools for foundation model deployment—including vLLM, TGI, SGLang, llama.cpp, Ollama, BentoML, Kubeflow, MLflow and others—was one of the more practically useful curation posts in the set @TheTuringPost. Meanwhile, Papers With Code is being revived with AI-agent-assisted parsing of methods, leaderboards, and SOTA tracking, underscoring renewed focus on research discoverability @NielsRogge.

Top Tweets (by engagement)
Cursor's Composer 2.5 + bigger training push: The highest-signal high-engagement product news was Composer 2.5 and Cursor's disclosure that it is training a much larger model from scratch with 10× more compute @cursor_ai.

OpenAI/Anthropic product updates with developer impact: Sam Altman said ChatGPT improved significantly with the latest update @sama, while Anthropic shipped Fast mode defaulting to Opus 4.7 and prompt cache diagnostics in Claude Console @ClaudeDevs.

Enduring research/engineering framing: Richard Sutton's 26-word condensation of the Bitter Lesson—focus on methods for creating knowledge that scale with compute, like search and learning—was among the most engaged research-adjacent posts and resonated with many of the week's themes around agent harnesses, search, and verifier-driven systems @RichardSSutton.

## Why It Matters

The week's dominant signal is the maturation of coding-agent infrastructure: observability loops, harness design, and background execution are converging into production patterns, while Cursor's Composer 2.5 launch (and Colossus 2 training reveal) marks the first IDE company making a credible vertical play on the frontier model stack.

---
[Source: AINews](https://www.latent.space/p/ainews-how-to-land-a-job-at-a-frontier)
