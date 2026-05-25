---
title: "TeamPCP Breaches GitHub via Poisoned VS Code Extension, Steals 3,800 Internal Repos"
date: 2026-05-20
source_url: https://thehackernews.com/2026/05/github-internal-repositories-breached.html
source: The Hacker News
type: article
topics: [ai-infra, ai-startup]
tags: [TeamPCP, supply-chain, VS-Code, GitHub, npm, developer-security, Nx-Console, Mini-Shai-Hulud, TanStack, CVE, credential-theft, Claude-Code, PyPI, infosec]
saved_at: 2026-05-24
---

## Summary

Threat actor TeamPCP breached GitHub's internal codebase on May 18, 2026 by distributing a malicious version of the Nx Console VS Code extension (2.2M installs) for just 18 minutes on the Visual Studio Marketplace. The trojanized extension harvested credentials from developer environments — including 1Password vaults, Anthropic Claude Code configurations, GitHub tokens, and AWS keys — enabling the exfiltration of ~3,800 GitHub internal repositories. The attack was part of a broader Mini Shai-Hulud supply chain worm campaign that had earlier compromised the TanStack npm library (May 11) and Microsoft's Python durabletask SDK on PyPI.

## Key Highlights

- Poisoned Nx Console extension (v18.95.0) was live for only **18 minutes** (12:30–12:48 UTC, May 18); enough for widespread deployment
- Exfiltrated: ~3,800 GitHub internal repos, credentials from 1Password, Claude Code configs, npm, GitHub, and AWS accounts
- Also hit in the broader Mini Shai-Hulud campaign: OpenAI (May 11, 2 devices), Mistral AI, Grafana Labs, Microsoft Python SDK (PyPI)
- Nx developer's system was itself compromised in the earlier TanStack attack, propagating the chain
- 639 malicious npm package versions forged with valid cryptographic provenance in a single wave
- Stolen GitHub data listed for sale on criminal forums at $50,000+

## Why It Matters

The attack demonstrates that developer toolchains — VS Code extensions, npm packages, PyPI packages — are now primary AI-era attack surfaces, with Claude Code configs and AI company credentials explicitly targeted alongside traditional cloud and version-control secrets.

---
[Source: The Hacker News](https://thehackernews.com/2026/05/github-internal-repositories-breached.html)
