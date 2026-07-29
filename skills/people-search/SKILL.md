---
name: people-search
description: >-
  Guides Worklittle People Search: GET /people discovery with has_* flags,
  metered REST contact and resume unlocks, and people:read scope. Use when
  sourcing opt-in candidates platform-wide, enriching outbound lists, or building
  recruiting agents — not for an employer's own ATS applicants (use skill candidates).
---

Jobs / platform directory skill. ATS `/candidates` is a different dataset (Business — skill `candidates`).

## Critical rules

- Only people who applied to a **Worklittle-hosted job** and **opted into recruiter discovery** appear.
- Search returns summaries and `has_email`, `has_linkedin`, etc. — **never contact values** until unlock.
- **Contact unlocks are REST-only** (`GET /people/:id/contact?field=`). MCP has `search_people` only.
- Unlock billing is **per successful unlock**; repeats for the same person+field charge again — cache values.
- Resume unlock (`GET /people/:id/resume`) returns processed text/HTML ($1.00/unlock), not raw uploads.
- Prefer small `limit` values for interactive agents (API allows up to 100).

## Endpoints

| Action | REST | MCP | Scope | Price cue |
| --- | --- | --- | --- | --- |
| Search | `GET /people` | `search_people` | `people:read` | ~$0.05/request |
| Unlock contact | `GET /people/:id/contact?field=` | — | `people:read` | ~$0.02–$0.25/field |
| Unlock resume | `GET /people/:id/resume` | — | `people:read` | ~$1.00/unlock |

Confirm before any unlock in agent loops. Details: [references/unlocks.md](references/unlocks.md).

Docs: [Search people](https://docs.worklittle.com/jobs/api/search-people) · [People Search](https://docs.worklittle.com/use-cases/people-search) · [Pricing](https://docs.worklittle.com/jobs/get-started/pricing)
