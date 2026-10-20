# AI VAT Number Validation

<img src="assets/logo.png" alt="iWebDevelopment" width="180">

AI VAT Number Validation, by iWebDevelopment, is a hosted MCP server that lets your AI assistant
verify EU VAT numbers through VIES, the VAT Information Exchange System, and hand you the
consultation number as evidence.

Free. Hosted at `https://mcp-vat.iwebdevelopment.com`. No accounting package needed, no credit
card, no tokens to paste into a config.

[![Add to Cursor](https://img.shields.io/badge/Add_to-Cursor-000?logo=cursor)](https://cursor.com/install-mcp?name=vat&config=eyJ1cmwiOiJodHRwczovL21jcC12YXQuaXdlYmRldmVsb3BtZW50LmNvbSJ9) [![Install in VS Code](https://img.shields.io/badge/Install_in-VS_Code-007ACC?logo=visualstudiocode)](https://insiders.vscode.dev/redirect/mcp/install?name=vat&config=%7B%22name%22%3A%22vat%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-vat.iwebdevelopment.com%22%7D)

Works with Claude, ChatGPT, Perplexity, GitHub Copilot in VS Code, Cursor and other MCP-capable
clients. How you add it differs per client; see the [client list](#client-compatibility) below.

![AI VAT Number Validation in action](assets/demo.gif)


## What you can do

One tool, **read-only**.

`company_verify_vat` checks a VAT number against VIES, which forwards the question to the tax
administration of the member state that issued it. Supply a company name and address as well and
those are cross-checked against the registration.

What comes back:

- Whether the number is valid.
- **A consultation number**, the evidence that this specific number was verified at that moment.
- Per field, whether it matched, did not match, or **was not processed by the member state**.

That last distinction is the one to understand before you use this. See
[Reading the result](#reading-the-result).

## Example prompts

- "Is the VAT number on this invoice valid?"
- "Verify this supplier's VAT number and check that the name and address match."
- "Check this supplier and give me the consultation number for our records."
- "We are about to invoice without VAT to a French company. Verify their number first."
- "Is this number still valid, or has it been deregistered?"

## Connect

1. Paste the base URL into your AI client: `https://mcp-vat.iwebdevelopment.com`
2. Your client asks for authorization and sends you to our sign-up form.
3. Fill in your email address and the VAT number of your own organization, and agree to the
   terms. You get a sign-in link by email, and you are connected.

Your own VAT number is not optional bookkeeping: VIES issues a consultation number to a
*requester*, so without it there is nothing to hand you as evidence.

### Add to Claude (web + Desktop)

1. Go to **Settings → Connectors → Add custom connector**.
2. Paste the base URL: `https://mcp-vat.iwebdevelopment.com`
3. Follow the sign-up form.

On the free plan you can add one custom connector. On Team/Enterprise, an owner adds it org-wide.

For a legacy `mcp-remote` fallback, see `examples/claude-desktop-config.json` (optional, not
required).

### Claude Code (plugin)

```
/plugin marketplace add iwebdevnl/ai-vat-number-validation
/plugin install ai-vat-number-validation@iwebdevnl-vat-number-validation
/reload-plugins
/mcp
```

The last command signs you in. The plugin adds two commands: `/vat-check` and `/vat-evidence`.

Prefer to add it manually? `claude mcp add --transport http vat https://mcp-vat.iwebdevelopment.com`

### Other clients

This is a standard remote MCP server, so most MCP-capable clients (ChatGPT, Perplexity, GitHub
Copilot, Cursor, Cline, Windsurf, Zed, and others) can add it by URL. Setup steps vary per
client, see the matrix below and the per-client pages in
[the documentation](https://iwebdevnl.github.io/ai-vat-number-validation/).

## Reading the result

**A field that was "not processed" was not checked.** Member states decide for themselves whether
they confirm a name and address match. Ireland, Luxembourg, France, Italy and Germany return no
match elements at all.

Not processed is **not** a mismatch and says nothing about the company. Treating it as suspicious
would put every German and French supplier under suspicion for no reason.

**An unavailable service is not an invalid number.** VIES goes down, and member states go offline
individually. "We could not check right now" and "this number is not valid" are different
answers, and only the second is a finding.

**A valid number is not a guarantee of who you are dealing with.** It confirms that the number is
registered and, where the member state cooperates, that the name and address match. It is not a
credit check and not a fraud determination.

## Monthly allowance

Free, with a monthly allowance per organization that resets at the start of each calendar month.
Your remaining allowance comes back with every answer, so ask your assistant if you want to know
where you stand.

There are two counters, and that is worth knowing. A verification draws from one. For a Dutch VAT
number given with a company name but no address, the address is completed from the Dutch business
register before the cross-check runs, and that draws from a second, separate one. Supply an
address yourself, or pass `use_kvk: false`, and the second counter stays untouched. Running out of
it never blocks a verification; it only means the address is not completed for you.

## Client compatibility

| Client | How to add |
|---|---|
| Claude (web / Desktop) | Settings → Connectors → Add custom connector → base URL |
| Claude Code | `claude mcp add --transport http vat https://…` |
| GitHub Copilot (VS Code) | `.vscode/mcp.json` with `"type":"http"` + the server URL |
| Cursor | Settings → Tools & MCP → New MCP Server (`url`), or the Add-to-Cursor badge |
| Cline | mcp.json `"type":"streamableHttp"` (camelCase) |
| Windsurf | Settings → Tools → Add Server (`serverUrl`) |
| Zed | Settings → AI → MCP Servers (URL + Authorization header) |
| ChatGPT | Settings → Connectors → Advanced → Developer mode → add the URL |
| Perplexity | Add a custom remote connector by URL |
| Microsoft 365 Copilot | No "paste a URL" for end users; the agent path via Copilot Studio |

This connection is free on all of them. A few clients gate remote connectors behind their own
paid plan or an admin policy, ChatGPT and Perplexity among them; the
[per-client pages](https://iwebdevnl.github.io/ai-vat-number-validation/) say which.

## Verify the connection

Once connected, try:

- "Is this a valid EU VAT number?"
- "Give me the consultation number for that check."

## Trust

- The tool is **read-only** and marked as such in the protocol.
- Connecting this gives us no access to any system of yours. You give an email address and your
  own VAT number, and that is the whole account.
- We do not keep a record of which VAT numbers you checked.
- **ISO 27001** certified. Data hosted in the EU.

See [TRUST.md](TRUST.md), [PRIVACY.md](PRIVACY.md), and [SECURITY.md](SECURITY.md) for details.

## Looking up Dutch companies?

That is a separate connection, free and standalone like this one:
[KVK Handelsregister AI Connect](https://github.com/iwebdevnl/kvk-handelsregister-ai-connect).

## License

The files in this repository are MIT licensed (see [LICENSE](LICENSE)), except the brand material
in `assets/`. The hosted service itself is proprietary and is not covered by that license.
[NOTICE](NOTICE) sets out the exact scope.

## Support

Product page: https://www.iwebdevelopment.com/btw-nummer-validator
Documentation: https://iwebdevnl.github.io/ai-vat-number-validation/
Knowledge base: https://www.iwebdevelopment.com/kennisbank
