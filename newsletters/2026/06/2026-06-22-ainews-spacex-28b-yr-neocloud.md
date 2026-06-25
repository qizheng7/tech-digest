---
title: "[AINews] SpaceX is already a $28B/yr Neocloud"
date: 2026-06-23
source_url: https://www.latent.space/p/ainews-spacex-is-already-a-28byr
source: AINews
type: newsletter
newsletter: AINews
topics: [newsletter, ai-infra, ai-startup, genai-llm]
tags: [roundup, twitter-recap, SpaceX, neocloud, Baseten, GLM-5.2, OpenAI, Daybreak, Sakana, Fugu, Gemini-Interactions-API, Hermes]
saved_at: 2026-06-25
---

## Top Stories

- SpaceX signed its third GPU rental deal (Reflection AI, $6.3B for GB300 access), combining with Anthropic and Google deals to reach ~$28B/yr in compute leasing — twice CoreWeave's current revenue
- Baseten announced its $13B Series F, betting enterprises want to own their intelligence layer via open models and post-training on proprietary data
- OpenAI expanded Daybreak cybersecurity program: Codex Security plugin, GPT-5.5-Cyber model for trusted defenders, Cyber Partner Program, "Patch the Planet" OSS security; 30M+ commits scanned, 30K+ codebases covered
- GLM-5.2 emerged as the first open-weight model broadly treated as frontier-adjacent for agentic work — #3 on GDPval-AA Elo, landing on AWS Marketplace, Baseten (>280 tok/s), and 20+ providers within days
- Sakana launched Fugu, a learned orchestration system across a model pool; praised for the concept but criticized for opaque baselines, missing cost accounting, and trailing Opus on SWE-Bench Pro by ~10 points
- Google promoted the Interactions API to GA as the new primary Gemini interface for agents, with background async execution, managed agents, and isolated remote Linux sandbox called Antigravity

## Community Signals (AI Twitter Recap)

OpenAI Daybreak, GPT-5.5-Cyber, and the policy/security split

OpenAI expanded its cyber stack beyond vuln discovery into remediation: OpenAI announced an expanded Daybreak program with a Codex Security plugin, the full GPT-5.5-Cyber model for trusted defenders, a Cyber Partner Program, and Patch the Planet for securing critical OSS. Follow-on posts added concrete scope: 30M+ commits scanned, 30K+ codebases covered, 70K+ reviewer-marked fixes, and 500K+ additional fixes detected automatically; major projects like cURL, Go, Python, Sigstore, and pyca/cryptography are in scope; and the plugin supports deep scans, threat modeling, patch generation, and export into existing workflows. The notable shift is from "find bugs" to closed-loop patch generation with human review.

Capability claims are colliding with export-control logic: OpenAI is explicitly claiming SOTA on CyberGym for GPT-5.5-Cyber via @sama, while the public debate around Anthropic's restricted Mythos/Fable access continued. @BlackHC asked the obvious policy question: if OpenAI's latest cyber model is stronger, why is it not under equivalent controls? @shashj also added an important correction to the Mythos story: NSA references to "hours, not weeks" were tied to red-teaming efforts with initial access assumptions, and those red teams reportedly no longer have Mythos access. The result is a widening gap between model capability reporting and coherent governance criteria.

Sakana Fugu's orchestration release and the benchmark transparency backlash

Fugu reframes "model release" as learned orchestration over a model pool: Sakana introduced Fugu, presenting it as a single API that learns model selection, delegation, verification, and synthesis across multiple frontier models; Vercel quickly added Fugu Ultra to AI Gateway. The product thesis resonated with engineers who already see real systems moving toward orchestration layers: @levie called routing/orchestration a likely high-value layer, and @audreyt reported Fugu Ultra working well as a planner/advisor paired with a fast driver loop. Sakana then published a sequence of use cases—autoresearch, finance, blindfold chess, CAD—arguing that test-time coordination can beat monolithic calls on long-horizon tasks.

The critique was immediate: opaque baselines, missing cost accounting, and questionable reporting: The most detailed teardown came from @eliebakouch, who argues Fugu is essentially a router/classifier plus a preplanned multi-step workflow system, with several core issues: it trails Opus on SWE-Bench Pro by ~10 points, compares against anonymized "Model A/B/C," omits token/cost reporting for best-of-N style orchestration, and should be compared against other test-time scaling setups rather than plain base models. Skepticism escalated further with @BlancheMinerva, who challenged Sakana's trustworthiness based on prior incidents and alleged impossible performance claims in earlier work.

GLM-5.2's breakout: open-weight agents, infra adoption, and real-harness wins

GLM-5.2 is emerging as the first open-weight model broadly treated as frontier-adjacent for agentic work: Multiple posts converged on the same story. Artificial Analysis put GLM-5.2 at #3 overall on GDPval-AA at 1524 Elo, behind only Claude Fable 5 and Opus 4.8, and level with or ahead of some proprietary models; they also highlighted GLM as the leading open-weight model and a strong point on the AA-Briefcase cost/performance frontier. @natolambert called it a possible "DeepSeek moment" for agents, while @AravSrinivas argued it revives serious interest in open source because it "passes the blind test" on median production knowledge work.

The strongest evidence came from actual harnesses, not abstract benchmark charts: Cline tested GLM-5.2 and Opus 4.8 on a real bug in the Cline repo using the same harness and found GLM was slower and more tool-call-heavy, but cheaper ($0.41 vs $0.81) and more robust in verification: it cleaned up dead code and confirmed the production build, while Opus left type errors that passed tests. @askalphaxiv said GLM-5.2 is the first open-weights model they've tried that can do real autoresearch tasks, including async vs colocated RL training runs over two 8xH100 nodes.

Distribution and serving velocity were unusually high: GLM-5.2 landed on AWS Marketplace, in Baseten's library with >280 tok/s and <0.8s TTFT, in Droid via Fireworks, in LangChain's deepagents code, and across many providers—one count put it at 20. There is also a growing ecosystem of practical guides, like running GLM-5.2 inside Claude Code via Baseten's OpenAI-compatible endpoint.

Agent infrastructure: Gemini Interactions API, Hermes expansion, and harness-first engineering

Google promoted the Interactions API to its primary Gemini interface for agents: Google and @OfficialLoganK announced the Interactions API is now GA and the new default for Gemini models and agents. The feature set is notable: one API for models and agents, background async execution, expanded tool support, multimodal generation, managed agents, and an isolated remote Linux sandbox called Antigravity per @_philschmid. That makes Google's stack look increasingly like a first-party answer to the "agent harness" problem, not just a model endpoint.

Skills, communication protocols, and stateful sessions are becoming first-class infra concerns: To smooth migration, Google shipped an installable Gemini Interactions skill that teaches coding agents the new SDK patterns and current model versions. In parallel, @omarsar0 highlighted a useful survey of nine open-source agent communication protocols, noting an emerging standard around hybrid payloads plus session-state persistence, while decentralized discovery remains immature.

Hermes continues to gain surface area as a local/personal agent platform: Hermes updates included iMessage access without a Mac, Raft integration as an external agent in a shared workspace, and most significantly GUI control for Windows or Linux desktop apps with any model. The repo also crossed 200K stars.

Inference economics, infrastructure scale, and the shift toward "owned intelligence"

Baseten's $1.5B Series F is a direct bet on post-trained open models and inference as the enterprise control plane: Baseten and CEO @amiruci argued that companies increasingly want to own their intelligence layer: run open or specialized models, post-train on their own data/evals, and retain control over continual learning. Their customer list—Abridge, Cursor, Decagon, Harvey, Notion, OpenEvidence, etc.—shows this is already happening at the application layer.

Compute leasing is becoming a strategic market of its own: Reports that Reflection signed a $6.3B compute deal with SpaceX for GB300 access were widely discussed; @jaminball contextualized it alongside SpaceX/xAI's other large compute deals with Anthropic and Google, noting implied Blackwell pricing above $10/hour and 90-day out clauses. If accurate, this makes "neocloud" capacity and GPU brokerage an increasingly important strategic layer between model builders and hardware supply.

Top tweets (by engagement):
OpenAI Daybreak / GPT-5.5-Cyber: @OpenAI, @sama
GLM-5.2 real-world validation: @cline
Google's Interactions API GA: @Google
Baseten Series F / owned intelligence thesis: @amiruci
Sakana Fugu release: @SakanaAILabs

Benchmarks, eval methodology, and the move from static scores to real workflows

Judge reliability is under fresh scrutiny: @dair_ai summarized a large LLM-as-a-Judge audit across 21 judges, nine providers, and about 541K judgments. The key result is methodological: exact-match agreement materially overstates judge quality, while switching to Cohen's kappa deflates agreement by 33–41 points on MT-Bench, with judge rankings shifting significantly. That's a strong warning for teams using judge models as internal eval infrastructure.

There is increasing pressure to evaluate agents as systems, not chatbots: Jules framed this explicitly: the goal is not just an agent that reacts, but one that notices, anticipates, and partners. Relatedly, @rseroter highlighted the distinction between using a coding agent and engineering an autonomous coding harness. The most substantive posts of the day—GLM in Cline, OpenAI Daybreak, Fugu criticism—were all really about system behavior under tools, memory, verification, and long-horizon execution, not raw single-turn IQ.

## Why It Matters

SpaceX's emergence as the dominant GPU compute lessor ($28B/yr) alongside the commoditization of frontier open models signals a structural shift: the moat in AI is moving from model quality to compute ownership, inference optimization, and post-training on proprietary data.

---
[Source: AINews](https://www.latent.space/p/ainews-spacex-is-already-a-28byr)
