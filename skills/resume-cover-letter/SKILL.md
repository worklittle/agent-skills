---
name: resume-cover-letter
description: >-
  Guides Worklittle resume and cover letter generation: hiring-ready vs draft
  modes, get_job_keywords as job_context, output formats, and attach-to-apply
  fields. Use when tailoring documents to a job_id or building apply pipelines —
  not for Apply with AI browser sessions (use skill apply-with-ai) or ATS writes
  (use skill ats).
---

Jobs document skill. For full apply session lifecycle, also load `apply-with-ai`.

## Critical rules

- Scope **`agent:tools`** (plus `jobs:read` for details/keywords).
- **Hiring-ready never invents** employers, schools, or metrics — omit unknowns.
- **Draft** endpoints may leave bracketed gaps when input is thin.
- Use **`get_job_keywords` as `job_context`**, not the full job description.
- Default outputs include HTML/PDF in a JSON envelope (`pdf_base64`), not raw PDF bytes alone.
- Attach with the correct apply fields (`resume_file`, `cover_letter` / `cover_letter_file`) — swapping slots fails silently.

## Canonical chain

```text
get_job_details → get_job_keywords → create_resume / create_cover_letter
```

## Endpoints

| Goal | REST | MCP | Scope |
| --- | --- | --- | --- |
| Resume | `POST /v1/resumes` | `create_resume` | `agent:tools` |
| Cover letter | `POST /v1/cover-letters` | `create_cover_letter` | `agent:tools` |
| Draft resume | `POST /v1/draft-resumes` | `create_draft_resume` | `agent:tools` |
| Draft cover letter | `POST /v1/draft-cover-letters` | `create_draft_cover_letter` | `agent:tools` |
| Keywords | — | `get_job_keywords` | `jobs:read` |

Docs: [Resumes and cover letters](https://docs.worklittle.com/use-cases/resume-cover-letter) · [Create resumes](https://docs.worklittle.com/jobs/api/create-resumes) · [Create cover letters](https://docs.worklittle.com/jobs/api/create-cover-letters) · [Structured extraction](https://docs.worklittle.com/use-cases/structured-extraction)
