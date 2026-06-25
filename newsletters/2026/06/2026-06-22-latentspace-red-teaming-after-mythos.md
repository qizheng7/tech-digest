---
title: "Red-Teaming after Mythos — Zico Kolter & Matt Fredrikson, Gray Swan"
date: 2026-06-22
source_url: https://www.latent.space/p/gray-swan
source: Latent.Space
type: newsletter
newsletter: Latent.Space
topics: [newsletter, genai-llm, ai-infra]
tags: [red-teaming, AI-safety, prompt-injection, Gray-Swan, Mythos, jailbreak, security, Shade, Cygnal, enterprise-AI]
saved_at: 2026-06-25
---

## Summary

Prompted by US Government export control directives on Claude Mythos/Fable and the resulting focus on jailbreaks and prompt injection, swyx interviews Gray Swan cofounders Zico Kolter (CMU professor, OpenAI board Safety & Security Committee member) and Matt Fredrikson (CMU professor, Gray Swan CEO). Gray Swan was cited in the Mythos model card and co-authored the definitive paper on Indirect Prompt Injections. The episode covers Shade (adversarial red-teaming AI), Cygnal (guardrails model), and their AI Red Teaming Arena.

## Key Highlights

- **Shade** outperforms human red teamers at breaking AI systems — a specialized AI attacking AI is more scalable and thorough than human-run security tests. Anthropic used Shade to evaluate robustness against prompt injection in coding environments
- **The "lethal trifecta"** (Simon Willison framing): untrusted data in context + access to private data + an exfiltration channel. Any agent with all three is exploitable
- **Bigger models ≠ more robust**: scale improves capability but doesn't solve adversarial robustness — "just prompt it better" is insufficient for enterprise AI security
- **LLMs as alien intelligence**: browser-based human users ranked 4th in agent robustness tests — agents are more vulnerable to certain attack vectors than humans
- **The first major AI prompt-injection breach** framed as a "gray swan" — not unknowable, but an event everyone can see coming. OpenClaw (computer-use agents) introduces an especially dangerous new attack surface
- **Product suite:** Shade (red-teaming), Cygnal (AI guardrails/policy enforcement), and world's largest AI Red Teaming Arena with community red teamers

## Why It Matters

As AI agents gain real-world system access, the gap between model alignment and enterprise security becomes dangerous — the prompt-injection surface area for agents with tool access is orders of magnitude larger than for chat interfaces.

---
[Source: Latent.Space](https://www.latent.space/p/gray-swan)
