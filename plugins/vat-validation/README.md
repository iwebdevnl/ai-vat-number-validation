# AI VAT Number Validation

Verify EU VAT numbers from your AI assistant, with a consultation number as evidence.

This plugin connects to the hosted MCP server at `https://mcp-vat.iwebdevelopment.com`. On first
use your client asks for authorization and sends you to a sign-up form: your email address and
the VAT number of your own organization. You get a sign-in link by email.

One tool, read-only:

| Tool | What it does |
| --- | --- |
| `company_verify_vat` | Checks a VAT number via VIES and cross-checks the name and address you supply |

And two commands: `/vat-check` and `/vat-evidence`.

Setup, allowances, privacy and the per-client guides are in the
[main README](https://github.com/iwebdevnl/ai-vat-number-validation).
