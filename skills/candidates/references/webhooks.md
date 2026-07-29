# Candidate and offer webhooks

## Event types (subscribe as needed)

| Type | When |
| --- | --- |
| `candidate.application_submitted` | New application on a posted job |
| `candidate.updated` | Candidate record changed |
| `candidate.deleted` | Candidate removed |
| `candidate.stage_changed` | Pipeline stage update |
| `candidate.note_created` | New note |
| `candidate.bookmarked` / `candidate.unbookmarked` | Bookmark toggles |
| `offer.created` / `offer.updated` / `offer.deleted` | Offers |

Or subscribe to `"*"` for all types.

## Management

| Action | REST | MCP |
| --- | --- | --- |
| Endpoints | `/webhooks` | `list_webhooks`, `create_webhook`, `update_webhook`, `delete_webhook` |
| Rotate secret | `POST /webhooks/:id/secret` | `rotate_webhook_secret` |
| Test | `POST /webhooks/:id/test` | `test_webhook` |
| Deliveries | `GET /webhook-deliveries` | `list_webhook_deliveries` |

Scope: `webhooks:manage`.

## Reliability

1. Verify signatures on every delivery
2. Ack fast; process async; dedupe by delivery id (at-least-once)
3. Hourly reconciliation against `GET /candidates` for missed events

Docs: [Webhooks](https://docs.worklittle.com/business/webhooks/overview) · [Integration](https://docs.worklittle.com/business/webhooks/integration) · [Reliability](https://docs.worklittle.com/use-cases/webhooks-reliability)
