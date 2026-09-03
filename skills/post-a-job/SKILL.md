---
name: post-a-job
description: >-
  Guides Worklittle Business job publishing: /business/jobs and MCP listing tools,
  jobs:post scope, required fields, and public_job_id for apply routes. Use when
  automating Worklittle-hosted postings or careers boards — not for market job
  search (job-search) or candidate pipeline management (candidates).
---

Business product skill for employer listings.

## Critical rules

- **`jobs:read` cannot post.** Need **`jobs:post`** for `/business/jobs`, `/jobs/manage`, and MCP listing tools.
- Required on create: `title`, description (`description` / `description_raw`), `employment_type`, `workplace_type`; **location required when not fully remote**.
- Posted jobs appear on **`GET /business/jobs/company/:company/*`**; use the listing’s **`public_job_id`** for apply routes.
- Configure **`application_fields`** when candidates will apply on Worklittle.
- Listing CRUD is typically free with a valid key; still confirm scopes before debugging empty errors (403 ≠ empty list).

## Endpoints

| Surface | Routes / tools | Scope |
| --- | --- | --- |
| REST | `/business/jobs`, `/jobs/manage` | `jobs:post` |
| MCP | `create_job_listing`, `list_posted_jobs`, `update_job_listing`, `delete_job_listing` | `jobs:post` |
| Public board | `GET /business/jobs/company/:company/...` | None (public) |

Docs: [Post a job](https://docs.worklittle.com/business/api/post-a-job) · [Embedded job board](https://docs.worklittle.com/use-cases/embedded-job-board) · [Apply for jobs](https://docs.worklittle.com/jobs/api/apply-for-jobs)
