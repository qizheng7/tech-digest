---
title: "Giving Agents Computers — Ivan Burazin, Daytona"
date: 2026-05-21
source_url: https://www.latent.space/p/daytona
source: Latent.Space
type: newsletter
newsletter: Latent.Space
topics: [newsletter, ai-infra, ai-startup]
tags: [Daytona, agent-sandboxes, computer-use, bare-metal, RL-training, Windows-compute, agent-infrastructure, cloud, Ivan-Burazin, CodeAnywhere]
saved_at: 2026-05-21
---

## Summary

Ivan Burazin, CEO of Daytona, joined swyx on Latent Space to trace the journey from CodeAnywhere (one of the first browser-based IDEs, 2000s) through a failed human-dev-environment product, to Daytona's current position as a leading provider of AI agent sandboxes. The episode covers how agent compute differs fundamentally from human compute — demanding stateful, composable, instantly-resizable sandboxes rather than generic VMs — and how Daytona's bare-metal-plus-custom-scheduler architecture enables 60ms startup times and 850,000 daily sandbox runs for its largest customer. Ivan also explains the explosion of RL/eval workloads (now roughly 50% of usage), the challenges and opportunity in Windows/macOS computer-use sandboxes, why CLI gives agents more leverage than MCP, and why the agent infra market is growing 40%+ month-over-month across all providers, with CPU availability — not GPUs — potentially becoming the next bottleneck.

## Key Highlights

- **Agents need composable computers, not disposable boxes.** Daytona delivers Linux, Windows, macOS, and GPU sandboxes via an API with stateful snapshots, ~60ms startup time for one sandbox, and ~75 seconds for 50,000 concurrent sandboxes.
- **The pivot happened New Year's Eve 2024:** After discovering that agents couldn't use the human-oriented dev environment, Ivan half-coded a new MVP overnight. Every single prospect immediately asked for access — a reaction he had never seen before.
- **RL and eval workloads went from 0% to ~50% of usage in months.** These "square spike" workloads (zero → 100,000 CPUs → zero, unpredictably) create 15% mean utilization despite 90% peak utilization.
- **Bare metal + custom scheduler is the core differentiator.** Daytona runs on bare metal with NVMe-local snapshots and no network layer between sandbox and disk — enabling Docker-inside-Docker and K3S-inside-sandbox for RL workloads. Firecracker VMs and Kubernetes were too slow and rigid.
- **Windows sandboxes are the next big bet.** Ivan estimates the TAM from automating 40% of knowledge workers' legacy-app tasks at ~$10T/year. macOS is severely constrained by Apple licensing (2 parallel VMs max, 24-hour exclusive licensing, no cross-machine snapshot migration).
- **The future AI cloud may look more like Stripe than AWS** — a consumption-billed API platform bundling sandboxes, search, agent-native databases, and other primitives, rather than raw infrastructure provisioning.

## Why It Matters

Agent sandboxes are becoming the unsexy bottleneck of the agentic AI wave — Daytona's 40%+ month-over-month growth across the sector and the shift of RL workloads from niche to majority of usage signals that the "give agents computers" infrastructure layer is now the fastest-growing primitive in the AI stack.

---
[Source: Latent.Space](https://www.latent.space/p/daytona)
