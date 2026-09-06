# Privacy

This page is an informational summary of how AI VAT Number Validation handles data. It is not a
legal document. The authoritative, binding terms, and the current list of subprocessors, live in
iWebDevelopment's [Algemene Voorwaarden (AV)](https://www.iwebdevelopment.com/hubfs/144641067/Files/algemene-voorwaarden.pdf)
and the accompanying DPA (verwerkersovereenkomst). Where this page and the AV/DPA differ, the
AV/DPA governs. The DPA is available on request via support@iwebdevelopment.com.

## What we store about you

Signing up asks for two things, and those two are what we keep:

- **Your email address**, so we can send you the sign-in link and reach you about the service.
- **The VAT number of your own organization.** VIES needs a requester VAT number to issue a
  consultation number, so without it there is no evidence to hand you.

Alongside that we keep a session, so the connection knows who is asking, and a monthly usage
counter per organization, so the allowances can be enforced. The counters live in a cache with a
retention of about 35 days, which is just over the longest month.

There is no accounting package to connect, so there are no credentials to that kind of system,
and there is nothing synced or copied in bulk.

## What goes out per request, and to whom

Two external registers can be involved in a single check.

**Always: VIES, operated by the European Commission.** It receives the VAT number you are
checking, your own VAT number as the requester, and any company name and address you supplied for
cross-checking. VIES forwards the question to the tax administration of the member state that
issued the number.

**Sometimes: the Dutch business register, operated by the Kamer van Koophandel.** For a Dutch VAT
number given with a company name but no address, the company name is sent to that register to
complete the address before the cross-check runs. Pass `use_kvk: false`, or supply an address
yourself, and this does not happen.

Answers are used to reply to you and are not kept afterwards as a stored copy. We do not keep a
record of which VAT numbers you checked.

## Where things run

Core infrastructure runs in the **EU**. We use a small number of infrastructure and service
providers to operate the connection and to send account notifications. The authoritative,
current list of subprocessors is maintained in the AV/DPA, not on this page.

## Your AI assistant is a separate relationship

AI VAT Number Validation is the connection between these registers and your AI assistant. The
assistant itself (for example Claude or ChatGPT) is operated by its own vendor, under your own
account and agreement with that vendor. Connecting this does not change or extend that
relationship, and does not make us a party to it.

Anything you type into your assistant reaches that vendor before it reaches us. That is worth
knowing whichever connection you use.

## Data residency

Your data is hosted in the **EU**.
