---
title: "[AINews] The Inference Inflection"
date: 2026-04-29
source_url: https://www.latent.space/p/ainews-the-inference-inflection
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra]
tags: [roundup, twitter-recap, community-signals, inference, Codex, Cursor-SDK, Mistral, vLLM, Blackwell]
saved_at: 2026-04-29
---

## Top Stories

- **The Inference Inflection op-ed:** swyx frames Jensen Huang's GTC claim ("inference compute has gone up 10,000× in 2 years, usage 100×, demand 1,000,000×") alongside Noam Brown ("inference compute is undervalued") and Sam Altman ("we have to become an AI inference company now") as a coordinated signal — inference is the strategic resource of this era, and CPU demand is also surging (Intel CEO: CPU refresh cycle delayed 2yr by GPU budget prioritization, RL gyms and Claude Code workloads are CPU-heavy)
- **Codex becomes a platform:** OpenAI expanded Codex beyond coding to research synthesis, spreadsheets, and decision tracking; launched Codex-only seats at $0 seat fee for Business/Enterprise through June; WebSocket mode on Responses API yields 40% faster agentic workflows
- **Cursor SDK launches:** Exposes Cursor's runtime, harness, and models for CI/CD, automations, and embedded agents — shifts Cursor from seat-based IDE to programmable agent infrastructure
- **Mistral Medium 3.5 released:** Dense 128B model; vision reasoning; runs locally on ~64GB RAM; community split on whether its 128K context and pricing can compete with large Chinese open MoEs
- **IBM Granite 4.1:** Three new open-weight Apache 2.0 models (30B/8B/3B), non-reasoning; Granite 4.1 8B used only 4M output tokens on AA Intelligence Index vs 78M for Qwen3.5 9B — aimed at enterprise edge where cost/transparency > benchmarks
- **Qwen FlashQLA:** High-performance linear attention kernels on TileLang; 2–3× forward and 2× backward speedups for long-context workloads; gate-driven automatic intra-card CP, fused warp-specialized kernels

## Community Signals (AI Twitter Recap)

**Coding Agents Become Platforms: Codex, Cursor SDK, and VS Code Harness Upgrades**

OpenAI is turning Codex from a coding tool into a general work surface: the strongest product signal today was not just usage enthusiasm, but the steady expansion of capabilities around persistent context, tools, integrations, and team rollout. OpenAI highlighted Codex for broader knowledge-work tasks like research synthesis, spreadsheets, and decision tracking in addition to code; launched Codex-only seats with $0 seat fee for eligible Business/Enterprise customers through end of June; and added integrations like Supabase and a Figma plugin that turns implementation plans into FigJam boards.

Performance work is shifting from model latency to agent-loop systems engineering: OpenAI said moving Codex-style workflows to WebSocket mode on the Responses API keeps state warm across tool calls and cuts repeated work, yielding up to 40% faster agentic workflows. VS Code shipped a parallel stack of harness improvements: semantic indexing across workspaces, cross-repo search, chat session insights, skill context, remote control for Copilot CLI, and a prompt/agent evaluation extension aimed at refining prompts, skills, and instructions. The throughline is that coding-agent UX is now dominated by memory, retrieval, harness quality, and tool orchestration—not just raw model intelligence.

Cursor is making an explicit platform play: the new Cursor SDK exposes the same runtime, harness, and models that power Cursor for use in CI/CD, automations, and embedded agents inside products. This is notable because it shifts Cursor from seat-based IDE product toward programmable agent infrastructure. Taken together with Codex app-server and VS Code harness work, the category is clearly converging on headless agent runtimes + programmable harnesses + usage-based economics.

**Agent Harness Engineering, LangGraph/Deep Agents, and Production AgentOps**

Harnesses are emerging as a first-class optimization layer: multiple posts converged on the idea that model quality alone is insufficient; the harness around the model often determines production performance. The clearest research example was Agentic Harness Engineering, which makes harness evolution observable via revertible components, condensed execution evidence, and falsifiable predictions. Reported gains: Terminal-Bench 2 pass@1 from 69.7% to 77.0% in ten iterations, beating a human-designed Codex-CLI baseline at 71.9%, while also transferring across model families and reducing token use on SWE-bench Verified by 12%. Related work on HALO describes recursively self-improving agents using trace analysis to patch harness failures, claiming AppWorld improvement from 73.7 to 89.5 on Sonnet 4.6.

LangChain's Deep Agents product line is leaning into model-specific harness tuning and deployability: new Harness Profiles let teams version per-model prompts, tools, and middleware, with built-in profiles for OpenAI, Anthropic, and Google models. LangChain also pushed DeepAgents Deploy, a low-code deployment path using a small set of markdown/config files and LangSmith-backed tracing. The broader message from LangChain staff was consistent: open harnesses, open evals, and OSS-friendly model mixes matter because closed models are becoming too expensive for many agent workloads.

Cloudflare continued to flesh out its "agents as software" stack with ideas like execution ladders and, more concretely, making agents able to become Cloudflare customers—create accounts, register domains, start paid plans, and get tokens for deployment. This is a meaningful sign that vendors are starting to expose business workflows directly to agents rather than treating them as passive copilots.

**Model Releases and Benchmarks: Mistral Medium 3.5, Granite 4.1, Ling-2.6, and Open-Model Price Pressure**

Mistral Medium 3.5 was the day's most debated model release. Early commentary pegged it as a dense 128B model, with Unsloth describing it as a vision reasoning model that can run locally on roughly 64GB RAM and publishing GGUFs/guidance. Reaction split sharply: some criticized its 128K context, architecture choices, and pricing versus large Chinese open MoEs, while others argued Mistral is making a deliberate enterprise reliability/instruction-following bet rather than chasing raw benchmark spectacle.

IBM Granite 4.1 added three new open-weight, Apache 2.0 non-reasoning models—30B, 8B, 3B—with a strong emphasis on openness and token efficiency. The standout claim is that Granite 4.1 8B used only 4M output tokens on the Artificial Analysis Intelligence Index, versus 78M for Qwen3.5 9B, while scoring 61 on the AA Openness Index. Intelligence lags stronger peers, but the family looks aimed squarely at enterprise/edge deployments where cost and transparency matter more than leaderboard position.

Open-weight competitive pressure continues to intensify: Ant OSS's Ling-2.6-flash was cited as ~107B MoE, MIT-licensed, with 61.2 SWE-bench Verified and strong math scores; Ling-2.6-1T also landed with day-0 vLLM support. Meanwhile, Tencent Hunyuan open-sourced Hy-MT1.5-1.8B-1.25bit, a 440MB, fully offline translation model for phones covering 33 languages, 1,056 translation directions, and claiming parity with commercial APIs via aggressive 1.25-bit quantization. On the market side, multiple posts underscored how rapidly pricing is falling for capable open models, e.g. Qwen 3.5 Plus at $3/M output tokens and MiMo-V2.5 Pro shifting the Pareto frontier in Code Arena at $1/$3 per M tokens.

**Inference, Kernels, and MoE Systems: FlashQLA, vLLM on Blackwell, torch.compile, and GLM-5 Serving**

Qwen's FlashQLA is a notable long-context kernel release: Alibaba introduced FlashQLA, high-performance linear attention kernels on TileLang, reporting 2–3× forward and 2× backward speedups, especially for small models, long-context workloads, and tensor-parallel setups. The design centers on gate-driven automatic intra-card CP, algebraic reformulation, and fused warp-specialized kernels. It is explicitly positioned for agentic AI on personal devices, which fits a broader trend of long-context optimization migrating from cloud-only infra to edge-friendly runtimes.

vLLM and Blackwell co-design is landing real throughput wins: vLLM reported #1 output speed on Artificial Analysis for DeepSeek V3.2 at 230 tok/s, 0.96s TTFT and also strong results on Qwen 3.5 397B using DigitalOcean serverless inference on NVIDIA HGX B300, with optimizations including NVFP4 quantization, EAGLE3 + MTP speculative decoding, and per-model kernel fusion. SemiAnalysis separately highlighted gains from vLLM 0.20.0 and MegaMoE kernels for DeepSeek v4 Pro on GB200.

More engineers are sharing the "middle layer" details between models and GPUs: a useful thread on torch.compile broke down Dynamo → pre-grad → AOT autograd → post-grad → Inductor, including where to inject custom FX passes for inference optimizations. John Carmack posted a reminder that GPU library performance remains extremely path-dependent and notchy, noting a 10× regression in torch.linalg.solve_ex when going from 511×511 to 512×512, apparently due to a different internal path with CudaMalloc/Free. Zhipu AI also published a good serving postmortem on GLM-5, detailing KV cache race conditions, HiCache synchronization bugs, and LayerSplit, which reportedly improved prefill throughput by up to 132% for long-context coding-agent serving.

**Research Signals: Knowledge Probes, Web-Agent Benchmarks, Multimodal/Science Infrastructure**

Incompressible Knowledge Probes (IKP) is one of the more provocative research threads: @bojie_li claims that factual knowledge accuracy over 1,400 questions / 188 models / 27 vendors gives a strong log-linear signal of model size (R² = 0.917 on open-weight models from 135M to 1.6T params). The paper argues factual capacity does not compress over time the way some "reasoning compresses" narratives suggest, and uses the fitted curve to estimate closed-model sizes. Whether one buys the estimates or not, the work is valuable as a reminder that black-box evals still leak architecture-scale information.

## Why It Matters

The "inference inflection" framing — CPU and GPU demand both surging together, coding agents becoming programmable platforms, and open-weight models compressing the price floor — signals that AI has moved from the research phase into an infrastructure and economics phase where distribution, harness quality, and cost efficiency determine who wins.

---
[Source: AINews](https://www.latent.space/p/ainews-the-inference-inflection)
