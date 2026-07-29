# Candidate hiring email

Org ATS email for application / interview / offer / custom stages — **not** Jobs `/job-alerts` and **not** consumer Settings alerts.

| Action | REST | MCP | Notes |
| --- | --- | --- | --- |
| Templates | `/email-messages` CRUD | `set_email_messages`, `update_email_messages`, `delete_email_messages` | Free |
| Preview | `POST /email-messages/preview` | — | Free |
| Send / schedule | `POST /email/send` | `send_email` | Metered |
| Sent history | `GET /email/sends` | — | REST |

Scope: `jobs:applications`.

Confirm recipient, template, and body before every `send_email`. Treat sends as irreversible.
