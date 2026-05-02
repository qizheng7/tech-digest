---
title: "Automating GPU Kernel Translation with AI Agents: cuTile Python to cuTile.jl"
date: 2026-04-30
source_url: https://developer.nvidia.com/blog/automating-gpu-kernel-translation-with-ai-agents-cutile-python-to-cutile-jl/
source: NVIDIA Developer Blog
type: article
topics: [ai-infra]
tags: [GPU, CUDA, Julia, Python, AI-agents, kernel-optimization, cuTile, TileGym]
saved_at: 2026-05-01
---

## Summary

NVIDIA researchers built TileGym, an AI agent workflow for translating GPU kernel code from cuTile Python to cuTile.jl (Julia). Rather than generating code from scratch, the agent references a "skills" repository containing 17 documented translation rules, API mappings, worked examples, validation scripts, and debugging guides — systematically handling semantic differences that produce silent errors rather than compiler warnings. A representative matrix multiplication kernel was translated in approximately 4 minutes with 78K tokens and zero manual intervention, transforming what was a one-off porting effort into a repeatable, scalable process.

## Key Highlights

- 17 critical semantic differences between Python/Julia cuTile implementations: indexing (0-based vs 1-based), memory layout (row-major vs column-major), type casting, syntax variations
- Silent errors (not compiler warnings) make manual translation dangerous and error-prone
- TileGym "skills" structure: API mapping files + critical rules + worked examples + validation scripts + debugging guides
- Matrix multiply kernel: ~4 minutes, 78K tokens, zero manual intervention with the skill-based approach
- cuTile enables high-level tile-based GPU kernel programming without managing individual threads and memory addresses
- Approach is extensible to future kernel translations as skill libraries grow

## Why It Matters

AI agents can now automate GPU kernel porting between programming languages with high accuracy, potentially accelerating Julia adoption in ML workloads and offering a template for skill-driven code migration at scale.

---
[Source: NVIDIA Developer Blog](https://developer.nvidia.com/blog/automating-gpu-kernel-translation-with-ai-agents-cutile-python-to-cutile-jl/)
