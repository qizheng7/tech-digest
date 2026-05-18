---
title: "[AINews] The End of Finetuning"
date: 2026-05-13
source_url: https://www.latent.space/p/ainews-the-end-of-finetuning
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, genai-llm, ai-infra, ai-startup]
tags: [roundup, twitter-recap, community-signals, finetuning, OpenAI, SOOHAK, AI-Co-Mathematician, Mini-Shai-Hulud, supply-chain, GB200, Perplexity, Claude-Opus-4, Perceptron, Lighthouse-Attention, SOAP-Muon]
saved_at: 2026-05-17
---

## Top Stories

- **OpenAI finetuning API deprecation**: OpenAI deprecated its finetuning APIs, marking the "end of finetuning" for the modal 80% of AI engineers — though the top tier (Cursor, Cognition's $25B round) are increasing RLFT; finetuning may persist for custom ASIC/open-model deployments but "just very long prompts" increasingly dominate
- **SOOHAK benchmark**: 439 research-level math problems authored from scratch by 64 mathematicians (38 faculty), explicitly targeting capabilities above olympiad-style math; joins Medmarks v1.0 (30 benchmarks, 61 models) as part of the hard-eval push to retire saturated benchmarks
- **Google DeepMind AI Co-Mathematician**: Asynchronous, stateful research workbench for mathematicians; reaches 48% on FrontierMath Tier 4 while supporting ideation, literature discovery, computational analysis, theorem verification, and formal outputs
- **Mini Shai-Hulud supply-chain attack**: Campaign expanded beyond TanStack to OpenSearch, Mistral AI, Guardrails AI, UiPath across npm and PyPI; persists via hooks in Claude Code (.claude/settings.json) and VS Code (.vscode/tasks.json); Guardrails AI 0.10.1 quarantined within ~2 hours
- **GB200 Perplexity benchmarks**: NVLS all-reduce latency dropped 586µs→313µs vs H200; MoE prefill combine at EP=4 dropped 730µs→438µs; materially changes prefill/decode disaggregation for serving large MoEs like Qwen3 235B
- **Claude Opus 4.7 fast mode**: Reached APIs and Claude Code; Cursor reports 2.5× speed at 6× cost — new concrete point on the latency/price frontier
- **Perceptron Mk1**: Frontier video + embodied reasoning model; native video at up to 2 FPS, temporal grounding, multimodal in-context learning, structured spatial outputs (points, boxes, polygons, clips); 32k multimodal context; all inference on Modal
- **SOAP-Muon optimizer record**: Set new Modded-NanoGPT record at 3150 steps (-60); Lighthouse Attention from Nous is a training-time-only subquadratic wrapper removable near training end; Lean4-to-TileLang superoptimizer auto-discovers FlashAttention2 + 1.8× geomean speedup on A100s

## Community Signals (AI Twitter Recap)

Research Benchmarks, Hard Evals, and Agentic Science Systems

Research-level reasoning benchmarks keep getting harder: Soohak introduces 439 research-level math problems authored from scratch by 64 mathematicians (including 38 faculty), explicitly targeting capabilities above standard olympiad-style math. In medical evaluation, @SophontAI released Medmarks v1.0, expanding its open medical benchmark suite from 20→30 benchmarks and 46→61 models. There's also growing sentiment that old evals are saturating: @polynoamial argues benchmarks with uniformly high scores should be retired in favor of lower-scoring, frontier-challenging tests.

Agentic systems are starting to move benchmark frontiers in science and math: Google DeepMind's AI Co-Mathematician is described as an asynchronous, stateful research workbench for mathematicians, reportedly reaching 48% on FrontierMath Tier 4 while supporting ideation, literature discovery, computational analysis, theorem verification, and formal outputs. In theoretical physics, physics-intern boosts Gemini 3.1 Pro from 17.7% to 31.4% on CritPt via decomposition into specialized agents. On coding/program synthesis, ProgramBench's first task was reportedly solved by GPT-5.5 high/xhigh, with xhigh outperforming Opus 4.7 xhigh across metrics.

Retrieval and search benchmarks are rewarding small, specialized models: LightOn's Agent-ModernColBERT stacks another ~10% over Reason-ModernColBERT on BrowseComp-Plus while keeping the retriever at 149M parameters, with claims of matching or exceeding much larger model-based systems when paired with a generator. Related discussion from @xuzihuan4 asks whether lexical retrieval may suffice in agentic search loops when agents can iteratively refine their own queries.

Training, Optimization, and Scaling-Law Techniques

Optimizer work continues to compress training cost and improve small-scale experimentation: Several tweets centered on fast variants of SOAP/Muon-style updates. @torchcompiled applied tangent-step + Stiefel manifold retraction to SOAP basis updates, with follow-up discussion on drift checks and QR fallback for stability. In the Modded-NanoGPT community, SOAP-Muon set a new record at 3150 steps (-60), while an earlier MuLoCo-style outer Nesterov SGD wrap on NorMuonH also improved results, both backed by p-value reporting.

Formal methods and superoptimization are beginning to merge with ML systems work: @leloykun described a Lean4-to-TileLang tensor program superoptimizer that can automatically discover kernels such as FlashAttention2, FlashNorm, and split-k matmul, reporting roughly 1.8× geomean speedup on A100s. The same framework is positioned to jointly search over kernels, optimizers, hyperparameter transfer rules, and scaling laws.

Scaling laws and training metrics are being re-examined: @che_shr_cat argues the classic "20 tokens per parameter" framing is tokenizer-dependent and that scaling should be measured in bytes, not tokens. Separately, @JJitsev emphasized that prescriptive scaling laws are valuable not just for prediction, but as a systematic basis for comparing learning procedures across scales.

Training-time-only efficiency tricks are getting more interesting: Lighthouse Attention from Nous is highlighted as a subquadratic training wrapper around vanilla attention that can be removed near the end of training after a recovery phase, preserving standard deployment-time inference while reducing long-context pretraining cost. In a similar spirit, Renderers from Prime Intellect addresses the token/message impedance mismatch between RL trainers and agent environments, claiming >3× throughput on popular open models.

Inference Systems, Serving Stacks, and Runtime Infrastructure

Blackwell racks are emerging as the reference platform for large-MoE serving: Perplexity published details on serving post-trained Qwen3 235B on NVIDIA GB200 NVL72 systems, arguing GB200 is a major inference step up over Hopper for large MoEs. Their benchmarks cite NVLS all-reduce latency dropping from 586.1µs on H200 to 313.3µs on GB200, and MoE prefill combine at EP=4 dropping from 730.1µs to 438.5µs, with better decode throughput at high token rates. @AravSrinivas framed this as materially changing prefill/decode disaggregation for serving large MoEs.

Inference orchestration is increasingly specialized, not "just Kubernetes": Modal argues inference needs a dedicated stack, citing work on compute management, cloud-native caching, CRIU, and GPU checkpointing. That positioning got an immediate real-world endorsement from Perceptron, which said all Mk1 inference runs on Modal because native video, structured outputs, and hybrid reasoning create unusual cold-start and scaling requirements.

OSS inference economics continue to improve fast: SemiAnalysis reported that clustering multiple B200 8-GPU machines over RoCEv2 CX-7 with PD disaggregation can lift per-GPU token throughput by up to 7×, implying comparable cost-per-token reductions. On the vector DB side, Qdrant 1.18 added TurboQuant, claiming recall near scalar quantization with 2× less memory, alongside memory monitoring and named-vector lifecycle operations.

Agent runtimes are becoming version-control-like substrates: A standout systems idea was Stanford's Shepherd, summarized by @ai_satoru_chan, which treats agent execution more like Git: first-class tasks, effects, scopes, and traces; exact replay; branching; rollback; and formal guarantees in Lean. Claimed results include live-supervision gains on CooperBench from 28.8%→54.7%, plus faster counterfactual optimization and tree-RL rollouts.

Product and Model Releases: Multimodal, Video, Retrieval, and Embeddings

Perceptron Mk1 was the most substantive new model release in the set: @perceptroninc launched Perceptron Mk1 as a model for frontier video and embodied reasoning, with native video support at up to 2 FPS, temporal grounding, multimodal in-context learning, and structured spatial outputs. OpenRouter's summary notes a 32k multimodal context and first-class outputs like points, boxes, polygons, and clips. The release is framed less as a generic VLM and more as a physical-world reasoning stack.

Google and Meta both pushed multimodal interaction layers rather than standalone model specs: Google DeepMind's AI-enabled mouse pointer demos reimagine the cursor as a contextual pointing interface tied to Gemini, allowing users to point at on-screen content and speak shorthand instructions. In parallel, Meta announced Meta AI voice conversations powered by Muse Spark, adding interruption, language switching, image generation, and live camera-grounded interaction.

Embedding and retrieval model updates were notable: Jina released jina-embeddings-v5-omni, a universal embedding model for text, images, audio, and video, in 1.57B and 0.95B variants, both with Matryoshka truncation and backward compatibility with existing v5-text indexes. Meta quietly released Sapiens2, a family of human-centric high-resolution ViTs spanning 0.1B→5B params for pose estimation, segmentation, normals, and pointmaps.

Diffusion and image tooling kept moving: Hugging Face's Diffusers 0.38.0 added new pipelines including Ace-Step 1.5, LongCat-AudioDiT, and Ernie-Image, plus support for Flash Attention 4, FlashPack loading, and Ring Anything for context parallelism. Other research releases included ELF: Embedded Language Flows, a continuous-space text diffusion model, and Tencent's Pixal3D for pixel-aligned 3D generation.

Agents, Tooling, and Developer Workflow

Agent products are shifting from demos to operational platforms: OpenAI teased Symphony as a system where every open task gets a running Codex agent, and separately highlighted computer use for Codex to work across apps without full takeover. LangChain re-open-sourced its revamped Chat LangChain app, describing it as a production Q&A agent handling nearly 2T tokens/week.

Long-running-agent state management is becoming a first-class systems problem: LangGraph's new DeltaChannel snapshots aim to replace full-state checkpointing for scalable durable execution; LangChain says the same mechanism now powers message histories and file storage in deepagents v0.6. The broader pattern also shows up in Google's Gemini Interactions API guide, where encrypted thought signatures preserve reasoning context across turns in both stateful and stateless modes without forcing developers to manage signature injection manually.

Synthetic data and RL environment generation are being operationalized: @Vtrivedy10 offered a useful practitioner perspective: targeted synthetic data extraction from model weights is hard at scale, especially for underrepresented distributions like long sequences, and effective pipelines need programmatic tests, verifiers, judges, and agentic long-horizon framing. On the infrastructure side, Tau2-Infinity formalizes autonomous mining of hard tool-use tasks for RL post-training via DAG walks or world-generation from failure hypotheses.

Top tweets (by engagement, filtered for technical relevance)

Gemini as an OS-level intelligence layer: Google's Gemini Intelligence, Googlebook, and AI pointer demos collectively point to agentic UX moving from chat windows into the operating system.

Isomorphic Labs funding: @demishassabis announced $2.1B in new funding for AI-driven drug discovery, one of the largest capital commitments in this dataset tied directly to an applied AI platform.

Speech-to-speech benchmarking: Artificial Analysis' τ-Voice benchmark found even the best S2S models solve only about half of realistic customer service scenarios, with Grok Voice Think Fast 1.0 leading at 52.1%.

Claude Opus 4.7 fast mode: Anthropic's fast mode release reached APIs and Claude Code, with Cursor noting 2.5× speed at 6× cost — a concrete new point on the latency/price frontier.

Security, Supply Chain, and Safer Coding

The most urgent operational story was the Mini Shai-Hulud supply-chain attack: @IntCyberDigest reported the campaign had expanded beyond TanStack to hit OpenSearch, Mistral AI, Guardrails AI, UiPath, and others across npm and PyPI, specifically targeting AI developer tooling. The noteworthy technical detail is persistence: it allegedly hooks into Claude Code (.claude/settings.json) and VS Code (.vscode/tasks.json) so the compromise can re-execute on future tool events even after package removal. Guardrails AI later confirmed its 0.10.1 package was compromised and quarantined within about 2 hours.

Actionable mitigations surfaced quickly: @ramimacisabird noted that beyond minimumReleaseAge, teams should enable blockExoticSubdeps to prevent remote GitHub references from slipping into dependency graphs. @elithrar reiterated that GitHub's pull_request_target remains one of the sharpest CI/CD footguns for fork-based PR automation. And at the workstation level, @andersonbcdefg recommended moving secrets out of ubiquitous local .env files into a proper secrets manager.

Safer codegen is becoming its own research track: Stanford-aligned work on SecureForge targets vulnerability discovery/prevention in LLM-generated code via prompt optimization, while the corresponding paper frames it as a bridge between codegen and security evaluation. The broader point: coding agents are now strong enough that supply-chain hardening and secure-generation evaluation need to be treated as core infra, not side concerns.

## Why It Matters

OpenAI's finetuning API deprecation is the symbolic end of a development-phase bet that most AI engineers never needed to win — the real frontier is moving toward RL-trained specialized models, very long prompts, and agent harnesses, with supply-chain security (Mini Shai-Hulud) now a practical concern for anyone using AI dev tooling.

---
[Source: AINews](https://www.latent.space/p/ainews-the-end-of-finetuning)
