# ATS and webhooks

## Identifiers

| ID | Meaning |
| --- | --- |
| `candidate_id` | Person in your org ATS |
| `candidate_job_id` | That person on a **specific** job (use for stage moves) |
| `job_id` / listing id | The role |

One apply can create related rows. ATS applicants ≠ People Search profiles.

## Write safety

1. List/get the candidate (and application) before mutating
2. Stage / note / interview updates target the correct `candidate_job_id`
3. Never tell the user a write succeeded unless the API/MCP tool returned success
4. Prefer tools over narrating fictional pipeline changes

## Webhooks

- Verify signatures
- Treat delivery as at-least-once (idempotency keys)
- Reconcile with a sweep when events may have been missed
- Scope: `webhooks:manage`

See [Webhooks reliability](https://docs.worklittle.com/use-cases/webhooks-reliability) and [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates).
