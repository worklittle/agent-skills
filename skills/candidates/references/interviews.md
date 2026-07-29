# Candidate interviews (calendar)

Interviews are scheduled on the **candidate** profile — the hiring calendar for pipeline work.

| Action | MCP |
| --- | --- |
| Schedule / record | `create_candidate_interview` |
| Update (time, status, notes) | `update_candidate_interview` |
| Delete | `delete_candidate_interview` |
| Interview Q&A answers | `create_interview_answer`, `update_interview_answer`, `delete_interview_answer` |

Scope: `jobs:applications`.

Confirm time/timezone and candidate identity with the user before creating or moving interviews. After writes, only claim success when the tool returns OK.
