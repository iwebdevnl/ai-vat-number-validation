# Zed

Recent Zed builds support remote MCP servers natively. Older builds need a small stdio bridge instead.

## Recent builds

1. Go to **Settings → AI → MCP Servers** and add the URL: `https://mcp-vat.iwebdevelopment.com`
2. Sign up when prompted: your email address and the KVK number of your own organization. You get a sign-in link by email.

## Older builds

Bridge the remote server as a stdio context server with `mcp-remote`:

```
npx mcp-remote https://mcp-vat.iwebdevelopment.com
```

See the [compatibility matrix](https://github.com/iwebdevnl/ai-vat-number-validation#client-compatibility) (last verified 2026-07).
