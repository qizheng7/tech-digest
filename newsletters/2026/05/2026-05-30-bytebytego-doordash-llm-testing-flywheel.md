---
title: "How DoorDash Built a Testing System to Evaluate LLMs"
date: 2026-05-30
source_url: https://blog.bytebytego.com/p/how-doordash-built-a-testing-system
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm, ai-infra]
tags: [DoorDash, LLM-evaluation, simulation, hallucination, chatbot, testing, flywheel, LLM-as-judge, generator-verifier-gap, agent-evaluation]
saved_at: 2026-06-01
---

## Summary

DoorDash's customer support chatbot had a subtle hallucination problem: too much data in the context window caused the model to misread fields and suggest non-existent refund policies. Their solution — the "simulation and evaluation flywheel" — runs 200+ realistic multi-turn LLM-to-LLM customer conversations in under 5 minutes, evaluates results automatically with an LLM judge, and achieves a 90% reduction in hallucinations in simulation that carries over to production. The core architectural fix was a "case state" layer that synthesizes raw tool history into a clean intermediate representation — giving the chatbot less information, not more, fixed the hallucinations.

## Key Highlights

- **Flywheel**: offline LLM-simulated conversations (customer role played by LLM using real historical transcripts) + LLM-as-judge evaluation → tight iteration loop without risking real customers
- **Speed**: 200+ simulated conversations in under 5 minutes; what used to take days of manual testing now takes hours
- **Generator-verifier gap**: acting as a full support agent is hard (complex, multi-step, open-ended); verifying a single narrowly-defined behavior (binary pass/fail) is much simpler — LLMs are reliable at the latter
- **Calibration process**: human experts label samples, LLM judge grades the same samples, disagreements analyzed, prompt revised until judge matches human expert judgment
- **Case state architecture**: synthesizes raw tool call history into a structured intermediate representation — counter-intuitive fix: giving model LESS data reduced hallucinations
- **90% hallucination reduction** in simulation after 11 iterations; strong offline-to-production correlation validates the flywheel as a reliable development tool (not just a sandbox)
- 50+ evaluations covering hallucination detection, tone assessment, issue classification; must pass full suite before any production deployment

## Why It Matters

DoorDash's flywheel is the canonical example of how LLM systems require a completely different testing paradigm than deterministic software — the same offline-eval → iterate loop is now the standard pattern for any production AI system handling real customer interactions.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/how-doordash-built-a-testing-system)
