# Inbox Triage

**Read this before ranking anything.** It runs as a gate, not as a scoring adjustment.

Cold outreach is written by people whose job is to make a stranger's email feel like an obligation. It is deliberately built to trip the exact priority rules this system uses — *the ball is in your court*, *money is on the table*, *this is decaying*. "Following up on my note from last week, can we find fifteen minutes?" hits two tiebreakers perfectly and means nothing.

If ranking runs first and filtering second, a good cold sequence will beat a real client every time. So relationship gets established first. **Only verified counterparties are eligible for the ranked sections at all.**

---

## The prior-contact test

A sender is a **verified counterparty** if any one of these is true:

1. The person has **sent mail to that address or that domain** at any point — a real message, not an auto-reply or an unsubscribe.
2. They have **shared a calendar event** with that person or domain. **A calendar entry that names only an organization, with no attendee address, verifies the organization — not the sender.** Someone writing in cold from a company that once appeared on the calendar is still a stranger. Note the organizational footprint on their line and leave them unverified.
3. The sender is **named in `Business Context.md`**.
4. The person **replied in a thread this sender started**, at any point in the past.
5. The sender was **introduced by someone who passes 1–4**, in a real intro thread the person took part in.
6. The sender is **the counterparty on something recorded in the workspace** — an engagement letter, contract, lease, invoice, proposal or obligation. The *person* need not be named: a landlord writing about a lease that's in their files, an insurer about a policy, a registrar about a domain they actually own, all pass on the matter even when the individual is new.

None of these true → **unverified**. Unverified mail never enters *Needs you now*, *Needs you today*, *Your commitments*, or *Gone quiet*. No exceptions, no matter how urgent it reads.

**Domain is usually the right unit, not the address.** A new person at a firm they already work with passes on the domain. But a large shared provider is not a relationship — `gmail.com`, `outlook.com`, `icloud.com`, `proton.me` and similar must match on the full address, never the domain.

**Search the whole history for verification, not the gathering window.** Finding what's live uses the last 21 or 30 days. Establishing whether someone is a stranger uses everything available. If the mail search is limited to a window, say so in the map — *"no prior contact in the last 90 days"* is a weaker claim than *"no prior contact,"* and the difference matters when the verdict is "stranger."

**The Step 1 sent-mail index does not settle this test** — it is window-bounded by design. Finding a sender in it verifies them; not finding them means nothing, and the unbounded search still runs.

---

## Claims are not evidence

Cold email routinely manufactures the appearance of history. Treat all of this as unverified until checked against actual mail:

- **"As we discussed" / "following up on my last email" / "circling back"** — check for the prior message. If there isn't one, the follow-up is the first contact, and that's worth noting.
- **A `Re:` subject with no earlier message in the thread.** Fabricated continuity.
- **"Your colleague suggested I reach out"** — check whether that colleague exists in their mail.
- **A named referrer** — verify the referrer is a real contact before giving the mail any weight.
- **An invoice, renewal or payment notice from an unverified sender.** This is the highest-risk category in the entire inbox and the one where a wrong call is expensive. Never surface it as money owed. Surface it as *an unverified payment request*, and say plainly that no prior relationship with the sender was found.

When a claim of prior contact fails verification, **say so** — that's a useful finding, not a silent drop.

---

## Which rule wins

A single message often trips several rules at once. Resolve in this order, top wins:

1. **Never drop silently: an unverified demand for payment on a claimed existing obligation, or any request for credentials, login, or account action.** A renewal notice, an overdue invoice, a suspension warning, a password or verification request. It always gets a line, always as an *unverified payment request*, never as money owed. A no-reply address and a manufactured deadline are exactly what a fraudulent invoice looks like — the signals that would otherwise silence it are the reason to report it.

   **This does not cover priced sales pitches.** A sponsorship deck listing tiers, a quote, a product price list — those are offers, not claimed obligations, and they drop under the normal rules. The test is whether the sender asserts that money is already owed or that an account is at risk.
2. **A failed claim of prior contact is always worth reporting**, at minimum as one aggregated line — even when the message also trips mass-send signals.
3. **Then** the mass-send rules below, which drop silently.
4. **Then** the cold-pattern rules.

---

## Mass-send signals

Any one of these means it went to a list. Drop it silently — it never appears anywhere, unless rule 1 or 2 above applies.

- A `List-Unsubscribe` header, or an unsubscribe or preference-centre link in the body
- `Precedence: bulk`, `Precedence: list`, or list-management headers
- A no-reply sender, or a `Reply-To` on a different domain from the `From`
- Sender is `info@`, `sales@`, `marketing@`, `team@`, `hello@`, `newsletter@`, `notifications@` **and** the sender is unverified
- Tracking pixels, click-wrapped links, or a body that is mostly images
- Near-identical wording to another message from a different sender — a sequence template
- Generic salutation, or a salutation with a name that doesn't match how anyone addresses them

Automated mail from services they actually use — a booking notification, a payment receipt, a calendar invite — is not outreach. It's a **system signal**: use it as evidence for a verified counterparty, don't list it as a message needing attention.

---

## Cold-pattern signals

Unverified plus **two or more** of these means it's a sales sequence, not a person:

- A calendar or booking link on first contact
- A specific short meeting ask — "15 minutes," "a quick call," "20 minutes Thursday"
- Manufactured urgency or scarcity — rates increasing, a closing window, limited spots
- Templated personalization — a job title, company name or recent post dropped into an otherwise generic body
- Flattery about their work followed by a pivot
- A "breakup" or guilt frame — "should I close your file?", "I'll stop reaching out", "did I lose you?"
- A pitch for a service the business plainly doesn't buy
- Third message or later in a sequence with no reply from them

---

## Not everything unfamiliar is cold

**A first-time inbound inquiry is one of the most valuable things in the inbox**, and a filter that kills it is worse than no filter. The distinction is simple:

> **Who is proposing to pay whom?**

If the sender is asking about **their** services, availability, pricing, capacity, or describing a need this business exists to solve — that's a **possible new [client / booking / matter / inquiry]**, in their words. It is unverified and it does not go in the ranked sections, but it gets its own line, near the top of the unverified block, and it is never described as spam.

Signals that separate a real inquiry from a pitch:

- They describe **their own** situation, not their product
- They reference something specific and true — a real referrer, an actual page, a service the business really offers
- They ask a question only this business can answer
- The ask is for **the business's** time on the business's terms, not a demo of something else
- No unsubscribe, no sequence markers, written like a person

When it's genuinely ambiguous, surface it as a possible inquiry and say why you're unsure. A false positive here costs one line; a false negative costs a client.

### The name-drop problem

Most real referrals arrive as name-drops. The referrer mentions the business over coffee; the prospect writes in cold, with no intro thread anywhere. A rule that requires a verified intro thread classifies the best growth channel in a small business as spam by construction — and cold outreach name-drops real contacts too, precisely because it works.

So a named referrer is **corroboration, not a credential**, and the who-pays-whom test is what separates the two:

- **Named referrer is a real contact of theirs, and the sender is asking to buy** → a **corroborated inquiry**. Still first contact, still unverified, but this is a live lead and should read like one. Say the referrer checks out.
- **Named referrer is a real contact of theirs, and the sender is selling** → still cold. The name-drop is a flag, not a credential; report that the referrer was named and no introduction appears.
- **Named referrer doesn't exist in their mail at all** → cold, and say so.

### Genuine inquiries get a next step

The no-next-step rule below exists to stop the system acting as a delivery mechanism for sales sequences. It is not meant to strand a real prospect.

**A possible new client, booking, matter or inquiry gets a next step** — "a reply," "twenty minutes on the calendar," "the intake form." It stays under *First contact*, plainly labelled as someone with no prior history, but a live prospect with no suggested action is a filter doing damage.

**Cold outreach never gets a next step.** That distinction is the whole point.

---

## How to report unverified mail

At the bottom, after everything ranked. Compact.

```markdown
## First contact — unverified
No prior contact found. Listed separately, not ranked.

- **Possible new [client]:** [Name] — [what they're asking about, one clause] → [next step] *(no prior mail; [referrer] named — [checks out as a real contact of yours / not found in your mail])*
- **Unverified payment request:** [what, from whom] — no prior relationship with this sender found in your mail or files.

**Cold outreach:** [n] messages from senders with no prior contact, filtered out. [If any claimed a referrer or earlier contact that didn't check out, one line covering all of them.]
```

Four rules for this section:

1. **Never inherit their urgency.** Not "waiting on your reply" — "cold outreach from Northbeam offering a pricing tool." Neutral, and their framing goes in quotes if it goes in at all.
2. **Never attach a next step to cold outreach.** Recommending action on a sales sequence is how a filter becomes a delivery mechanism. Possible new clients are the exception, per above.
3. **Cold outreach gets a count, not a list.** Reproducing five subject lines just delivers the sequence a second time. Failed referrer claims are summarized in one line across all of them, not itemized.
4. **Unverified payment requests are always named**, with what they're demanding and what makes them unverified. Never a link, never a total presented as owed.

---

## When the test can't run

If sent mail isn't connected, the prior-contact test can't run on signals 1 and 4, and the filter is much weaker. Say so explicitly in the *What I couldn't see* line — something like: *"Sent mail isn't connected, so I can't confirm prior contact. Anything from an unfamiliar sender is marked unverified and left out of the ranking."*

Then be conservative: with no way to verify, unfamiliar senders stay unverified. **Under-surfacing a real message costs a day. Surfacing a stranger's sales sequence as a priority costs trust in the whole brief.**
