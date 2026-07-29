---
name: candidates
description: >-
  Guides Worklittle Business candidate ATS work: list/profile/stage updates with
  candidate_job_id, notes, interview calendar, offers, org hiring email, and
  candidate/offer webhooks. Use when automating recruiting pipelines, scheduling
  interviews, sending candidate email, or syncing applications — not for hired
  employees (use skill employees) or market apply (apply-with-ai).
---

Business skill for **pre-hire** people in your org ATS. After hire, use skill `employees`.

## Critical rules

- Scope **`jobs:applications`** for candidates/notes/interviews/offers/email. Webhooks need **`webhooks:manage`**.
- **Stage moves use `candidate_job_id`**, not bare `candidate_id`.
- **ATS candidates ≠ People Search** (`GET /people`). Your applicants are `/candidates` only.
- Read `get_candidate_profile` / list before writes. Only report success after the API/MCP returns OK.
- **Interviews** are the candidate calendar surface (`create_candidate_interview`, etc.).
- **Email** (`/email/send`, `send_email`) is metered and irreversible — confirm before send. Not the same as Jobs `/job-alerts`.
- **Webhooks:** prefer event-driven sync + hourly reconciliation. Verify signatures; at-least-once delivery.

## Surface map

| Area | Details |
| --- | --- |
| Pipeline / profile | [references/pipeline.md](references/pipeline.md) |
| Interviews (calendar) | [references/interviews.md](references/interviews.md) |
| Offers | [references/offers.md](references/offers.md) |
| Hiring email | [references/email.md](references/email.md) |
| Webhooks | [references/webhooks.md](references/webhooks.md) |

Docs: [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates) · [ATS automation](https://docs.worklittle.com/use-cases/ats-automation) · [Webhooks](https://docs.worklittle.com/business/webhooks/overview) · [Prompting ATS](https://docs.worklittle.com/use-cases/prompting-ats)
