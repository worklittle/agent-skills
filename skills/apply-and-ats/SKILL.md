---
name: apply-and-ats
description: >-
  Guides Worklittle apply flows and employer ATS: hosted apply vs Apply with AI
  eligibility, closed_at vs apply_with_ai_eligible, resume and cover letter
  grounding, candidate_job_id stage updates, and webhook identity rules. Use when
  applying to jobs, starting Apply with AI, generating application documents, or
  writing ATS candidate pipeline automation.
---

## Two apply paths

| Path | When | Call | Cost cue |
| --- | --- | --- | --- |
| **Hosted apply** | Worklittle-published job with application fields | `POST /jobs/:id/apply` / `submit_job_application` | ~$0.01 success |
| **Apply with AI** | Employer form automation (browser run) | `POST /v1/apply-with-ai` / `start_apply_with_ai` | ~$0.15 per started session |

Public careers boards: `POST /job-boards/:company/jobs/:id/apply` — no API key, separate rate limit.

## Critical rules

- **`apply_with_ai_eligible` is the only eligibility check** for Apply with AI. Never sniff Greenhouse/Ashby URLs or `source_name`.
- **`closed_at` and `apply_with_ai_eligible` are independent.** Re-read job details immediately before apply.
- **Documents are grounded.** Hiring-ready resumes/cover letters use only the candidate's real history + posting keywords. Omit unknowns; never invent employers, schools, or metrics.
- **Use `get_job_keywords` as `job_context`**, not the full job description.
- **ATS stage changes use `candidate_job_id`**, not `candidate_id`. Read the profile before writes. Only report success after the tool/API returns OK.
- **Apply with AI lifecycle:** start → poll session → `continue_apply` / live view → `approve_apply_submit` when `auto_submit` is false. Check `/applied-jobs` or session status before retrying to avoid double-submit.

Details: [references/apply.md](references/apply.md) · [references/ats.md](references/ats.md)

## Scopes

| Action | Scope |
| --- | --- |
| Hosted apply / Apply with AI | `jobs:apply` (+ `jobs:read` for details) |
| Resumes / cover letters | `agent:tools` |
| ATS candidates / notes / stages | `jobs:applications` |

Docs: [Apply for jobs](https://docs.worklittle.com/jobs/api/apply-for-jobs) · [Apply with AI](https://docs.worklittle.com/use-cases/apply-with-ai) · [ATS automation](https://docs.worklittle.com/use-cases/ats-automation) · [Closed jobs](https://docs.worklittle.com/use-cases/closed-jobs-and-eligibility)
