---
name: market-stats
description: >-
  Guides free Worklittle market aggregates via GET /stats and get_market_overview,
  plus paid salary averages, and when not to paginate job search for counts. Use
  when answering how-many, trends, remote share, top companies, or compensation
  ranges — not when listing individual open roles (use skill job-search).
---

Jobs product skill for aggregate questions.

## Critical rules

- **`GET /stats` / `get_market_overview` is free** (`jobs:read`). Prefer it for counts and trends.
- **Never page `GET /jobs` / `search_jobs` to count.** Search bills per job in `data`.
- Stats = shape of the market. Search = which specific jobs to show the user.
- **`GET /jobs/salary-average`** is paid (~$0.05/request). Always report how many jobs went into the average when the API returns it.
- For individual roles, switch to skill `job-search`.

## Endpoints

| Goal | REST | MCP | Scope | Price |
| --- | --- | --- | --- | --- |
| Market overview | `GET /stats` | `get_market_overview` | `jobs:read` | Free |
| Salary average | `GET /jobs/salary-average` | — | `jobs:read` | Paid |
| Individual roles | `GET /jobs` | `search_jobs` | `jobs:read` | Per job in `data` |

Docs: [Alerts and market](https://docs.worklittle.com/use-cases/alerts-and-market) · [Search jobs](https://docs.worklittle.com/jobs/api/search-jobs) · [Capability map](https://docs.worklittle.com/use-cases/capability-map)
