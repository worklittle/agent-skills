# API key scopes

Missing scope → **403**. Empty result sets are not a substitute for a missing scope.

## Jobs (market + candidate tools)

| Scope | Allows |
| --- | --- |
| `jobs:read` | `GET /jobs`, `GET /jobs/:id`, `GET /jobs/map`, `GET /stats` |
| `jobs:apply` | `POST /jobs/:id/apply`, Apply with AI, MCP `submit_job_application` |
| `people:read` | Reserved — public People Search temporarily unavailable |
| `agent:tools` | `POST /jobs/resumes`, `POST /jobs/cover-letters`, `POST /v1/agent/tool` |

## Business (employer workspace)

| Scope | Allows |
| --- | --- |
| `jobs:post` | `/business/jobs`, `/jobs/manage`, `/jobs/post/*` |
| `jobs:applications` | ATS (`/candidates`, `/employees`, `/offers`, `/attendance`, email, …) |
| `people:read` | Reserved — public People Search temporarily unavailable |
| `webhooks:manage` | `/webhooks` CRUD and delivery |
| `documents:read` / `documents:write` | `/platform/documents` |
| `employees:read` | Surveys and related employee-org reads |

## Typical scope sets

| Pattern | Scopes |
| --- | --- |
| Search and detail | `jobs:read` |
| Apply + Apply with AI | `jobs:read`, `jobs:apply` |
| Resumes / cover letters | `jobs:read`, `agent:tools` |
| ATS automation | `jobs:applications` (+ `jobs:post` if posting) |
| Webhooks | `webhooks:manage` |
