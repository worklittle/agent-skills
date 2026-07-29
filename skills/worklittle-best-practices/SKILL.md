---
name: worklittle-best-practices
description: >-
  Guides Worklittle integration decisions across REST vs MCP vs SDK/CLI, API key
  scopes, per-job search billing, rate limits and 402 handling, grounding answers
  in API data, and never inventing job_id or candidate IDs. Use when building,
  modifying, or reviewing any Worklittle integration, including job search,
  apply automation, resumes, ATS, People Search, webhooks, or MCP tools.
---

Base URLs:

| Surface | URL |
| --- | --- |
| REST | `https://api.worklittle.com` |
| MCP | `https://mcp.worklittle.com` |
| Docs | `https://docs.worklittle.com` |

Auth: Bearer `sk-wl-api01-...` from [API keys](https://worklittle.com/work/api-keys). One key works for REST and MCP. Missing scope returns **403**, not empty data.

## Integration routing

| Building… | Prefer | Details |
| --- | --- | --- |
| Unsure which endpoint / product | Router | skill `capability-map` |
| Connect Cursor / Claude / VS Code | MCP install | skill `mcp-install` |
| Agent in Cursor / Claude / ChatGPT with tools | MCP | [references/transport.md](references/transport.md) |
| Backend, scripts, high-volume loops | REST or SDK/CLI | [references/transport.md](references/transport.md) |
| Job discovery | `GET /jobs` / `search_jobs` | skill `job-search` |
| Counts / trends / salary averages | `GET /stats` | skill `market-stats` |
| API saved-search email | `/job-alerts` | skill `job-alerts` |
| Apply with AI or hosted apply | Jobs apply APIs | skill `apply-with-ai` |
| Resumes / cover letters | Document APIs | skill `resume-cover-letter` |
| Opt-in talent directory | `GET /people` | skill `people-search` |
| Publish employer listings | `/job-listings` | skill `post-a-job` |
| Candidates (stages, interviews, offers, email, webhooks) | Business `/candidates` | skill `candidates` |
| Employees (roster, attendance calendar, email, webhooks) | Business `/employees` | skill `employees` |
| Docs lookup | docs discovery | skill `worklittle-docs` |

Read the relevant reference (and the matching skill) before writing code or answering integration questions.

## Critical rules

- **Never invent IDs.** `job_id`, `candidate_id`, `candidate_job_id`, and `session_id` must come from a prior API response stored in application state. Quote them; do not reconstruct them.
- **Search bills per job in `data`**, not per HTTP request. Default `limit` to 10–20. Do not use `limit=50` to "save round trips."
- **List rows are thin.** Never summarize requirements, salary, or qualifications from search results. Call `get_job_details` / `GET /jobs/:id` for shortlisted roles only.
- **Ground every claim.** Salary, location, company, and requirements come from API fields. If a field is missing, say so. Do not invent.
- **Enforce spend and confirmations in code**, not only in prompts: cap `limit`, gate metered unlocks, require user confirm before apply / contact unlock.
- **402 means add balance** at [Billing](https://worklittle.com/work/billing). Never retry a 402. Metered retries spend money.
- **Rate limit** is 60 req/min/key by default (`429` + `Retry-After`).

## Scopes

| Scope | Allows |
| --- | --- |
| `jobs:read` | `GET /jobs`, `GET /jobs/:id`, `GET /jobs/map`, `GET /stats` |
| `jobs:apply` | Hosted apply, Apply with AI |
| `agent:tools` | Resumes, cover letters, agent tools |
| `people:read` | People Search + unlocks |
| `jobs:post` | Employer listings |
| `jobs:applications` | ATS candidates, employees, offers, email |
| `webhooks:manage` | Webhooks CRUD |
| `documents:read` / `documents:write` | HR documents |
| `employees:read` | Surveys and related org reads |

Full tables: [references/scopes.md](references/scopes.md). Billing notes: [references/billing.md](references/billing.md).

## Key documentation

- [Capability map](https://docs.worklittle.com/use-cases/capability-map) — goal → endpoint / MCP tool / scope
- [Tool chains](https://docs.worklittle.com/use-cases/tool-chains) — call order that works
- [Grounding](https://docs.worklittle.com/use-cases/grounding) — never invent job facts
- [REST vs MCP](https://docs.worklittle.com/use-cases/rest-vs-mcp)
- [MCP guide](https://docs.worklittle.com/jobs/mcp)
- [Agent skills index](https://docs.worklittle.com/.well-known/skills/index.json)
