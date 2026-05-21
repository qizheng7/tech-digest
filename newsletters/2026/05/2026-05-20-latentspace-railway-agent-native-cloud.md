---
title: "Railway: The Agent-Native Cloud — Jake Cooper"
date: 2026-05-20
source_url: https://www.latent.space/p/railway
source: Latent.Space
type: newsletter
newsletter: Latent.Space
topics: [newsletter, ai-infra, ai-startup]
tags: [Railway, agent-native, cloud, deployment, infrastructure, bare-metal, Jake-Cooper, coding-agents, CI-CD, versioning, observability, Railpack, Nixpacks, agentic-workflows]
saved_at: 2026-05-20
---

## Summary

Latent.Space interviews Jake Cooper, founder of Railway, about how the 35-person deployment platform (3M users, ~100K signups/week) has evolved from a developer-friendly PaaS into agent-native cloud infrastructure. Cooper argues that the pull request is obsolete and the future is instant production iteration with versioned infrastructure snapshots and autonomous rollbacks — enabled by agents operating with specialized tooling. Railway now spends ~$200K/month on coding agents across the company, with Cooper personally spending ~$25K/month.

## Key Highlights

- Railway: 3M users, 35-person team, ~100K new signups weekly; 6 years from hand-acquiring first 100 users to profitability after a $500K/month free-tier phase
- **Agent-native infrastructure**: versioning/branching, observability (logs/traces/metrics), 1,000x compute/storage scaling, safe production forking via copy-on-write databases, progressive rollouts with feature flags
- **Bare metal data centers**: 3-month hardware payback vs. cloud costs; 70% margins on own hardware fund cloud bursting
- **Custom infra**: Railpack (dependency detection), Nixpacks, content-addressable filesystems, custom Linux kernel patches for optimized storage
- **Agent economics**: ~$200K/month company-wide on coding agents; Cooper's personal spend: ~$25K/month. Philosophy: "If you're writing code by hand, you're doing this wrong"
- **Core thesis**: The pull request is obsolete — future dev cycles will feature instant production iteration, versioned infrastructure snapshots, and autonomous rollbacks

## Why It Matters

Railway's trajectory illustrates how coding agents are reshaping cloud infrastructure requirements from the bottom up — the platform built for human developers is being rebuilt for agent-driven iteration loops, and the unit economics of bare metal make agent-first companies viable at a much smaller headcount than before.

---
[Source: Latent.Space](https://www.latent.space/p/railway)
