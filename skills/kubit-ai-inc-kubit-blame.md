---
name: kubit-blame
description: Find the code change behind a trace regression, downstream of report / inspect.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-blame

Correlate a regression seen in Kubit analytics with the change in the codebase that
produced it.

## MCP tools used

- `getUserContext`, `getSchema`, `createReport`, `getRawData`, `searchKubit`.

## Steps

1. Run `/kubit-inspect` or `/kubit-report` first — this skill is documented as
   downstream of them. Establish *what* regressed and *when* before asking *why*.
2. Pin the regression window from the report output: the metric, the affected cohort or
   segment, and the first date the change appears.
3. Pull the raw rows for that window with `getRawData` so the boundary is exact rather
   than eyeballed off a chart.
4. Search the local repository history across the same window (commits, deploys,
   released package versions) and line the candidates up against the boundary date.
5. Report the candidate change with the evidence: the Kubit report link, the metric
   delta, and the specific commit or deploy that lands in the window.

## Notes

- Kubit maps clickstream behavior to LLM traces, so a regression may be behavioral, a
  model/prompt change, or both — check whether the affected traces share a model,
  prompt version, or provider before blaming application code.
- Incidents can be attached alongside reports in Kubit to record the finding.
