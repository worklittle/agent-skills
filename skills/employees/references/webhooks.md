# Employee-related webhooks

There is no dedicated `employee.*` event catalog in docs today. For hire/roster sync:

1. Watch **`offer.*`** and **`candidate.stage_changed`** (hire stages) via skill `candidates` webhooks, then call `create_employee` / employment period APIs.
2. Watch **organization membership** for who can access the Work app:

| Type | When |
| --- | --- |
| `organization.member_joined` | Someone joined the organization |
| `organization.member_role_changed` | Role changed |
| `organization.member_left` | Left or removed |

## Management (same as candidates)

| Action | REST | MCP |
| --- | --- | --- |
| Endpoints | `/webhooks` | `create_webhook`, `list_webhooks`, … |
| Deliveries | `/webhook-deliveries` | `list_webhook_deliveries` |

Scope: `webhooks:manage`. Verify signatures; at-least-once; reconcile with `list_employees` / `/attendance` on a schedule.

Docs: [Webhooks overview](https://docs.worklittle.com/business/webhooks/overview) · [Reliability](https://docs.worklittle.com/use-cases/webhooks-reliability)
