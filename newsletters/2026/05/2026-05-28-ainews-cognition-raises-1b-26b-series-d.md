---
title: "[AINews] Cognition Raises $1B in $26B Series D"
date: 2026-05-28
source_url: https://www.latent.space/p/ainews-cognition-raises-1b-in-26b
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-startup, ai-infra]
tags: [roundup, twitter-recap, community-signals, Cognition, Devin, funding, inference-efficiency, ESMFold2, continual-learning, vLLM-Rust, DeepSWE]
saved_at: 2026-06-01
---

## Top Stories

- Cognition ($26B Series D, $1B raised, $492M ARR run-rate, enterprise usage up 10x YTD) — now the largest remaining independent agent lab; valuation up 2.5x in 8 months from $10B Series C
- ESMFold2 released by BioHub's Alex Rives: open protein structure prediction engine, atlas of 6.8B proteins + 1.1B predicted structures, SOTA on antibodies; "Bitter Lesson is coming for proteins"
- DeepSeek V4-Pro's hybrid attention (Compressed Sparse Attention + Heavily Compressed Attention) brings 1M-token KV cache to ~10% of V3.2 and single-token inference FLOPs to 27% — price cuts are structurally justified
- vLLM merged a Rust frontend as drop-in alternative to the Python API server: ~837 req/s vs ~162 req/s on preprocess-heavy workload in a single process
- EAGLE 3.1 improves speculative decoding robustness for long-context serving; Perplexity open-sourced a Unigram tokenizer cutting CPU utilization 5-6x (63 µs at 514 tokens, zero heap allocations)
- Trajectory launched with $15M funding: platform for continuous post-training of agentic models using product usage signals and agent traces; design partners include Clay, Harvey, Decagon

## Community Signals (AI Twitter Recap)

Inference Efficiency, Serving Architectures, and Cost Curves
Inference optimization is increasingly architectural, not just kernel-level: EAGLE 3.1 improves speculative decoding robustness by stabilizing hidden-state feedback and reducing attention drift at deeper decode steps, with explicit emphasis on long-context acceptance length and real-world serving reliability; the team also highlighted collaboration with vLLM and TorchSpec. At the kernel/system layer, Perplexity open-sourced a rebuilt Unigram tokenizer that cuts CPU utilization 5–6× and reaches 63 µs at 514 tokens with zero heap allocations, while Qwen3.5 on TokenSpeed reportedly hits 580 tokens/s for agentic workloads via joint optimization across Alibaba, LightSeek, NVIDIA, Mooncake, and FlashAttention-4 contributors. Supporting libraries also improved: MaxSim v2 adds backprop and reports 10.33× faster on H200 and 11.94× on A100 versus naïve PyTorch.
Price cuts are being justified by structural KV-cache and attention changes: @kimmonismus summarized how DeepSeek V4-Pro uses hybrid attention with Compressed Sparse Attention and Heavily Compressed Attention to bring 1M-token KV cache to ~10% of V3.2 and single-token inference FLOPs to 27%, while still routing 49B active params out of 1.6T total. Xiaomi's MiMo similarly reduces cache traffic using SWA plus hierarchical cache management. The broader takeaway: long-context inference economics are now being pushed by attention design + cache hierarchy + routing, not just cheaper hardware.

Agents, Harnesses, Memory, and Continual Learning
The stack is shifting from "model quality" to "model-harness-memory fit": A substantial cluster of tweets focused on practical agent engineering. LangChain shipped Deep Agents v0.6 with Delta Channels, cutting checkpoint storage for a 200-turn coding session from 5.3 GB to 129 MB, and also launched computer use in Fleet, plus Context Hub for versioned agent context/skills. LangSmith Engine was framed as automating the eval → diagnosis → fix loop, with multiple practitioners emphasizing its value for turning trace feedback into reusable online/offline evaluators. @Vtrivedy10 made the clearest formulation of the day: task-harness fit matters as much as model quality, and bespoke vertical systems outperform generic harnesses by narrowing tools, prompts, and context to the task.
Continual learning is re-emerging as a product category, not just a research topic: The biggest announcement here was Trajectory's launch: a platform for using product usage signals and agent traces to continuously post-train large agentic models, with $15M in funding and design partners including Clay, Harvey, Decagon, Mercor, and Rogo. Baseten said it supports these deployments with FP8/NVFP4 quantization and autoscaled H100 infra, including a cited overnight deployment of a 397B-parameter model.

Benchmarks, Scaling Laws, and Training Methods
New benchmarks are increasingly about long-horizon, messy, real-world workflows: DeepSWE was highlighted as a SWE/agent benchmark with 113 tasks across 91 repos in 5 languages, using a minimalist bash-only harness — @theo called it "the first code bench that actually aligns with how it feels to use these models coding." Artificial Analysis and IBM launched ITBench-AA, an SRE benchmark over Kubernetes incident response where all frontier models scored below 50%; Claude Opus 4.7 led at 47%, GPT-5.5 followed at 46%, GLM-5.1 Reasoning led open weights at 40%.
Training efficiency: Sakana AI's DiffusionBlocks reinterprets forward passes as diffusion-like denoising steps so deep nets can be trained one block at a time, dramatically reducing memory while matching end-to-end performance. Snowflake introduced ZoRRo, claiming up to 3.5× faster long-context RL and 3.2× longer context windows by eliminating redundant rollout computation.

Model and Modality Releases: Biology, Vision, OCR, and Embedded AI
Protein modeling had a standout day: ESMFold2 was announced as an open scientific engine for protein structure prediction and design, with strong reported results on protein interactions and antibodies, plus an accompanying atlas of 6.8B proteins and 1.1B predicted structures. The release emphasized both practical design outcomes — miniprotein binders and single-chain antibodies across five therapeutic targets — and mechanistic interpretability findings about emergent protein representations. @cgeorgiaw noted the atlas exceeds AlphaFold DB in scale.
A wave of smaller but practical multimodal/open releases landed: Google DeepMind shared the white paper for Gemini Embedding 2, described as a native multimodal embedding model supporting unified representations over text, image, audio, and video. NVIDIA's LocateAnything combines Qwen2.5-3B + Moon-ViT for high-speed grounding, with a claimed 10× speedup for dense object detection. Surya OCR 2 ships as a 650M model with 83.3% OLMOCR bench and 5 pages/s on RTX 5090.

Developer Platforms, Enterprise Controls, and Coding-Agent Productization
Coding agents are consolidating into full product stacks with enterprise controls: OpenAI continued tightening Codex's product surface: GPT-5.2 and GPT-5.3-Codex being sunset in favor of GPT-5.5, while enterprise features now include private MCP connectivity over outbound-only HTTPS, Workload Identity Federation, and expanded Admin API controls for spend alerts, allowlists, retention policies, and hosted tool management.
The biggest commercial datapoint was Cognition: >$1B raised at a $26B valuation, enterprise usage up >10× YTD, and $492M run-rate revenue, paired with a growing customer list and strong endorsements from users like Exa. The biggest technical signal: vLLM merged a Rust frontend as a drop-in alternative to the Python API server, with early numbers showing ~837 req/s vs ~162 req/s on a preprocess-heavy workload in a single process. OpenRouter announced a $113M Series B and said weekly volume grew from 5T to 25T tokens over six months.

Top tweets (by engagement)
- Cognition's scale-up: Cognition announced >$1B raised, $26B valuation, and $492M run-rate revenue, one of the clearest signals yet that coding agents are converting into large enterprise businesses
- Claude Code reliability push: Anthropic's ClaudeDevs posted a high-engagement update on responsiveness, reliability, and better feedback collection
- Sakana AI's DiffusionBlocks: @hardmaru drew major attention to block-wise training that can match end-to-end performance while dramatically lowering memory requirements
- ESMFold2 release: @alexrives announced one of the day's most substantive science releases — open protein modeling at atlas scale with therapeutic design implications
- OpenAI enterprise controls + MCP: @OpenAIDevs on private MCP and related admin/security updates
- vLLM Rust frontend: @vllm_project's merge announcement mattered for anyone hitting CPU/API-server bottlenecks in high-throughput serving

## Why It Matters

Cognition's $26B valuation with $492M ARR makes coding agents no longer a research bet but a proven enterprise category, while the convergence of better benchmarks (DeepSWE), continual learning platforms (Trajectory), and Rust-speed serving (vLLM) signals the stack is maturing from model-racing to systems-engineering.

---
[Source: AINews](https://www.latent.space/p/ainews-cognition-raises-1b-in-26b)
