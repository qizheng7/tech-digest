---
title: "DeepSeek-V4 on Day 0: From Fast Inference to Verified RL with SGLang and Miles"
date: 2026-04-25
source_url: https://www.lmsys.org/blog/2026-04-25-deepseek-v4/
source: LMSYS Blog
type: article
topics: [ai-infra]
tags: [inference, SGLang, DeepSeek, MoE, RL-training, open-source, FP4]
saved_at: 2026-04-28
---

## Summary

SGLang and Miles shipped Day-0 support for DeepSeek V4 Pro (1.6T) and Flash (284B) across both inference and RL training. The release introduces ShadowRadix prefix cache, HiSparse CPU-extended KV, MTP speculative decoding, Flash Compressor, Lightning TopK, and hierarchical multi-stream overlap. The team also delivers a verified end-to-end RL training pipeline via Miles at launch — the first open-source stack to serve and train V4 on day one.

## Key Highlights

- Day-0 inference + RL training for both DeepSeek V4 Pro (1.6T) and Flash (284B)
- ShadowRadix prefix caching optimized for V4's hybrid sparse-attention and MoE architecture
- TRTLLM-Gen fused MoE backend via FlashInfer pairs MXFP8 activations with MXFP4 expert weights
- HiSparse CPU-extended KV enables long-context serving beyond GPU memory limits
- Miles RL pipeline provides end-to-end Verified RL training stability, efficiency, and broad hardware support

## Why It Matters

Day-0 open-source parity with frontier model releases accelerates the research-to-production cycle and allows the broader community to fine-tune and experiment with state-of-the-art models immediately on launch.

---
[Source: LMSYS Blog](https://www.lmsys.org/blog/2026-04-25-deepseek-v4/)
