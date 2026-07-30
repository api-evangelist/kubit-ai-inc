---
name: kubit-inspect
description: Inspect Kubit users, sessions, traces, and events without leaving the editor.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-inspect

Explore the behavioral and LLM-trace data in the connected Kubit organization.

## MCP tools used

- `getUserContext` — establish user context, available schemas, and active schema.
- `getSchema` — retrieve event definitions, properties, and dimensions for one schema.
- `searchKubit` — locate existing reports and dashboards across the organization.

## Steps

1. Call `getUserContext` if the session has not already done so, and note the active
   schema.
2. Call `getSchema` for the schema under investigation. Read the event definitions and
   properties before composing any question — Kubit's semantic layer applies business
   definitions, data models, and governance policies, so use the schema's own names
   rather than guessing column names.
3. Use `searchKubit` to check whether an existing report or dashboard already answers
   the question before building anything new.
4. Narrow to the users, sessions, traces, or events of interest using the dimensions the
   schema actually declares.

## Notes

- Data retention depends on plan: 45 days (Developer), 200 days (Growth), unlimited
  (Enterprise). Queries beyond the retention window will return nothing.
- Only schemas permitted by the caller's role are visible; a missing schema is usually a
  permissions result, not an error.
