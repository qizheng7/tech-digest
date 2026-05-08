---
title: "OpenAI Releases MRC: An Open Networking Protocol for 100K+ GPU Training Clusters"
date: 2026-05-06
source_url: https://openai.com/index/mrc-supercomputer-networking/
source: OpenAI
type: article
topics: [ai-infra]
tags: [OpenAI, MRC, networking, ethernet, OCP, supercomputer, training, infrastructure, AMD, NVIDIA, InfiniBand, distributed]
saved_at: 2026-05-07
---

## Summary

OpenAI released MRC (Multipath Reliable Connection), an open networking protocol designed for AI training clusters at 100K+ GPU scale, contributing the specification to the Open Compute Project (OCP). The protocol distributes traffic across hundreds of simultaneous network paths using dynamic packet spraying and SRv6-based source routing, achieving microsecond failover around failures. MRC is already deployed on OpenAI's largest GB200 supercomputers at Oracle Cloud (Abilene, TX) and Microsoft Fairwater sites.

## Key Highlights

- Developed in consortium with AMD, Broadcom, Intel, Microsoft, and NVIDIA; released as open OCP specification
- Uses dynamic packet spraying across hundreds of simultaneous paths, eliminating fixed-routing congestion points
- SRv6-based source routing encodes routing decisions directly into packet headers for microsecond rerouting around failures
- Already deployed at OpenAI's Oracle Cloud Abilene and Microsoft Fairwater GB200 supercomputers
- Positioned as combining "the losslessness of InfiniBand with the flexibility of a stateless, global IPv6 standard"
- Ethernet surpassed InfiniBand in AI network sales in 2025; MRC accelerates this structural shift

## Why It Matters

As training clusters approach 500K+ GPUs, network congestion and failures have become the primary source of compute inefficiency — MRC makes Ethernet viable at frontier scale and could define the networking stack for the next generation of AI supercomputers.

---
[Source: OpenAI](https://openai.com/index/mrc-supercomputer-networking/)
