---
name: mcp-install
description: >-
  Guides Worklittle MCP client setup: https://mcp.worklittle.com/, Bearer
  sk-wl-api01 auth, one-click installs, and common JSON-RPC auth errors. Use when
  connecting Cursor, VS Code, Claude, ChatGPT, or other MCP clients — before
  calling Worklittle tools in an agent session.
---

Shared install skill. For which tool to call after connect, use `capability-map` or product skills.

## Critical rules

- MCP URL: **`https://mcp.worklittle.com/`** (forwards JSON-RPC to the Jobs API with your key).
- Every request needs `Authorization: Bearer sk-wl-api01-...` from [API keys](https://worklittle.com/business/api-keys).
- Same prepaid balance and scopes as REST. Missing scope → **403**; no balance → **402**; rate limit → **429** (often JSON-RPC `-32603`).
- After changing MCP config, **restart** the client.
- Agent skills (`npx skills add https://docs.worklittle.com`) are separate from MCP tools — install both when useful.

## Quick install

Docs one-click and manual configs: [Jobs MCP](https://docs.worklittle.com/jobs/mcp) · [Business MCP](https://docs.worklittle.com/business/mcp).

Typical Cursor `mcp.json` shape:

```json
{
  "mcpServers": {
    "worklittle": {
      "url": "https://mcp.worklittle.com/",
      "headers": {
        "Authorization": "Bearer sk-wl-api01-..."
      }
    }
  }
}
```

Stdio-only clients: bridge with `mcp-remote` and pass the Bearer key via env/args.

## See also

- [API keys](https://docs.worklittle.com/jobs/get-started/api-keys)
- [Rate limits](https://docs.worklittle.com/jobs/resources/rate-limits)
- [Agent skills](https://docs.worklittle.com/skills)
- skill `worklittle-best-practices` · skill `capability-map`
