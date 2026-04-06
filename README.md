# Tech Digest

A personal knowledge base of tech articles, trends, and newsletter summaries — indexed for future search and deep-dives.

## What's in here

Each article is saved as a standalone markdown file with structured metadata (frontmatter), making it easy to search by topic, source, date, or tag — both on GitHub and with future tooling.

## Structure

```
tech-digest/
├── articles/          # Articles from specific URLs
│   └── YYYY/MM/       # Organized by year and month
│       └── YYYY-MM-DD-article-title.md
├── newsletters/       # Articles extracted from newsletter emails
│   └── YYYY/MM/
│       └── YYYY-MM-DD-article-title.md
└── INDEX.md           # Running table of contents (auto-updated)
```

## Article format

Each file contains:

```markdown
---
title: "Article Title"
date: YYYY-MM-DD
source_url: https://...
source: Publication Name
type: article  # or: newsletter
newsletter: TLDR  # if from a newsletter
tags: [AI, LLM, inference]
saved_at: YYYY-MM-DD
---

## Summary
Short paragraph (2–4 sentences)

## Key Highlights
- Bullet points of key facts, numbers, and implications

## Why It Matters
One sentence on the broader trend or significance.
```

## How articles get added

Articles are added via the `/trend-digest` Claude Code skill:

- **`/trend-digest <url1> <url2>`** — summarize and save specific articles
- **`/trend-digest subscribe`** — scan recent newsletter emails, extract article links, summarize and save

## Searching

- **GitHub search** — use the search bar (or press `t`) to search across all files
- **By tag** — search for a tag name like `LLM` or `robotics` to find related articles
- **By source** — search for a publication name like `TechCrunch` or `MIT Tech Review`
- **INDEX.md** — browse the full chronological table of contents
