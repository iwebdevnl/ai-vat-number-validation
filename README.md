# AI VAT Number Validation

<img src="assets/logo.png" alt="iWebDevelopment" width="180">

AI VAT Number Validation, by iWebDevelopment, is a hosted MCP server that lets your AI
assistant look up Dutch companies in the Handelsregister, the business register of the Kamer van
Koophandel. Ask in plain language, get the registered details back, right in the chat you
already use.

Free. Hosted at `https://mcp-vat.iwebdevelopment.com`. No accounting package needed, no credit
card, no tokens to paste into a config.

[![Add to Cursor](https://img.shields.io/badge/Add_to-Cursor-000?logo=cursor)](https://cursor.com/install-mcp?name=kvk&config=eyJ1cmwiOiJodHRwczovL21jcC1rdmsuaXdlYmRldmVsb3BtZW50LmNvbSJ9) [![Install in VS Code](https://img.shields.io/badge/Install_in-VS_Code-007ACC?logo=visualstudiocode)](https://insiders.vscode.dev/redirect/mcp/install?name=kvk&config=%7B%22name%22%3A%22kvk%22%2C%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fmcp-vat.iwebdevelopment.com%22%7D)

Works with Claude on all plans (including the free plan); also with ChatGPT (Developer Mode, paid
plans), Perplexity (Pro/Max/Enterprise), GitHub Copilot in VS Code, Cursor and other developer
tools. Availability and setup differ per client. See the
[client compatibility matrix](#client-compatibility) below.

![AI VAT Number Validation in action](assets/demo.gif)


## What you can do

Two tools, both **read-only**. There is nothing to write to: this is a public register, not your
own system.

| Tool | What it gives you |
|---|---|
| `company_search` | Matches by name, KVK number, town or address. Per hit: the KVK number, the name, the type and, where the register discloses it, the street and town. |
| `company_profile` | The full record for one KVK number: statutory name, trade names, legal form, registration date, activities, and the address of the main establishment. |

Typical use: checking a new customer or supplier before you take them on, filling in the
registered details of a company you only know by name, or confirming that a company is actually
registered.

## Example prompts

- "Zoek Joanknecht in het Handelsregister."
- "Wat is het KVK-nummer van iWebDevelopment?"
- "Welke bedrijven met 'bakkerij' in de naam staan er in Utrecht?"
- "Haal het volledige profiel op bij KVK-nummer 12345678."
- "Controleer deze nieuwe leverancier tegen het Handelsregister: Voorbeeld BV, Amsterdam."
- "Sinds wanneer staat dit bedrijf ingeschreven?"

## Connect

1. Paste the base URL into your AI client: `https://mcp-vat.iwebdevelopment.com`
2. Your client asks for authorization and sends you to our sign-up form.
3. Fill in your email address and the KVK number of your own organization, and agree to the
   terms. You get a sign-in link by email, and you are connected.

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

The last command signs you in. The plugin adds three commands: `/kvk-zoek`, `/kvk-profiel` and
`/kvk-controleer-relatie`.

Prefer to add it manually? `claude mcp add --transport http kvk https://mcp-vat.iwebdevelopment.com`

### Other clients

This is a standard remote MCP server, so most MCP-capable clients (ChatGPT, Perplexity, GitHub
Copilot, Cursor, Cline, Windsurf, Zed, and others) can add it by URL. Setup steps vary per
client, see the matrix below and the per-client pages in
[the documentation](https://iwebdevnl.github.io/ai-vat-number-validation/).

## Monthly allowances

Per organization, per calendar month:

| Allowance | Free | With the add-on |
|---|---:|---:|
| Searches | 50 | 1000 |
| Profiles | 25 | 100 |

Profiles have a lower allowance than searches because the register charges for them. When one
allowance runs out, that tool declines with an explanation and the other one keeps working. The
counters reset each calendar month.

The add-on is part of a paid subscription to one of our accounting integrations; see the last
section.

## Client compatibility

**Last verified: 2026-07**

| Client | Remote MCP? | Plan / mode | How to add |
|---|---|---|---|
| Claude (web / Desktop) | Yes | All plans incl. **Free** (Free = 1 custom connector); Team/Ent = owner adds | Settings → Connectors → Add custom connector → base URL |
| Claude Code | Yes | Claude Code itself needs Pro/Max or API billing | `claude mcp add --transport http kvk https://…` |
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

- "Zoek iWebDevelopment in het Handelsregister."
- "Haal het profiel op bij dat KVK-nummer."

## Trust

- Both tools are **read-only** and marked as such in the protocol.
- Connecting this gives us no access to any system of yours. You give an email address and your
  own KVK number, and that is the whole account.
- We do not keep a record of which companies you looked up.
- **ISO 27001** certified. Data hosted in the EU.

See [TRUST.md](TRUST.md), [PRIVACY.md](PRIVACY.md), and [SECURITY.md](SECURITY.md) for details.

## Limitations

- **Dutch companies only.** The Handelsregister covers organizations registered in the
  Netherlands. A foreign supplier will not be in it, and that absence says nothing about them.
- **`company_profile` needs a KVK number**, so look the company up first if you only have a name.
- **A search result is thin on address data.** The register does not disclose an address for
  every entry; `company_profile` has more.
- This is a comparison against the register. It is not a credit check and not a fraud
  determination.

## Using an accounting package?

These same tools are also available inside our AI connections for Exact Online, Twinfield and AFAS,
so you can look a company up without leaving your administration. That is also where the larger
monthly allowances come from.

- [Exact Online AI Connect](https://github.com/iwebdevnl/exact-online-ai-connect)
- [Twinfield AI Connect](https://github.com/iwebdevnl/twinfield-ai-connect)
- [AFAS AI Connect](https://github.com/iwebdevnl/afas-ai-connect)

Verifying EU VAT numbers is a separate connection:
[AI VAT Number Validation](https://github.com/iwebdevnl/ai-vat-number-validation).

## License

The files in this repository are MIT licensed (see [LICENSE](LICENSE)), except the brand material
in `assets/`. The hosted service itself is proprietary and is not covered by that license.
[NOTICE](NOTICE) sets out the exact scope.

## Support

Documentation: https://iwebdevnl.github.io/ai-vat-number-validation/
Knowledge base: https://www.iwebdevelopment.com/kennisbank
