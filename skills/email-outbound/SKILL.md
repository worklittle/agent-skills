---
name: email-outbound
description: >-
  Guides Worklittle Business ATS outbound email: templates on /email-messages,
  metered POST /email/send, and GET /email/sends history. Use when automating
  stage or offer email from employer integrations — not API job-alert emails
  (skill job-alerts) or consumer Settings alerts on worklittle.com.
---

Business org email skill. Distinct from Jobs `/job-alerts`.

## Critical rules

- Templates/preview on **`/email-messages`** are free; **`POST /email/send`** / MCP `send_email` is **metered**.
- Scope: **`jobs:applications`**.
- Treat send as **irreversible** — confirm recipient and body before calling send.
- Sent history: **`GET /email/sends`** (REST; list may not have an MCP twin).
- Do not use this skill for consumer job-alert product behavior.

## Endpoints

| Action | REST | MCP | Scope |
| --- | --- | --- | --- |
| Templates | `/email-messages` CRUD | `set_email_messages`, `update_email_messages`, `delete_email_messages` | `jobs:applications` |
| Preview | `POST /email-messages/preview` | — | `jobs:applications` |
| Send | `POST /email/send` | `send_email` | `jobs:applications` |
| History | `GET /email/sends` | — | `jobs:applications` |

Docs: [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates) · [ATS automation](https://docs.worklittle.com/use-cases/ats-automation) · [Pricing](https://docs.worklittle.com/jobs/get-started/pricing)
