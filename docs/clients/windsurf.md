# Windsurf

Windsurf connects to remote MCP servers through its Tools settings, or by editing the raw config directly. Note the field name: Windsurf uses `serverUrl`, not `url`.

## Steps

1. Go to **Settings → Tools → Add Server**, or edit the raw config:

   ```json
   { "mcpServers": { "kvk": { "serverUrl": "https://mcp-vat.iwebdevelopment.com" } } }
   ```

2. Sign up when Windsurf opens the browser: your email address and the KVK number of your own organization.

Some Enterprise Windsurf plans may gate remote MCP servers by admin policy.

See the [compatibility matrix](https://github.com/iwebdevnl/ai-vat-number-validation#client-compatibility) (last verified 2026-07).
