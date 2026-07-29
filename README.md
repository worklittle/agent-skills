# Worklittle Agent Skills

[Agent skills](https://agentskills.io/home) that help coding agents build accurate integrations with the Worklittle Jobs API, Business ATS, and MCP.

## Install

From docs (recommended — always current with [docs.worklittle.com](https://docs.worklittle.com)):

```bash
npx skills add https://docs.worklittle.com
```

From this repo:

```bash
npx skills add worklittle/agent-skills
```

Update later:

```bash
npx skills update -y
```

## Skills

| Skill | Product | Use when |
| --- | --- | --- |
| `worklittle-best-practices` | Shared | Auth, scopes, billing, grounding, REST vs MCP |
| `worklittle-docs` | Shared | Docs / OpenAPI / agent manifest |
| `capability-map` | Shared | Goal → endpoint / tool / scope / skill |
| `mcp-install` | Shared | Connect MCP clients |
| `job-search` | Jobs | Search, pagination, details vs keywords |
| `market-stats` | Jobs | Free aggregates, salary averages |
| `job-alerts` | Jobs | API saved-search email |
| `apply-with-ai` | Jobs | Apply with AI, hosted apply |
| `resume-cover-letter` | Jobs | Resumes and cover letters |
| `people-search` | Jobs | Opt-in talent directory + unlocks |
| `post-a-job` | Business | Publish employer listings |
| `ats` | Business | Pipeline stages, notes, webhooks |
| `offers-and-employees` | Business | Offers, employees, hire completion |
| `email-outbound` | Business | Org ATS email send |

Machine-readable index on docs: [https://docs.worklittle.com/.well-known/skills/index.json](https://docs.worklittle.com/.well-known/skills/index.json)

## See also

- [Agent skills docs page](https://docs.worklittle.com/skills)
- [Worklittle MCP](https://docs.worklittle.com/jobs/mcp) — `https://mcp.worklittle.com`
- [API keys](https://worklittle.com/work/api-keys)
- [Capability map](https://docs.worklittle.com/use-cases/capability-map)

Canonical source of truth for the skill files lives in the Worklittle monorepo under `docs-ui/public/.well-known/skills/` and is published with docs deploys. This repository is the public GitHub mirror for `npx skills add worklittle/agent-skills`.

## License

MIT
