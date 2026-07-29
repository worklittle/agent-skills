# REST, MCP, SDK, CLI

Same account, same `sk-wl-api01-...` key, same billing. Choose by where code runs.

| Transport | Best for | Notes |
| --- | --- | --- |
| **MCP** (`https://mcp.worklittle.com`) | Coding agents with tool calling | JSON-RPC tools forward to the Jobs API |
| **REST** (`https://api.worklittle.com`) | Backends, webhooks receivers, fine control | Full surface including REST-only routes |
| **SDK** (`@worklittle/sdk` / `worklittle` Python) | In-process typed clients | Same endpoints as REST |
| **CLI** (`worklittle`) | Shell scripts, JSON on stdout | Same auth and billing |

## REST-only gaps (no MCP equivalent)

- Contact unlock: `GET /people/:id/contact`
- Public board apply: `POST /job-boards/:company/jobs/:id/apply` (no key)

Prefer MCP when the agent already has an MCP client. Prefer REST when you need those routes or tight control over pagination and retries.

## Auth header

```http
Authorization: Bearer sk-wl-api01-...
```

Create keys at https://worklittle.com/work/api-keys. Worklittle shows the full secret once.
