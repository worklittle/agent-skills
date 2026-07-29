---
name: offers-and-employees
description: >-
  Guides Worklittle Business hire completion: offers CRUD, employee records,
  employment periods, and candidate_job_id stage moves into hire. Use when
  automating offers, HRIS hire sync, or post-offer roster management — not for
  market apply (apply-with-ai) or People Search (people-search).
---

Business skill focused on the hire side of ATS. For stages/notes/interviews broadly, also see skill `ats`.

## Critical rules

- Scope **`jobs:applications`**. Organization-scoped only.
- **Stage / hire links use `candidate_job_id`**, not bare `candidate_id`.
- **ATS applicants ≠ People Search profiles.**
- Only report offer/employee writes after the API/MCP tool returns success.
- Confirm identity before creating offers or employees in agent loops.

## Endpoints

| Area | REST | MCP | Scope |
| --- | --- | --- | --- |
| Offers | `/offers` | `create_offer`, `update_offer`, `delete_offer` | `jobs:applications` |
| Employees | `/employees`, `/employee-employment-periods` | `list_employees`, `create_employee`, `create_employee_employment_period` | `jobs:applications` |
| Candidates | `/candidates` | `list_candidates`, `update_candidates` | `jobs:applications` |

Docs: [ATS automation](https://docs.worklittle.com/use-cases/ats-automation) · [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates) · [Prompting ATS agents](https://docs.worklittle.com/use-cases/prompting-ats)
