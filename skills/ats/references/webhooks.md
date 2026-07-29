# Business webhooks

- Verify signatures on every delivery
- Treat delivery as at-least-once (idempotency keys)
- Assume any event can arrive twice or fail to arrive — design a reconciliation sweep
- Scope: `webhooks:manage`

See [Webhooks reliability](https://docs.worklittle.com/use-cases/webhooks-reliability) and [Webhook integration](https://docs.worklittle.com/business/webhooks/integration).
