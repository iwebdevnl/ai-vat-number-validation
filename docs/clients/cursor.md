# Cursor

Cursor connects to remote MCP servers by URL. Add AI VAT Number Validation through the settings UI, or edit the project config directly. There is no documented plan gate for MCP in Cursor.

## Steps

1. Go to **Settings → Tools & MCP → New MCP Server**, or edit `.cursor/mcp.json`:

   ```json
   { "mcpServers": { "vat": { "url": "https://mcp-vat.iwebdevelopment.com" } } }
   ```

2. On first connect, Cursor opens your browser for OAuth authorization.

You can also use the "Add to Cursor" badge in the [README](https://github.com/iwebdevnl/ai-vat-number-validation) for a one-click add.

See the [compatibility matrix](https://github.com/iwebdevnl/ai-vat-number-validation#client-compatibility) (last verified 2026-07).
