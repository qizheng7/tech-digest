---
title: "Inside Thinking Machines' Interaction Models"
date: 2026-06-30
source_url: https://blog.bytebytego.com/p/inside-thinking-machines-interaction
source: ByteByteGo
type: newsletter
newsletter: ByteByteGo
topics: [newsletter, genai-llm, ai-infra]
tags: [interaction-model, real-time-AI, multimodal, TML-Interaction-Small, MoE, micro-turns, voice-AI, harness, SGLang, streaming]
saved_at: 2026-06-30
---

## Summary

ByteByteGo covers Thinking Machines' new TML-Interaction-Small — a 276B MoE model (12B active params) designed for real-time human-AI collaboration. Rather than wrapping a turn-based LLM in a harness of voice-activity detectors and STT/TTS components, Thinking Machines built interactivity *into* the model itself via 200ms "micro-turns" that treat time (not conversation turns) as the fundamental unit. The article argues this represents a capability ceiling breakthrough analogous to deep learning replacing hand-crafted CV features.

## Key Highlights

- Today's voice AI is a harness: voice activity detection → STT → LLM → TTS → dialog manager; the helper components are simpler than the model and create a capability ceiling
- TML-Interaction-Small uses **time-aligned micro-turns**: the model processes 200ms chunks of concurrent audio, video, and text streams, deciding each micro-turn whether to speak, listen, or interject
- Capabilities unlocked: simultaneous speak+listen (live translation), watch+speak (live sports commentary), mid-sentence interjection (pushup counting, codeswitching correction) — all from one architectural choice
- Two-model coordination: fast interaction model (200ms micro-turns) + slower background model (deep reasoning, tool use, browsing) that share context and weave results back naturally
- Custom benchmarks: TimeSpeak (initiate speech at specified times), CueSpeak (interject while user is talking), RepCount-A (count video reps), ProactiveVideoQA (answer based on live visual events) — all existing models fail these
- Contributed streaming session feature back to SGLang for efficient 200ms chunk processing; limited research preview planned in coming months

## Why It Matters

The harness pattern (specialized helper components wrapped around a general model) has a ceiling; Thinking Machines' bet is that embedding interactivity inside the model itself is the correct scaling path, and their custom benchmarks show existing models can't do what micro-turns enable.

---
[Source: ByteByteGo](https://blog.bytebytego.com/p/inside-thinking-machines-interaction)
