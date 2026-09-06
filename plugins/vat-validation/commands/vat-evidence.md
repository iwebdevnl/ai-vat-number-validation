---
description: Obtain a consultation number as evidence that a VAT number was verified.
allowed-tools: mcp__plugin_ai-vat-number-validation_vat__company_verify_vat
---

Obtain evidence of verification for: $ARGUMENTS

Use `company_verify_vat` and report the consultation number prominently, together with the date
and the exact number that was checked. That combination is what makes the check reproducible
later.

Explain briefly what the consultation number is: proof issued by VIES that this specific VAT
number was verified at that moment. Tell the user to keep it with the record it belongs to, for
example with the invoice or in the supplier's file.

If no consultation number comes back, say so explicitly and do not present the result as
evidence. Two causes are worth telling apart:

- **VIES or the member state was unavailable.** Nothing was verified. Try again later.
- **No requester VAT number is on file**, so VIES has nobody to issue the number to. The user can
  add their own VAT number in their account and repeat the check.

A valid-looking answer without a consultation number is still useful to a human, but it is not
evidence, and presenting it as such would give the user something that does not hold up.
