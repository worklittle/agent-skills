---
name: capability-map
description: >-
  Routes a Worklittle product goal to the correct REST endpoint, MCP tool, scope,
  docs page, and agent skill. Use when the user knows what they want to build but
  not which API to call, or when disambiguating Jobs vs Business vs People Search.
---

Read this first when choosing an integration path. Full tables live in docs; this skill is the router.

## Product boundary

| Question | Product | Start skill |
| --- | --- | --- |
| Market-wide open roles? | Jobs | `job-search` |
| Counts / trends / salary averages? | Jobs | `market-stats` |
| Apply with AI / hosted apply? | Jobs | `apply-with-ai` |
| Resumes / cover letters? | Jobs | `resume-cover-letter` |
| Saved-search email via API? | Jobs | `job-alerts` |
| Opt-in talent directory? | Jobs (People) | `people-search` |
| Publish employer listings? | Business | `post-a-job` |
| Pipeline, interviews, offers, candidate email/webhooks? | Business | `candidates` |
| Employees, attendance calendar, post-hire email/webhooks? | Business | `employees` |
| Install MCP client? | Shared | `mcp-install` |
| Lookup docs / OpenAPI? | Shared | `worklittle-docs` |

## Billing anchor

Job search bills **per job in `data`**, not per HTTP request. Aggregates → `market-stats`. Individual roles → `job-search`.

## REST-only gaps (no MCP)

- People contact unlock: `GET /people/:id/contact`
- Public board apply: `POST /job-boards/:company/jobs/:id/apply`

## Docs

- [Capability map](https://docs.worklittle.com/use-cases/capability-map) — full Goal → REST → MCP → Scope tables
- [Tool chains](https://docs.worklittle.com/use-cases/tool-chains)
- [Agent skills](https://docs.worklittle.com/skills)
