---
title: "MiniMax M3 in vLLM: Day-0 Serving for 1M-Token Multimodal Reasoning"
date: 2026-06-12
source_url: https://vllm.ai/blog/2026-06-12-minimax-m3-vllm
source: vLLM
type: article
topics: [ai-infra, genai-llm]
tags: [vLLM, MiniMax, MiniMax-M3, MoE, multimodal, long-context, sparse-attention, MXFP8, EAGLE3, KV-cache, agentic]
saved_at: 2026-06-15
---

## Summary

vLLM added day-0 support for MiniMax M3, a Mixture-of-Experts multimodal model with a 1-million-token context window. The key serving challenge is making million-token inference practical — vLLM addresses this via the MiniMax Sparse Attention (MSA) backend, which scores 128-token KV blocks, selects the top blocks per query, and runs GQA attention only over selected blocks. The model natively handles text, images, and video without separate encoder systems, and supports togglable reasoning modes (enabled, disabled, or adaptive).

## Key Highlights

- 1M token context length with MoE architecture and MXFP8 quantized checkpoints
- MiniMax Sparse Attention (MSA): block-level scoring reduces computational overhead for long-context serving
- Native multimodal: image and video inputs flow through integrated preprocessing pipelines (no sidecar encoders)
- Supports EAGLE3 speculative decoding with draft models for latency reduction
- Built-in tool parsing, reasoning extraction, and prefix caching support
- Available day-0: released by MiniMax and served via vLLM simultaneously on June 12

## Why It Matters

MiniMax M3 demonstrates that million-token multimodal reasoning is ready for production serving — and vLLM's sparse attention approach provides a blueprint for efficiently serving other long-context MoE models.

---
[Source: vLLM](https://vllm.ai/blog/2026-06-12-minimax-m3-vllm)
