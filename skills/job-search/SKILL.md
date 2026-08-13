---
name: job-search
description: >-
  Guides Worklittle job search and discovery: search_jobs / GET /jobs filters,
  quota-aware pagination, get_job_details vs get_job_keywords, closed jobs, and
  free market stats. Use when searching jobs, building a job board or search
  assistant, ranking roles, or answering market questions from Worklittle data.
---

## Canonical funnel

```text
search_jobs / GET /jobs  (limit ≤ 20)
  → rank / pick with the user
  → get_job_details / GET /jobs/:id   # shortlisted only
  → get_job_keywords                  # for resume/cover tailoring
```

Do not feed full job descriptions into document models — use keywords. See [references/filters.md](references/filters.md).

## Critical rules

- **Search is free within monthly quotas** (not billed per row). Still keep `limit` at 10–20 so you do not burn quota.
- **Matching is title/filter text** (substring / FTS), not vector embeddings.
- **List rows are snippets.** Never state requirements or salary from search results alone.
- **Opaque cursors only.** Max 50 per page. Paginate on user intent, not by default (~3 pages/conversation).
- **Closed jobs:** check `closed_at`. Open ≠ applicable.
- **Aggregates are free:** `GET /stats` / `get_market_overview` for counts and trends — do not page search to count.

## Endpoints and tools

| Goal | REST | MCP | Scope |
| --- | --- | --- | --- |
| Search | `GET /jobs` | `search_jobs` | `jobs:read` |
| Detail | `GET /jobs/:id` | `get_job_details` | `jobs:read` |
| Keywords | — | `get_job_keywords` | `jobs:read` |
| Market stats | `GET /stats` | `get_market_overview` | `jobs:read` |
| Map | `GET /jobs/map` | — | `jobs:read` |

Docs: [Search jobs](https://docs.worklittle.com/jobs/api/search-jobs) · [Job search assistant](https://docs.worklittle.com/use-cases/job-search-assistant) · [Pagination](https://docs.worklittle.com/use-cases/pagination-and-limits)
