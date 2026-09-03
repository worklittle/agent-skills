# Apply paths (Jobs)

## Before any apply

1. `get_job_details` / `GET /jobs/:id`
2. Confirm `closed_at` is null/absent
3. For Apply with AI: confirm `can_apply === true`
4. Ensure a resume exists when the form requires one
5. Confirm with the user before spending (especially Apply with AI sessions)

## Apply with AI

1. Eligibility flag only — do not guess from `apply_url`, `source_name`, or the careers site host
2. `apply_for_job` / `POST /jobs/apply` → keep `session_id`
3. Poll `get_apply_status` / `GET /jobs/apply/:id` — read `status` and `form_progress`
4. Treat only `status: "completed"` as submitted success. Other statuses: `queued`, `running`, `awaiting_input`, `paused`, `failed`, `cancelled`, `stopped`
5. API keys always submit. Do not wait for a separate approve-submit step
6. Do not retry a rejected **start** blindly — check spend (`CONSUMER_*_SPEND_LIMIT`) and `BROWSER_CAPACITY`. Per-user concurrent caps are gone; when global browser slots are full the session is `queued` (Waiting) until a slot frees.

## Hosted apply

1. Read `application_fields` from job details
2. Map candidate profile + resume to fields (no invented facts)
3. `POST /jobs/:id/apply` or MCP `submit_job_application`
4. Scope: `jobs:apply`

## Public board apply

`POST /business/jobs/company/:company/jobs/:id/apply` — no API key, free, IP rate limited. Separate from metered hosted apply.
