---
name: apply-with-ai
description: >-
  Guides Worklittle Jobs apply flows: Apply with AI eligibility and session
  lifecycle, hosted apply via POST /jobs/:id/apply, closed_at vs
  can_apply, and grounded resume/cover letter generation. Use when
  applying to jobs, starting Apply with AI, checking can_apply, or
  generating application documents on the Jobs product.
---

Jobs product skill (market apply). For document-only work prefer skill `resume-cover-letter`. For employer ATS pipeline writes, use skill `candidates`.

## Two apply paths

| Path | When | Call | Cost cue |
| --- | --- | --- | --- |
| **Apply with AI** | Employer form automation (browser run) | `POST /jobs/apply` / `apply_for_job` | AI tokens + browser duration; no per-user concurrent cap — Waiting queue when browser slots are full; stops when credit runs out |
| **Hosted apply** | Worklittle-published job with application fields | `POST /jobs/:id/apply` / `submit_job_application` | ~$0.01 success |

Public careers boards: `POST /business/jobs/company/:company/jobs/:id/apply` — no API key, separate rate limit.

## Critical rules

- **`can_apply` is the only eligibility check** for Apply with AI. Never guess from `apply_url`, `source_name`, or the careers site host.
- **`closed_at` and `can_apply` are independent.** Re-read job details immediately before apply.
- **Documents are grounded.** Hiring-ready resumes/cover letters use only the candidate's real history + posting keywords. Omit unknowns; never invent employers, schools, or metrics.
- **Use `get_job_keywords` as `job_context`**, not the full job description.
- **Apply with AI lifecycle:** start → poll until `completed`. API keys always submit. Check `/jobs/applied` or session status before retrying to avoid double-submit. Each started session can bill — do not retry rejected starts blindly.

Details: [references/apply.md](references/apply.md) · [references/documents.md](references/documents.md)

## Scopes

| Action | Scope |
| --- | --- |
| Hosted apply / Apply with AI | `jobs:apply` (+ `jobs:read` for details) |
| Resumes / cover letters | `agent:tools` |

Docs: [Apply for jobs](https://docs.worklittle.com/jobs/api/apply-for-jobs) · [Apply with AI](https://docs.worklittle.com/use-cases/apply-with-ai) · [Closed jobs](https://docs.worklittle.com/use-cases/closed-jobs-and-eligibility) · [Resumes and cover letters](https://docs.worklittle.com/use-cases/resume-cover-letter)
