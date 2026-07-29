# ATS pipeline (Business)

## Identifiers

| ID | Meaning |
| --- | --- |
| `candidate_id` | Person in your org ATS |
| `candidate_job_id` | That person on a **specific** job (use for stage moves) |
| listing / job id | The role you posted |

One external apply can create related rows. They are not interchangeable with People Search profiles.

## Write safety

1. List/get the candidate (and application) before mutating
2. Stage / note / interview updates target the correct `candidate_job_id`
3. Never tell the user a write succeeded unless the API/MCP tool returned success
4. Confirm identity with the user before bulk or irreversible stage changes

## Typical tools / routes

- List / update candidates: `/candidates`, MCP `list_candidates` / `update_candidates`
- Notes, interviews, offers, employees under Business ATS routes
- Scope: `jobs:applications` (add `jobs:post` when creating listings)

See [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates) and [Prompting ATS agents](https://docs.worklittle.com/use-cases/prompting-ats).
