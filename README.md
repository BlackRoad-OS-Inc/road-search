# RoadSearch

Full-text search engine built on SQLite FTS5. Fast ranked results, AI-generated answers, autocomplete.

**Live at [search.blackroad.io](https://search.blackroad.io)**

## What It Does

RoadSearch indexes content and returns ranked results in milliseconds. BM25 ranking, prefix matching, and optional AI answer generation from top results via Ollama.

- **43 pages** indexed across BlackRoad domains
- **AI answers** — direct answers synthesized from search results (Ollama/Mistral)
- **Autocomplete** — suggestions from titles and recent queries
- **Trending** — 7-day query analytics
- **Lucky mode** — redirect straight to the best result

## API

| Endpoint | Description |
|----------|-------------|
| `GET /api/search?q=` | Full-text search with BM25 ranked results and snippets |
| `GET /api/suggest?q=` | Autocomplete suggestions |
| `GET /api/stats` | Index size, query count, health |
| `GET /lucky?q=` | Redirect to top result |
| `POST /api/index` | Add pages to the index (auth required) |

## Stack

- **Runtime**: Cloudflare Worker
- **Database**: D1 (SQLite FTS5)
- **Ranking**: BM25 with custom field weights
- **AI**: Ollama (Mistral) for answer generation
- **Frontend**: Vanilla JS search UI

## Deploy

```bash
npm install
npm run dev        # Local dev server
npm run deploy     # Deploy to production
```

## How It Works

1. Pages are crawled and stored in D1 with FTS5 indexes
2. Queries hit FTS5 with BM25 ranking and snippet extraction
3. Top results are optionally passed to Ollama for answer synthesis
4. Category and domain filtering narrow results
5. Response times under 100ms for most queries

## License

Proprietary. Copyright (c) 2024-2026 BlackRoad OS, Inc. All rights reserved.

---

*Remember the Road. Pave Tomorrow.*
