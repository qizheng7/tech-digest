---
title: "Remote agents in Vibe. Powered by Mistral Medium 3.5."
date: 2026-04-29
source_url: https://mistral.ai/news/vibe-remote-agents-mistral-medium-3-5
source: Mistral AI
type: article
topics: [genai-llm, ai-infra]
tags: [Mistral, open-weights, agents, remote-execution, coding, benchmark, SWE-bench, MoE, vibe]
saved_at: 2026-04-30
---

## Summary

Mistral AI released Mistral Medium 3.5 on April 29, 2026 — a 128B dense open-weight model with a 256K context window, released under a modified MIT license. Alongside the model, Mistral launched remote coding agents in its Vibe CLI, allowing async cloud execution of agent sessions that can run in parallel without developer intervention. The model claims 77.6% on SWE-Bench Verified, ahead of Devstral 2 and comparable open-weight models.

## Key Highlights

- **Architecture**: Dense 128B parameters, 256K context window, configurable reasoning effort per request, custom-trained vision encoder supporting variable image sizes
- **Performance**: 77.6% SWE-Bench Verified, 91.4 on τ³-Telecom agentic benchmark
- **Open weights**: Available on Hugging Face under modified MIT license; API pricing at $1.5/M input, $7.5/M output tokens
- **Remote agents in Vibe**: Local CLI sessions can be "teleported" to cloud with history preserved; sessions execute in parallel asynchronously
- **Integrations**: GitHub, Linear, Jira, Sentry, Slack, and Teams; Work mode in Le Chat for multi-step tasks
- **Hosted on**: NVIDIA GPU endpoints and NIM containerized inference

## Why It Matters

Mistral Medium 3.5 is the first open-weight model to pair frontier-class agentic coding performance with cloud-native async execution infrastructure, pushing the benchmark for what European AI labs can deliver while making remote agent workflows accessible at MIT-adjacent licensing terms.

---
[Source: Mistral AI](https://mistral.ai/news/vibe-remote-agents-mistral-medium-3-5)
