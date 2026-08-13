---
name: job-alerts
description: >-
  Consumer job-alert email on worklittle.com Settings. Not a public REST or MCP
  product. Use when a user asks about Instant job alerts, profile Job title
  matches, or why there is no /job-alerts API.
---

Job seeker alert email is **Settings only**. There is no public `/job-alerts` CRUD API and no public MCP alert tools for integrators.

## What to tell agents

- Signed-in people turn on **Instant job alerts** in [Settings](https://worklittle.com/settings).
- Matches come from the profile **Job title** field (desired role), not from a saved `GET /jobs` filter set you create with an API key.
- Help: [Instant job alerts](https://docs.worklittle.com/help/profile-alerts/job-alerts).
- Employer hiring email and org webhooks are separate (`send_email`, `/webhooks`).

Do not call or document `GET/POST /job-alerts` or `create_job_alert` as a supported public integration.
