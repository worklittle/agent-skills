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

| Skill | Use when |
| --- | --- |
| `worklittle-best-practices` | Any Worklittle integration (auth, scopes, billing, grounding, REST vs MCP) |
| `worklittle-docs` | Looking up docs, OpenAPI, or the agent manifest |
| `job-search` | Searching jobs, pagination, details vs keywords, market stats |
| `apply-and-ats` | Hosted apply, Apply with AI, resumes/cover letters, ATS writes |

Machine-readable index on docs: [https://docs.worklittle.com/.well-known/skills/index.json](https://docs.worklittle.com/.well-known/skills/index.json)

## See also

- [Agent skills docs page](https://docs.worklittle.com/skills)
- [Worklittle MCP](https://docs.worklittle.com/jobs/mcp) — `https://mcp.worklittle.com`
- [API keys](https://worklittle.com/work/api-keys)
- [Capability map](https://docs.worklittle.com/use-cases/capability-map)

Canonical source of truth for the skill files lives in the Worklittle monorepo under `docs-ui/public/.well-known/skills/` and is published with docs deploys. This repository is the public GitHub mirror for `npx skills add worklittle/agent-skills`.

## License

MIT
