# Billing and rate limits

Default rate limit: **60 requests/min per key**. On per-minute `429` with `RATE_LIMITED`, honor `Retry-After` (often 60). Those 429s, plus `UNAUTHORIZED`, `FORBIDDEN`, and `PAYMENT_REQUIRED`, include `error.documentation_url` — fetch that Help page before guessing.

Monthly free quotas return `429` with code **`QUOTA_EXCEEDED`** (no Retry-After). Tell the user to email **business@worklittle.com** for higher limits. Do not busy-retry.

## Who pays what

| Surface | Free | Then |
| --- | --- | --- |
| API / MCP (API key) | Quotas below + cached job AI | Org wallet **AI tokens only** |
| Consumer guest | **$0.15/month** provider (local calendar; no daily) | Hard stop `CONSUMER_MONTHLY_SPEND_LIMIT` → login modal (“Log in for higher usage”) |
| Consumer signed-in, no Instant | Personal monthly free **billed** credit **$0.50** (or **$0.10** if not first create on device); no daily hard stop | Then Personal PAYG if card; else monthly hard stop → `/plans` |
| Consumer Instant ($9.99/mo) | **$20/mo** plan credit per local calendar month (cancel→renew same month does not refresh; bonus/referral first; no free $0.50) | Then Personal org PAYG at token rates |
| Personal-org API | Same Personal free / Instant credit | Then org wallet PAYG |

## Paid (API / org wallet)

The only paid meter is **AI tokens**: **$2.50 / 1M input**, **$15.00 / 1M output** (documents, agent tools, Apply with AI tokens, platform AI chat, and job-detail AI generations after the free 100/day).

Public People Search is temporarily disabled (410). Do not quote People Search prices.

## Free quotas (UTC)

| Item | Quota |
| --- | --- |
| Job search | **1000** jobs returned / month |
| Job detail (raw / cached AI) | **Free** — raw `description_text` and already-persisted AI fields never bill |
| Job detail AI generation | **100** free first-time AI enrichments/org/**UTC day**, then token rates (not a hard deny) |
| Salary average | **1000** requests / month |
| Company map | **1000** requests / month |
| Company search | **1000** companies returned / month |
| Custom columns (structured / sandbox JS / hybrid) | **1000** rows/org / month each |
| Sandbox Python | **1000** jobs/org / month |
| Platform / ATS email | **100** messages/org / month |

Docs: [Jobs pricing](https://docs.worklittle.com/jobs/get-started/pricing) · [Business pricing](https://docs.worklittle.com/business/get-started/pricing) · [Jobs rate limits](https://docs.worklittle.com/jobs/resources/rate-limits) · [Business rate limits](https://docs.worklittle.com/business/resources/rate-limits)
