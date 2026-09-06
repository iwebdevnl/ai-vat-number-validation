# Claude (web + Desktop)

Claude connects to AI VAT Number Validation as a custom connector. Works on all Claude plans, including the free plan (free allows one custom connector); on Team and Enterprise, an owner can add it org-wide so the whole team gets it automatically.

Use the custom-connector UI described below, not the local desktop config file.

## Steps

1. Go to **Settings → Connectors → Add custom connector**.
2. Paste the base URL: `https://mcp-vat.iwebdevelopment.com`
3. Sign up in the browser: your email address and the VAT number of your own organization. You get a sign-in link by email.

That is it, no tokens, no manual JSON.

See the [compatibility matrix](https://github.com/iwebdevnl/ai-vat-number-validation#client-compatibility) (last verified 2026-07).
