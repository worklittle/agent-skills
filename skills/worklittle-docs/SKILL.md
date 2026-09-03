---
name: worklittle-docs
description: >-
  Use when the user or agent needs to read, search, or look up Worklittle
  documentation or API reference. Prefer docs discovery URLs over guessing
  endpoints, scopes, or MCP tool names.
---

Prefer fetching Worklittle docs over inventing API shapes.

## Discovery order

1. **Index** — [https://docs.worklittle.com/llms.txt](https://docs.worklittle.com/llms.txt)
2. **Agent manifest** — [https://docs.worklittle.com/docs-agent-manifest.json](https://docs.worklittle.com/docs-agent-manifest.json) (paths, titles, descriptions, nav, learning paths). Does not include full page bodies.
3. **Page as Markdown** — request a docs URL with `Accept: text/markdown`, or append `.md` (e.g. `https://docs.worklittle.com/jobs/api/search-jobs.md`)
4. **OpenAPI** — [https://docs.worklittle.com/openapi/openapi.yaml](https://docs.worklittle.com/openapi/openapi.yaml)
5. **Agent skills index** — [https://docs.worklittle.com/.well-known/skills/index.json](https://docs.worklittle.com/.well-known/skills/index.json)

## Start here by goal

| Goal | Page |
| --- | --- |
| Agent onboarding | [Agent Quickstart skill](https://docs.worklittle.com/agent-onboarding/SKILL.md) ([human page](https://docs.worklittle.com/use-cases/agent-quickstart)) |
| Goal → endpoint / tool / scope | [Capability map](https://docs.worklittle.com/use-cases/capability-map) |
| Call sequences | [Tool chains](https://docs.worklittle.com/use-cases/tool-chains) |
| Job search filters | [Search jobs](https://docs.worklittle.com/jobs/api/search-jobs) |
| Apply paths | [Apply for jobs](https://docs.worklittle.com/jobs/api/apply-for-jobs) |
| MCP install + tools | [MCP](https://docs.worklittle.com/jobs/mcp) |
| Install these skills | [Agent skills](https://docs.worklittle.com/skills) |

## Rules

- Do not invent query parameters, MCP tool names, or price points — look them up.
- Prefer product-prefixed paths (`/jobs/...`, `/business/...`) over legacy unprefixed API paths.
- For live account actions (list keys, spend), use the API / MCP with the user's key — docs are not a substitute for runtime data.
