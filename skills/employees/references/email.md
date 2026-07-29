# Employee / HR email

Same org send surface as candidate hiring email (`/email/send`, MCP `send_email`), scoped to employer communications.

| Action | REST | MCP | Notes |
| --- | --- | --- | --- |
| Templates | `/email-messages` | `set_email_messages`, … | Free; stage templates include offer/custom |
| Send | `POST /email/send` | `send_email` | Metered |
| History | `GET /email/sends` | — | REST |

Scope: `jobs:applications`.

Confirm before send. For interview/application stage templates, skill `candidates` is the primary guide; this skill covers post-hire follow-ups on the same API.
