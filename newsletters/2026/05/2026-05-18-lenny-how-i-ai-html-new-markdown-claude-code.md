---
title: "How I AI: HTML is the New Markdown — How Anthropic Engineers Are Building with Claude Code"
date: 2026-05-18
source_url: https://www.lennysnewsletter.com/p/how-i-ai-html-is-the-new-markdown
source: Lenny's Newsletter
type: newsletter
newsletter: Lenny's Newsletter
topics: [newsletter, genai-llm]
tags: [Claude-Code, Anthropic, HTML, Markdown, agentic-workflows, spec-driven-development, compute-allocator, design-system, AI-workflow, coding-agent, Thariq-Shihipar]
saved_at: 2026-05-19
---

## Summary

Thariq Shihipar, engineer on Anthropic's Claude Code team, shares how he replaced Markdown with interactive HTML artifacts for planning, specs, and design systems when building with Claude Code. Recorded live at Anthropic's "Code with Claude" event, the episode argues that as context windows scale and plans run to thousands of lines, HTML's interactivity and density make the AI's output actually legible and engaging — fundamentally changing the engineer's role from code writer to "compute allocator."

## Key Highlights

- **HTML > Markdown for AI specs**: HTML offers interactive elements, visual mockups, scrollable sections — critical when plans hit thousands of lines that engineers otherwise skip
- **Engineers as compute allocators**: when Claude runs for 8 hours on a single task, the key skill is deciding what's worth $500 of compute, not writing the code
- **Throwaway micro-UIs**: ask Claude to generate a custom editing interface for one specific section of a plan, use it, discard it — "micro software on top of micro software"
- **Living HTML design systems**: a single HTML file encodes colors, typography, spacing, components — passes across projects, extracted from existing codebases, human- and machine-readable simultaneously
- **~1% of tokens reach production**: the rest go into dashboards, interfaces, status updates, and planning tools; token abundance enables richness in process
- **Simple prompts work better**: "Create an HTML file with a plan. Help me visualize. Include excerpts, mockups, code, whatever is needed to give me maximum context." — trusting open-ended prompts outperform over-constrained system prompts
- **Test verification ≠ testing**: traditional unit tests are being replaced by verification rubrics, managed agent checks, and Claude recording video of what it did

## Why It Matters

HTML-as-interface for AI collaboration is a practical workflow shift any engineer can adopt today, and Thariq's "compute allocator" framing redefines the value of the engineer role in an agentic-first world.

---
[Source: Lenny's Newsletter](https://www.lennysnewsletter.com/p/how-i-ai-html-is-the-new-markdown)
