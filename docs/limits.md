# Monthly allowances

There are no plans and no trial. The connection is free, and every organization gets the same
monthly allowance.

| Allowance | Free | With the add-on |
|---|---:|---:|
| VAT verifications (`company_verify_vat`) | 100 | 1000 |
| Register lookups | 50 | 1000 |

## Why there are two rows

For a Dutch VAT number given with a company name but no address, the address is completed from
the Dutch business register before the cross-check runs. That is a second external register, and
it draws one unit from the register-lookup allowance. The response tells you when it happened.

Supply an address yourself, or pass `use_kvk: false`, and the lookup does not happen. For a
non-Dutch VAT number it never happens at all.

Until 2026-08 that lookup was not counted anywhere. It is now, because the Kamer van Koophandel
prohibits bulk extraction from the register in its terms, and an uncounted path cannot be kept
inside that boundary.

## When an allowance runs out

Running out of **verifications** means the tool declines until the start of the next calendar
month.

Running out of **register lookups** does not block a verification. Only the automatic address
completion is skipped, and the response says so. You can still verify by supplying the address
yourself.

## How the counting works

Counters are **per organization**, not per user, so everyone signed in under the same account
draws from the same allowance. They reset at the start of each calendar month.

## The add-on

The larger allowances belong to the add-on, which is part of a paid subscription to one of our
accounting integrations for Exact Online, Twinfield or AFAS. A free account cannot enable it.
