---
name: kubit-connect
description: Authenticate to Kubit and select the current org / workspace.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-connect

Authenticate the runtime against the hosted Kubit MCP server and select the
organization whose data the session will read.

## Steps

1. Ensure the MCP server is wired. The agent plugin bundles a `.mcp.json` pointing at
   `https://mcp.kubit.ai/mcp` over the `http-stream` transport. In Cursor this is
   Settings -> Tools & MCP -> Add a Custom MCP Server; in Claude it is
   Settings -> Connectors -> Add custom connector.
2. Trigger the OAuth flow. Kubit uses authorization code with PKCE (`S256`) against
   `https://mcp.kubit.ai/auth/oauth2/authorize`, exchanging at
   `https://mcp.kubit.ai/auth/oauth2/token`. Clients may self-register at
   `https://mcp.kubit.ai/auth/oauth2/register`.
3. Enter the organization name when prompted (`org: <org name>`).
4. Request only the scopes the task needs: `mcp:read` for inspection and reporting
   reads, `mcp:write` when the session will create reports.
5. Call `getUserContext` — it is documented as always the first call, and it returns the
   user context, the available schemas, and the active schema selection that every later
   tool call depends on.

## Notes

- Access is enforced by Kubit's existing role-based access controls (Admin, Governor,
  Creator, Viewer, or a custom role), so a successful connection does not imply access
  to every schema.
- If the connection stalls, restart the MCP server from the client's installed-servers
  panel, or reload the editor window.
