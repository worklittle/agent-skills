# Billing and rate limits

Default rate limit: **60 requests/min per key**. On `429`, honor `Retry-After` (often 60).

## Metered highlights

| Item | Rule |
| --- | --- |
| Job search | **$0.0015 per job in `data`** (not per HTTP request) |
| Job detail | $0.0015 per request |
| Salary average | $0.05 per request |
| Hosted apply | $0.01 per successful apply |
| Apply with AI | $0.15 per **started** session |
| People search | $0.05 per request |
| Resume unlock | $1.00 per unlock |
| `GET /stats` / market overview | **Free** |

Failed flat-fee calls are free. Token usage on AI document tools still bills.

## Agent spend rules

1. Cap search `limit` at 10–20 unless the user asks for more.
2. Paginate only on explicit user intent (max ~3 pages per conversation).
3. Never retry **402** (insufficient balance). Point the user to https://worklittle.com/work/billing.
4. Retrying a metered success path spends again — check idempotency (`/applied-jobs`, session status) before re-apply.
5. Prefer free `GET /stats` / `get_market_overview` for counts and trends instead of paging search results.
