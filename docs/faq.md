# FAQ

**How do I connect in Claude web?**
Go to Settings → Connectors → Add custom connector, paste the base URL
`https://mcp-vat.iwebdevelopment.com`, and follow the sign-up form. See the
[Claude client page](clients/claude.md) for details.

**What does it cost?**
Nothing. There is no plan, no trial that expires, and no credit card. Every organization gets 50
searches and 25 profiles per month; see [Monthly allowances](limits.md).

**Do I need an accounting package, or a KVK account of my own?**
Neither. You sign up with an email address and the KVK number of your own organization.

**Why does a search give me a company without an address?**
The register does not disclose an address for every entry in a search result. `company_profile`
returns more, including the address of the main establishment, but it needs a KVK number.

**My allowance is used up. What now?**
That tool declines until the start of the next calendar month; the other one keeps working. The
counter is per organization, so everyone signed in under the same account shares it.

**I cannot find a company. Is something wrong?**
Possibly not. The Handelsregister covers organizations registered in the Netherlands, so a
foreign supplier will not be in it. A company can also be registered under a statutory name that
differs from the name you know it by; try a distinctive part of the name, or search by town.

**Can the assistant change anything?**
No. Both tools are read-only, and there is nothing to write to: this connection talks to a public
register, not to your own systems.

**Do you keep what I look up?**
No. The answer is used to reply to you and is not stored. We keep your email address, your
organization's KVK number, a session and a usage counter. See
[PRIVACY.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/PRIVACY.md).

**Is this a product of the Kamer van Koophandel?**
No. It is built by iWebDevelopment and queries the register's public API. We are not affiliated
with the Kamer van Koophandel and do not speak on its behalf. See
[TRADEMARKS.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/TRADEMARKS.md).

**Where is my data hosted?**
In the **EU**.

**Where can I find the terms?**
The authoritative terms are iWebDevelopment's
[Algemene Voorwaarden (AV)](https://www.iwebdevelopment.com/hubfs/144641067/Files/algemene-voorwaarden.pdf)
and the accompanying DPA (verwerkersovereenkomst). See
[PRIVACY.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/PRIVACY.md) and
[TRUST.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/TRUST.md) for a
plain-language summary.
