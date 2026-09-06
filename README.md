# AI VAT Number Validation

<img src="assets/logo.png" alt="iWebDevelopment" width="180">

AI VAT Number Validation, by iWebDevelopment, is a hosted MCP server that lets your AI assistant
verify EU VAT numbers through VIES, the VAT Information Exchange System, and hand you the
consultation number as evidence.

Free. Hosted at `https://mcp-vat.iwebdevelopment.com`. No accounting package needed, no credit
card, no tokens to paste into a config.

[![Add to Cursor](https://img.shields.io/badge/Add_to-Cursor-000?logo=cursor)](https://cursor.com/install-mcp?name=vat&config=eyJ1cmwiOiJodHRwczovL21jcC12YXQuaXdlYmRldmVsb3BtZW50LmNvbSJ9) [![Install in VS Code](https://img.shields.io/badge/Install_in-VS_Code-007ACC?logo=visualstudiocode)](https://insiders.vscode.dev/redirect/mcp/install?name=vat&config=%7B%22name%22%3A%22vat%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-vat.iwebdevelopment.com%22%7D)

Works with Claude on all plans (including the free plan); also with ChatGPT (Developer Mode, paid
plans), Perplexity (Pro/Max/Enterprise), GitHub Copilot in VS Code, Cursor and other developer
tools. Availability and setup differ per client. See the
[client compatibility matrix](#client-compatibility) below.

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

- "Is VAT number DE123456789 valid?"
- "Verify NL810433941B01 and check that it belongs to iWebDevelopment in Amersfoort."
- "Check this supplier's VAT number and give me the consultation number for our records."
- "This invoice says Voorbeeld BV, Dorpsstraat 1, Utrecht, VAT NL999999999B01. Does that match?"
- "We are about to invoice without VAT to a French company. Verify their number first."

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

## Monthly allowances

Per organization, per calendar month:

| Allowance | Free | With the add-on |
|---|---:|---:|
| VAT verifications | 100 | 1000 |
| Register lookups | 50 | 1000 |

The second row is not a typo. For a Dutch VAT number given with a company name but no address,
the address is completed from the Dutch business register before the cross-check runs, and that
draws one register lookup. Supply an address yourself, or pass `use_kvk: false`, and it does not.

Running out of register lookups does not block a verification; it only means the address is not
completed for you.

The add-on is part of a paid subscription to one of our accounting integrations; see the last
section.

## Client compatibility

**Last verified: 2026-07**

| Client | Remote MCP? | Plan / mode | How to add |
|---|---|---|---|
| Claude (web / Desktop) | Yes | All plans incl. **Free** (Free = 1 custom connector); Team/Ent = owner adds | Settings → Connectors → Add custom connector → base URL |
| Claude Code | Yes | Claude Code itself needs Pro/Max or API billing | `claude mcp add --transport http vat https://…` |
| GitHub Copilot (VS Code) | Yes | All Copilot plans; Business/Enterprise need an admin "MCP servers" policy (off by default) | `.vscode/mcp.json` with `"type":"http"` + the server URL |
| Cursor | Yes | No documented plan gate | Settings → Tools & MCP → New MCP Server (`url`), or the Add-to-Cursor badge |
| Cline | Yes | Free (open-source) | mcp.json `"type":"streamableHttp"` (camelCase) |
| Windsurf | Yes | Enterprise may gate | Settings → Tools → Add Server (`serverUrl`) |
| Zed | Yes on recent builds (native HTTP since 2026-03); older builds via `mcp-remote` bridge | No documented gate | Settings → AI → MCP Servers (URL + Authorization header) |
| ChatGPT | Yes, **Developer Mode only** | **Paid** (Plus/Pro/Business/Enterprise/Edu), not Free | Settings → Connectors → Advanced → Developer mode → add the URL |
| Perplexity | Yes (since 2026-03) | **Paid** (Pro/Max/Enterprise), not Free, not in Comet | Add a custom remote connector by URL |
| Microsoft 365 Copilot | **No end-user "paste a URL"** | Agent path only (Copilot Studio) | Build/publish an agent (a heavier path) |

The plan requirements in this table are the client's own, not ours. This connection is free on
every one of them.

## Verify the connection

Once connected, try:

- "Is NL810433941B01 a valid VAT number?"
- "Give me the consultation number for that check."

## Trust

- The tool is **read-only** and marked as such in the protocol.
- Connecting this gives us no access to any system of yours. You give an email address and your
  own VAT number, and that is the whole account.
- We do not keep a record of which VAT numbers you checked.
- **ISO 27001** certified. Data hosted in the EU.

See [TRUST.md](TRUST.md), [PRIVACY.md](PRIVACY.md), and [SECURITY.md](SECURITY.md) for details.

## Using an accounting package?

These same tools are also available inside our AI connections for Exact Online, Twinfield and AFAS,
so you can verify a VAT number without leaving your administration. That is also where the larger
monthly allowances come from.

- [Exact Online AI Connect](https://github.com/iwebdevnl/exact-online-ai-connect)
- [Twinfield AI Connect](https://github.com/iwebdevnl/twinfield-ai-connect)
- [AFAS AI Connect](https://github.com/iwebdevnl/afas-ai-connect)

Looking up Dutch companies in the business register is a separate connection:
[KVK Handelsregister AI Connect](https://github.com/iwebdevnl/kvk-handelsregister-ai-connect).

## License

The files in this repository are MIT licensed (see [LICENSE](LICENSE)), except the brand material
in `assets/`. The hosted service itself is proprietary and is not covered by that license.
[NOTICE](NOTICE) sets out the exact scope.

## Support

Documentation: https://iwebdevnl.github.io/ai-vat-number-validation/
Knowledge base: https://www.iwebdevelopment.com/kennisbank
