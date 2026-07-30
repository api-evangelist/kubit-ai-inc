---
name: kubit-report
description: Find, run, or create Kubit analytics reports — cohorts, funnels, retention.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-report

Find an existing Kubit report, or generate and execute a new one, from the editor.

## MCP tools used

- `getUserContext` — required first call.
- `getSchema` — event definitions, properties, and dimensions.
- `searchKubit` — search reports and dashboards.
- `createReport` — generate and execute an analytical query.
- `getRawData` — export CSV-like raw output from an existing report.

## Steps

1. `getUserContext`, then `searchKubit` with the user's question text. Prefer reusing an
   existing report over creating a near-duplicate.
2. If nothing fits, `getSchema` for the target schema and build the request from the
   declared events, properties, and dimensions.
3. `createReport`. It returns a result summary, a link to the full report in the Kubit
   app, and a `formulaTemplateId` plus `analysisId` for further editing — surface all
   three to the user, since the link is how they continue in the product.
4. When the user needs the underlying rows rather than the summary, call `getRawData`
   against the report just created.

## Conventions

- `createReport` requires the `mcp:write` scope; the read-only path needs only
  `mcp:read`.
- There is no documented idempotency key — re-running `createReport` creates another
  report rather than returning the previous one. Reuse the returned `analysisId`
  instead of re-issuing the same creation.
- Usage is metered per trace, not per request, and overage bills at $0.0003/trace.
