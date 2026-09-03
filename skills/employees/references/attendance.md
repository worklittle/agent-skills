# Attendance (org calendar)

Attendance is the calendar API. There is **no** `/calendar` prefix. Same data as the Work calendar UI.

| Method | Path | Purpose |
| --- | --- | --- |
| GET | `/business/attendance` | Org calendar entries |
| POST | `/business/attendance` | Create (e.g. PTO) |
| GET | `/business/employees/:id/attendance` | Entries for one employee |
| GET | `/attendance/avatars` | Avatar bundle for calendar UI |
| PATCH | `/attendance/:id` | Update |
| DELETE | `/attendance/:id` | Delete |
| POST | `/attendance/:id/pending/approve` | Approve pending edit |
| POST | `/attendance/:id/pending/deny` | Deny pending edit |

Org role gates still apply — **403** means the key is valid but the member cannot access attendance for that org.

Example create body fields: `employee_id`, `start_date`, `end_date`, `type` (e.g. `pto`).

Docs: [Attendance](https://docs.worklittle.com/business/api/attendance)
