<div align="center">
<img src="https://images.blackroad.io/pixel-art/road-logo.png" alt="BlackRoad OS" width="80" />

# RoadSearch

**FTS5 search engine with AI answers across the BlackRoad ecosystem.**

[![BlackRoad OS](https://img.shields.io/badge/BlackRoad_OS-Pave_Tomorrow-FF2255?style=for-the-badge&labelColor=000000)](https://blackroad.io)
</div>

---

## Live

**[search.blackroad.io](https://search.blackroad.io)** — 43 pages indexed, AI-powered answers via Ollama.

## Architecture

```
Browser → Cloudflare Worker → D1 (FTS5) → Results
                                ↓
                         Ollama (AI answers)
```

## API

```bash
# Search
curl "https://search.blackroad.io/api/search?q=agent&limit=10"

# Autocomplete
curl "https://search.blackroad.io/api/suggest?q=black"

# Stats
curl "https://search.blackroad.io/api/stats"

# I'm Feeling Lucky
curl "https://search.blackroad.io/lucky?q=lucidia"

# Index new pages (auth required)
curl -X POST "https://search.blackroad.io/api/index" \
  -H "Authorization: Bearer $INDEX_KEY" \
  -d '[{"url":"https://example.com","title":"Example","description":"..."}]'
```

## Features

- **FTS5 full-text search** with ranking and snippets
- **AI answers** via Ollama (Mistral) — summarizes top results
- **Autocomplete** from titles + recent queries
- **Trending queries** with 7-day analytics
- **Category/domain filtering**
- **I'm Feeling Lucky** redirect
- **43 seed pages** covering all BlackRoad domains

## Stack

- Cloudflare Workers + D1 (FTS5)
- Ollama for AI answer generation
- Vanilla JS frontend with search UI

---

*Copyright (c) 2024-2026 BlackRoad OS, Inc. All rights reserved.*
