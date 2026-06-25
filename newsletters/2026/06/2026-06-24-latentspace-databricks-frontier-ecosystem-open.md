---
title: "Why the Frontier Ecosystem must be Open — Matei Zaharia and Reynold Xin, Databricks"
date: 2026-06-24
source_url: https://www.latent.space/p/databricks
source: Latent.Space
type: newsletter
newsletter: Latent.Space
topics: [newsletter, ai-infra, ai-startup, genai-llm]
tags: [Databricks, Omnigent, LTAP, meta-harness, open-source, agent-cloud, data-lakehouse, Matei-Zaharia, inference, enterprise]
saved_at: 2026-06-25
---

## Summary

Recorded live at the 2026 Data + AI Summit (30,000 in person, 100,000 worldwide), Databricks cofounders Matei Zaharia and Reynold Xin join swyx to discuss the company's two new announcements: Omnigent (open-source meta-harness above all coding agents) and LTAP (a database architecture replacing CDC/HTAP). Databricks ($175B valuation) is pushing from data lakehouse to full data-and-AI operating system.

## Key Highlights

- **Omnigent** is an open-source "agent cloud" providing a uniform API (sessions, messages, file sends, streams, tool calls, cancellation) on top of Claude Code, Codex, Cursor, Pi, and custom agents — solving portability, collaboration, session persistence, search, spend controls, and security in one layer
- **~400 merged PRs within days** of Saturday release, roughly half from outside Databricks — unusually fast community adoption
- **The core problem** it solves: Reynold describes tethering his laptop to his phone while driving to a doctor's appointment to keep an agent session alive. Cloud sandboxes that don't shut down are the fix
- **At Databricks' scale** (50–60M VMs/day, exabytes processed before breakfast), agent security and spend control become critical: a single agent can burn $500 accidentally reading logs, or read confidential docs, install a compromised npm package, and leak data
- **LTAP (Lakehouse Transactional-Analytical Processing):** Databricks' answer to why CDC = "continuous data corruption" and why HTAP has been the holy grail. It unifies the storage layer (writing transactional data in columnar Parquet formats) instead of collapsing every query engine — giving agents live operational context from databases
- **The durable moat**: when frontier model performance commoditizes, the advantage is company-specific context: proprietary data, governed access, operational state, transaction logs, workflows. "Get the data there, slap some agent on top" will rewrite traditional software

## Why It Matters

Omnigent directly addresses the "agent portability" problem that every AI shop is independently solving — if it becomes the standard harness layer above coding agents, Databricks gains a strategic position in every AI development stack, not just data infrastructure.

---
[Source: Latent.Space](https://www.latent.space/p/databricks)
