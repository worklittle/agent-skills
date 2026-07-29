---
name: job-alerts
description: >-
  Guides Worklittle API job-alert CRUD on /job-alerts and MCP alert tools: saved
  search filters, batched email sends, and developer-key billing. Use when building
  saved-search email products with API keys — not consumer profile alerts on
  worklittle.com, and not employer ATS outbound email (use skill candidates or
  employees).
---

Jobs API skill for saved-search email. Separate from Business `send_email` and from consumer Settings job alerts.

## Critical rules

- Alerts are **account-scoped saved filter sets** that reuse **`GET /jobs` filter vocabulary**.
- Sends are **batched**, not one email per matching job.
- API-created alert sends are **metered** when matches meet the send threshold — confirm spend assumptions before creating many alerts.
- Scope: **`jobs:read`** for alert CRUD.
- Do not confuse with org hiring email (`email-outbound`) or webhooks.

## Endpoints

| Method | Path | MCP |
| --- | --- | --- |
| GET | `/job-alerts` | `list_job_alerts` |
| POST | `/job-alerts` | `create_job_alert` |
| PATCH | `/job-alerts/:id` | `update_job_alert` |
| DELETE | `/job-alerts/:id` | `delete_job_alert` |

Docs: [Alerts and market](https://docs.worklittle.com/use-cases/alerts-and-market) · [Search jobs](https://docs.worklittle.com/jobs/api/search-jobs) · [Pricing](https://docs.worklittle.com/jobs/get-started/pricing)
