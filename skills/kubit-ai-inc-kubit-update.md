---
name: kubit-update
description: Check npm for a newer Kubit agent plugin and install it.
api: Kubit MCP Server
source: https://www.npmjs.com/package/@kubit-ai/agent-plugin
generated: '2026-07-19'
method: searched
mcp_server: https://mcp.kubit.ai/mcp
---

# /kubit-update

Keep the installed Kubit skills current.

## Steps

1. Read the installed version from `<config>/kubit/VERSION`.
2. Check npm for a newer release of `@kubit-ai/agent-plugin`.
3. Show the user the changelog slice they have not seen yet.
4. On confirmation, re-run the installer:

   ```bash
   npx @kubit-ai/agent-plugin
   ```

   Flags: `--global` (default, user-wide) or `--local` (current directory);
   `--uninstall` to remove; `--yes` to skip the location prompt. The runtime is always
   prompted.
5. Restart the runtime and run `/kubit-help` to confirm the skills re-registered.

## Notes

- The package is pre-1.0 and under active development; the MCP server it wires to is
  described as beta.
