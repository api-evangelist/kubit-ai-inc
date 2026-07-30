---
name: kubit-integrate
description: Wire an LLM app's tracing into Kubit — detect existing sinks and instrumentation sources.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-integrate

Connect an application's existing tracing into Kubit so behavior and LLM traces land in
the same place.

## Steps

1. Detect what the project already emits. The skill is documented to look for
   **sinks** — Langfuse, Braintrust — and **sources** — Vercel AI, OTel GenAI,
   LangChain. Kubit also documents integrations with LangSmith and Arize.
2. Install the exporter that matches:
   - OpenTelemetry / OTel GenAI semantics: `npm install @kubit-ai/otel`
   - An app already reporting to Sentry: `npm install @kubit-ai/sentry`, which tees
     Sentry errors and transactions to Kubit as OTLP for behavior analytics.
3. For warehouse-native product analytics rather than trace ingestion, follow the no-ETL
   integration guide — Kubit queries the customer's cloud data warehouse in place, and
   supports data replication via AWS S3 where direct query is not an option.
4. Verify by running `/kubit-inspect` and confirming the new events and traces appear in
   the expected schema.

## References

- Integration guide: https://docs.kubit.ai/docs/integration-guide
- Data replication via AWS S3: https://docs.kubit.ai/docs/s3
- Exporter: https://www.npmjs.com/package/@kubit-ai/otel
