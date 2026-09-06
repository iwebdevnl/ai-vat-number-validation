# AI VAT Number Validation

Look up Dutch companies in the Handelsregister, the business register of the Kamer van
Koophandel, from the AI assistant you already use.

Free, hosted at `https://mcp-vat.iwebdevelopment.com`. No accounting package needed and no
tokens to paste into any config: you sign up with an email address and the KVK number of your
own organization, and get a sign-in link by email.

## Two tools, both read-only

- **`company_search`** matches by name, KVK number, town or address.
- **`company_profile`** returns the full record for one KVK number: statutory name, trade names,
  legal form, registration date, activities, and the address of the main establishment.

There is nothing to write to. This connection talks to a public register, not to your own
systems.

## Where to go next

- **Connect:** pick your assistant in the Clients section for per-client steps. The
  [README on GitHub](https://github.com/iwebdevnl/ai-vat-number-validation) has the
  compatibility matrix at a glance.
- **What it costs you:** nothing. See [Monthly allowances](limits.md) for how much you can look
  up per month.
- **Trust and privacy:** see
  [TRUST.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/TRUST.md) and
  [PRIVACY.md](https://github.com/iwebdevnl/ai-vat-number-validation/blob/main/PRIVACY.md).
- **Other integrations:** see [iWebDevelopment](https://www.iwebdevelopment.com/kennisbank) for
  our AI connections to Exact Online, Twinfield and AFAS.
