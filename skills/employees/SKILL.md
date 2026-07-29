---
name: employees
description: >-
  Guides Worklittle Business employee roster work: create/update employees and
  employment periods, performance feedback, org attendance calendar, hiring-team
  email, and organization member webhooks. Use when automating hire conversion,
  HRIS employee sync, PTO/calendar, or post-hire roster management — not for
  pre-hire pipeline (use skill candidates) or People Search (people-search).
---

Business skill for **hired** people. Pre-hire pipeline, interviews, and offers → skill `candidates`.

## Critical rules

- Scope **`jobs:applications`** for employees. Attendance uses the same org auth; webhooks need **`webhooks:manage`**.
- `create_employee` can **convert a candidate into an employee**. Deleting an employee may restore the linked candidate.
- Employment periods need `employee_id` + `start_date`; set `end_reason` when closing a stint.
- **Attendance is the org calendar API** (`/attendance` — there is no `/calendar` prefix). Same data as the Work calendar UI.
- Org email (`send_email`) is metered — confirm before send. Prefer skill `candidates` for interview/offer stage templates; use this skill for employee/HR follow-ups on the same send surface.
- Only report writes after the API/MCP returns OK. Confirm identity before hire conversion or deletes.

## Surface map

| Area | Details |
| --- | --- |
| Roster / periods / feedback | [references/roster.md](references/roster.md) |
| Attendance (calendar) | [references/attendance.md](references/attendance.md) |
| Email | [references/email.md](references/email.md) |
| Webhooks | [references/webhooks.md](references/webhooks.md) |

Docs: [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates) · [Attendance](https://docs.worklittle.com/business/api/attendance) · [ATS automation](https://docs.worklittle.com/use-cases/ats-automation) · [Org ops](https://docs.worklittle.com/use-cases/org-ops) · [Webhooks](https://docs.worklittle.com/business/webhooks/overview)
