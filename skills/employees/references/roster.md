# Employee roster

| Action | REST | MCP |
| --- | --- | --- |
| List | `/employees` | `list_employees` |
| Create / convert from candidate | `/employees` | `create_employee` |
| Update | `/employees` | `update_employee` |
| Delete | `/employees` | `delete_employee` |
| Add employment period | `/employee-employment-periods` | `create_employee_employment_period` |
| Update period | — | `update_employee_employment_period` |
| Delete period | — | `delete_employee_employment_period` |
| Performance feedback | — | `set_employee_performance_feedback`, `delete_employee_performance_feedback` |

Scope: `jobs:applications`.

`create_employee_employment_period` requires `employee_id` and `start_date`. Example department: Engineering. When closing: `end_reason` in `resigned`, `terminated`, `laid_off`, `retired`, `contract_ended`, `other`.
