# Job search filters

## Query vs filters

- Role / title text goes in `query` (and optional keywords). Title matching is substring on **title**, not company names in the same field.
- Preserve negative title terms with a leading dash, e.g. `software engineer, -senior` or `-Senior` in title filters.
- Recency → `posted_within_days` (not stuffed into `q`).
- Location, job type, seniority, remote/hybrid → dedicated filter params (see Search jobs docs).

## What not to do

| Mistake | Do this instead |
| --- | --- |
| `limit=50` to reduce round trips | Use `limit=10–20`; detail only shortlisted rows |
| Summarize JD from list row | `get_job_details` |
| Paste full description into resume prompt | `get_job_keywords` as `job_context` |
| Page search to answer "how many remote X" | `GET /stats` / `get_market_overview` |
| Put company name in title query | Use company filter / company search |

## Pagination

- Follow the opaque `cursor` from the previous response.
- Stop when the user has enough results or after ~3 pages unless they ask for more.
