# AI VAT Number Validation

Verify EU VAT numbers from the AI assistant you already use, and get the consultation number as
evidence.

Free, hosted at `https://mcp-vat.iwebdevelopment.com`. No accounting package needed and no tokens
to paste into any config: you sign up with an email address and the VAT number of your own
organization, and get a sign-in link by email.

## One tool, read-only

`company_verify_vat` checks a VAT number against VIES, the VAT Information Exchange System, which
forwards the question to the tax administration of the member state that issued it. Supply a
company name and address as well and those are cross-checked against the registration.

You get back whether the number is valid, a consultation number as evidence, and per field
whether it matched, did not match, or was not processed by the member state.

## Read this before you rely on it

A field that was **not processed** was not checked. Several member states never return the match
elements, and treating that as a discrepancy would flag perfectly ordinary suppliers. See
[Reading the result](reading-the-result.md).

## Where to go next

- **Connect:** pick your assistant in the Clients section for per-client steps. The
  [README on GitHub](https://github.com/iwebdevnl/ai-vat-number-validation) has the compatibility
  matrix at a glance.
- **What it costs you:** nothing. See [Monthly allowances](limits.md) for how much you can verify
  per month.
- **Trust and privacy:** see
  [TRUST.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/TRUST.md) and
  [PRIVACY.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/PRIVACY.md).
- **Other integrations:** see [iWebDevelopment](https://www.iwebdevelopment.com/kennisbank) for
  our AI connections to Exact Online, Twinfield and AFAS.
