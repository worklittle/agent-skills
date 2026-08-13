---
name: people-search
description: >
  Public Worklittle People Search is temporarily unavailable (410 Gone).
  Reason: opt-in directory is still too small to ship publicly. Prefer skill
  candidates for employer ATS applicants. Use when a user asks about GET /people,
  search_people, or contact unlocks.
---

# People Search (temporarily unavailable)

Public **People Search** (`GET /people`, unlock routes, MCP `search_people`) is **off**.

**Why:** the opt-in recruiter directory does not have enough people yet to offer as a public product. Profiles still write on apply for a future launch.

**Flag:** `PEOPLE_SEARCH_ENABLED` on jobs-api + MCP (`"0"` = off). See `worklittle-jobs-api/README.md` § People Search.

- Calls return **410 Gone**
- There is no public metered People Search price while disabled
- For your own applicants and pipeline, use skill `candidates` and [Manage candidates](https://docs.worklittle.com/business/api/manage-candidates)

Do not invent contact data. Do not tell users People Search is live.
