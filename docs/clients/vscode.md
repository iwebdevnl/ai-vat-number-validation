# VS Code (GitHub Copilot)

GitHub Copilot in agent mode (VS Code 1.101 or later) can call remote MCP servers directly. Works on all Copilot plans, including the free plan. On Copilot Business and Enterprise, an admin must enable the "MCP servers in Copilot" policy, which is off by default.

## Steps

1. In your project (or user settings), create `.vscode/mcp.json`:

   ```json
   { "servers": { "vat": { "type": "http", "url": "https://mcp-vat.iwebdevelopment.com" } } }
   ```

2. VS Code prompts you to start the server; sign up in the browser with your email address and the VAT number of your own organization.

See the [compatibility matrix](https://github.com/iwebdevnl/ai-vat-number-validation#client-compatibility) (last verified 2026-07).
