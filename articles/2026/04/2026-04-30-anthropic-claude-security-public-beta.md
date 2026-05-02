---
title: "Claude Security Launches in Public Beta to Find and Fix Software Vulnerabilities"
date: 2026-04-30
source_url: https://www.anthropic.com/news/claude-code-security
source: Anthropic
type: article
topics: [genai-llm, ai-startup]
tags: [security, code-review, vulnerability-scanner, Claude, enterprise, DevSecOps, Opus-4.7, SAST]
saved_at: 2026-05-01
---

## Summary

Anthropic launched Claude Security in public beta for Enterprise customers on April 30, graduating from its February 2026 limited research preview after hundreds of organizations used it to find vulnerabilities missed by existing tools. Powered by Claude Opus 4.7, the system scans codebases by reasoning about code like a security researcher — tracing data flows across files, understanding component interactions, and catching complex issues like flawed business logic and broken access controls — rather than pattern-matching like traditional SAST tools. All findings appear in a dashboard where developers review and approve fixes; nothing is applied automatically.

## Key Highlights

- Powered by Claude Opus 4.7; uses data-flow reasoning rather than rule-based pattern matching
- Traces logic across files and modules, catches business logic flaws and broken access controls
- Multi-stage verification filters false positives; each finding includes confidence rating and detailed explanation
- New in public beta: scheduled scans for continuous monitoring, dismissal with documented reasons, CSV/Markdown export for audit systems
- Claimed 500+ vulnerabilities found in production open-source projects that escaped detection for years
- Available to Claude Enterprise customers; free access for open-source maintainers via claude.com/contact-sales/security
- Cursor simultaneously shipped Cursor Security Review (always-on PR review + scheduled codebase scans)

## Why It Matters

Model labs are moving directly into the DevSecOps category, using reasoning-capable models to identify vulnerability classes — flawed logic, indirect injection, access control gaps — that rule-based scanners structurally cannot detect.

---
[Source: Anthropic](https://www.anthropic.com/news/claude-code-security)
