# People Search unlocks

## Contact fields

`GET /people/:id/contact?field=<name>`

Typical fields: `email`, `work_email`, `phone`, `linkedin`, `github`, `website`, `x` (and similar presence flags from search).

- Confirm with the user before spending
- Cache unlocked values — repeat unlocks bill again
- No MCP equivalent; use REST with Bearer key

## Resume

`GET /people/:id/resume` — processed resume text/HTML for the profile.

## vs ATS

| | People Search | ATS `/candidates` |
| --- | --- | --- |
| Scope | Platform opt-in directory | Your org only |
| Skill | `people-search` | `candidates` |
| Unlock contact | Yes (REST) | Use candidate profile fields |
