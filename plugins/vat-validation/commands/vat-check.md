---
description: Verify an EU VAT number and cross-check the company name and address.
allowed-tools: mcp__plugin_ai-vat-number-validation_vat__company_verify_vat
---

Verify this VAT number: $ARGUMENTS

Use `company_verify_vat`. Pass the company name and address if the user supplied them, so they
are cross-checked against the registration.

Report the outcome in three parts:

1. Whether the number is valid, and the consultation number, which is the evidence that the
   check was performed.
2. Which fields matched, and which did not.
3. Which fields the member state did not process.

That third part matters, so do not fold it into the second. Ireland, Luxembourg, France, Italy
and Germany return no match elements at all. A field that was not processed **was not checked**.
It is not a mismatch, and it says nothing about the company. Reporting it as a discrepancy would
put every German and French supplier under suspicion for no reason.

Distinguish an invalid number from an unavailable service. VIES goes down, and member states go
offline individually. "We could not check right now" is a different answer from "this number is
not valid", and only the second one is a finding.

For a Dutch VAT number the address is completed from the Dutch business register when the user
gave a name but no address. That draws one unit from the register-lookup allowance; the response
says so, and you should pass that on.
