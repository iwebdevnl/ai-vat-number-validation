# Trust

## What the AI can and cannot do

The one tool in this connection is **read-only**. The assistant can check whether an EU VAT
number is valid and obtain the evidence for that check. It cannot create, change or delete
anything, here or anywhere else.

`company_verify_vat` checks a VAT number against VIES, the VAT Information Exchange System, which
forwards the question to the tax administration of the member state that issued the number. Give
it a company name and address as well, and those are cross-checked against the registration.

It is marked read-only in the protocol itself, so a client that distinguishes between safe and
unsafe tools sees that too.

## The consultation number

VIES returns a consultation number for a check made with a requester VAT number. That number is
the evidence that this specific VAT number was verified at that moment, and it is what makes the
check reproducible later. Keep it with the record it belongs to.

Obtaining it requires your own VAT number, which is why sign-up asks for it.

## Two sources, not one

For a Dutch VAT number given with a company name but no address, the address is completed from
the Dutch business register before the cross-check runs. That is a second external register, and
it is worth knowing about even though it costs you nothing at the source. It draws one unit from
the register-lookup allowance, and the response says so when it happens.

Pass `use_kvk: false`, or supply an address yourself, and that lookup does not happen.

## What we do not have access to

Connecting this does not give us access to your accounting package, your mailbox, your files, or
any other system. There is no such connection to make. You give an email address and your own VAT
number, and that is the whole account.

## Monthly allowances

Every organization gets a monthly allowance, reset at the start of each calendar month, and your
remaining allowance comes back with every answer. When an allowance runs out, the affected step
declines with an explanation. Running out of register lookups does not block a verification; it
only means the address is not completed for you.

## Certification

iWebDevelopment is **ISO 27001** certified.

## Where it runs

Core infrastructure runs in the **EU**.

## Authoritative terms

This page is a plain-English summary. The binding terms are set out in iWebDevelopment's
Algemene Voorwaarden (AV); where anything here and the AV appear to differ, the AV governs.
