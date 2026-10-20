# FAQ

**How do I connect in Claude web?**
Go to Settings → Connectors → Add custom connector, paste the base URL
`https://mcp-vat.iwebdevelopment.com`, and follow the sign-up form. See the
[Claude client page](clients/claude.md) for details.

**What does it cost?**
Nothing. There is no plan, no trial that expires, and no credit card. There is a monthly
allowance per organization; see [Monthly allowance](limits.md).

**Why do you need my own VAT number?**
VIES issues a consultation number to a *requester*. Without a requester VAT number there is
nothing to hand you as evidence, only a plain valid or not valid.

**It says a field was "not processed". Is that bad?**
No. Several member states, among them Ireland, Luxembourg, France, Italy and Germany, do not
return the match elements at all. Nothing was checked for that field and nothing is wrong. See
[Reading the result](reading-the-result.md).

**The check failed. Does that mean the number is invalid?**
Not necessarily. VIES has outages and member states go offline individually. An unavailable
service is a different answer from an invalid number, and only the second one is a finding.

**Does this prove my supplier is legitimate?**
No. It confirms that a VAT number is registered and, where the member state cooperates, that the
name and address match. It is not a credit check and not a fraud determination.

**Which countries does it cover?**
The 27 EU member states, plus Northern Ireland (XI) numbers. It does not cover VAT numbers issued
outside the EU.

**Why did a Dutch check use one of my register lookups?**
For a Dutch number given with a company name but no address, the address is completed from the
Dutch business register first. Supply an address yourself, or pass `use_kvk: false`, and it does
not happen.

**Can the assistant change anything?**
No. The tool is read-only, and there is nothing to write to.

**Do you keep what I check?**
No. The answer is used to reply to you and is not stored. We keep your email address, your
organization's VAT number, a session and a usage counter. See
[PRIVACY.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/PRIVACY.md).

**Is this an EU service?**
No, it is built by iWebDevelopment and queries VIES, which is operated by the European
Commission. We are not affiliated with the Commission and do not speak on its behalf. See
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
