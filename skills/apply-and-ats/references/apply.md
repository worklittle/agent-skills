# Apply paths

## Before any apply

1. `get_job_details` / `GET /jobs/:id`
2. Confirm `closed_at` is null/absent
3. For Apply with AI: confirm `apply_with_ai_eligible === true`
4. Ensure a resume exists when the form requires one
5. Confirm with the user before spending (especially Apply with AI sessions)

## Hosted apply

1. Read `application_fields` from job details
2. Map candidate profile + resume to fields (no invented facts)
3. `POST /jobs/:id/apply` or MCP `submit_job_application`
4. Scope: `jobs:apply`

## Apply with AI

1. Eligibility flag only — no ATS URL heuristics
2. `start_apply_with_ai` / `POST /v1/apply-with-ai` → keep `session_id`
3. Poll `get_apply_session`
4. Handle human-in-the-loop via `continue_apply` / `live_view_url`
5. If `auto_submit: false`, call `approve_apply_submit` after user approval
6. Do not retry a rejected **start** blindly — each start can bill

## Documents

```text
get_job_details → get_job_keywords → create_resume / create_cover_letter
```

- Inputs: candidate resume/profile text + `job_id` + keywords as `job_context`
- Hiring-ready mode omits gaps; draft mode may leave bracketed placeholders
- Attach generated docs to hosted apply when the API accepts them
