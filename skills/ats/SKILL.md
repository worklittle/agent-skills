---
name: ats
description: >-
  Guides Worklittle Business ATS automation: candidate_job_id stage updates,
  notes, interviews, employees and offers, and webhook identity rules. Use when
  writing employer hiring-pipeline automation, moving candidates between stages,
  syncing an HRIS, or handling Business webhooks — not for market job apply or
  Apply with AI (use skill apply-with-ai).
---

Business product skill (your org's hiring workspace). For market Apply with AI / hosted apply, use skill `apply-with-ai`.

## Critical rules

- **ATS stage changes use `candidate_job_id`**, not `candidate_id`. Read the profile before writes.
- **Only report success after the tool/API returns OK.** Prefer tools over narrating fictional pipeline changes.
- **ATS applicants ≠ People Search profiles.** Your org's `/candidates` are not the same as `GET /people`.
- **Webhooks:** verify signatures, treat delivery as at-least-once, reconcile with a sweep when events may have been missed.

Details: [references/pipeline.md](references/pipeline.md) · [references/webhooks.md](references/webhooks.md)

## Scopes

| Action | Scope |
| --- | --- |
| Candidates, notes, stages, employees, offers | `jobs:applications` |
| Employer job listings | `jobs:post` |
| Webhooks CRUD / delivery | `webhooks:manage` |

Docs: [ATS automation](https://docs.worklittle.com/use-cases/ats-automation) · [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates) · [Webhooks](https://docs.worklittle.com/business/webhooks/overview) · [Prompting ATS agents](https://docs.worklittle.com/use-cases/prompting-ats)
