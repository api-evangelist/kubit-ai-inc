---
name: kubit-help
description: List the installed Kubit skills and how to use them.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-help

List the `/kubit-*` skills installed by `@kubit-ai/agent-plugin` and explain when to
reach for each.

## Steps

1. Confirm the plugin is installed — after `npx @kubit-ai/agent-plugin` the runtime must
   be restarted before the skills register.
2. Present the skill surface:
   - `/kubit-connect` — authenticate and select the current org / workspace.
   - `/kubit-inspect` — inspect users, sessions, traces, and events.
   - `/kubit-report` — find, run, or create analytics reports.
   - `/kubit-blame` — find the code change behind a trace regression.
   - `/kubit-integrate` — wire an LLM app's tracing into Kubit.
   - `/kubit-update` — check npm for a new version and install it.
   - `/kubit-help` — this skill.
3. Point the user at `/kubit-connect` first if `getUserContext` has not yet succeeded in
   this session.
