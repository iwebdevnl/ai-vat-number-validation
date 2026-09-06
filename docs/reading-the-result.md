# Reading the result

A VIES answer has more shades than "valid" and "invalid", and the differences change what you
should conclude.

## "Not processed" is not a mismatch

Member states decide for themselves whether they confirm a name and address match. **Ireland,
Luxembourg, France, Italy and Germany return no match elements at all.**

So for a German supplier you will usually learn that the VAT number is valid, and nothing about
whether the name and address you hold are the ones on the registration. That is the member state
declining to say, not a discrepancy.

Three outcomes, three meanings:

| Outcome | What it means |
|---|---|
| Matched | The member state confirms this field agrees with the registration. |
| Not matched | The member state says this field does **not** agree. Worth investigating. |
| Not processed | The member state did not answer for this field. Nothing was checked and nothing is wrong. |

Reporting "not processed" as suspicious would put every German and French supplier under
suspicion for no reason. It is the single most common way to misread this tool.

## An unavailable service is not an invalid number

VIES has outages, and individual member states go offline independently of it. When that happens
you get told the check could not be completed.

"We could not check right now" and "this number is not valid" are different answers. Only the
second one is a finding. If your process blocks a payment on an invalid VAT number, it should not
block on an unavailable one; retry instead.

## What a valid number does and does not tell you

It confirms that the number is registered for VAT in that member state, and, where the member
state cooperates, that the name and address you supplied match the registration.

It does not tell you that the company is solvent, that the invoice is genuine, or that the person
you are dealing with represents them. This is a register comparison, not a credit check and not a
fraud determination.

## The consultation number

For a check made with a requester VAT number, VIES issues a consultation number. That is the
evidence that this specific number was verified at that moment, and it is what makes the check
reproducible later. Keep it with the record it belongs to.

If no consultation number comes back, the result is still informative but it is not evidence.
Either the service was unavailable, or there is no requester VAT number on file to issue it to.
