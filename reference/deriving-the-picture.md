# Deriving The Picture

How the chief of staff works out where things actually stand. Read this before the morning brief and before the dashboard — they are the same derivation at two zoom levels, and they must not disagree.

Read `inbox-triage.md` and `operating-models.md` alongside this, and the workspace's `Business Context.md` before gathering anything.

**Establish the time and the timezone first**, per ground rule 7b. Every window below is measured from *their* now, not from an assumed morning.

---

## The two scopes

Everything below runs the same way. Two things change.

| | **The whole picture** — the dashboard | **Today's slice** — the morning brief |
|---|---|---|
| How far back | 21 days, and 7 forward | Mail since the last brief: 24h on a weekday, 72h after a weekend. Calendar: today, plus tomorrow for prep. |
| The cap on the top section | Seven | Five |
| Step 8, the repeat check | Yes | No — that's the dashboard's job |

The brief is today's slice of the dashboard, not a second opinion. When the brief says something the dashboard didn't, it's because something arrived overnight — never because the two ranked the same evidence differently.

---

## The rule that makes this work

**Never assume a roster.** Do not start from a list of people or projects — not from `Business Context.md`, not from last week's picture. Derive who and what is live from signals, every single time, then use `Business Context.md` to interpret what you found.

A picture built from a remembered list tells them what they already know. One derived from signals tells them what they've forgotten. Only the second is worth the wait.

**If `Business Context.md` doesn't exist** — first run, or they skipped setup — don't stop. Derive what you need from the files in the workspace and the shape of their mail: infer the operating model, use neutral vocabulary until you learn better, and treat any client roster, engagement list or notes file as the Who Matters list. Say in one line at the end that it ran without a context file and would be sharper with one. **This is the run where it matters most, so it has to work.**

---

## Step 1 — Collect candidates

**Which sources exist is not a fixed list.** Read `Business Context.md` → **What's Connected** and gather from every row in it. Someone who connects their books in month three should see that in the next brief without anything being rebuilt, and that only happens if the gathering reads the registry rather than assuming mail and calendar.

From every connected source, over the window for your scope:

- **Calendar** — every external attendee on a meeting in the window, and on the next 7 days. **Read the calendar rule below before you trust a single query.**
- **Email received** — anyone who wrote to them, or replied in a thread they're in.
- **Email sent** — anyone they wrote to, including one-way sends with no reply.
- **Files** — documents created or modified in the window, and who they're about. Also any roster, engagement list, aging report or notes file regardless of date.
- **Other connected systems** — whatever the CRM, books, or project tool says is open.
- **`Business Context.md`** — fixed points and currently-behind. **`Standing Work.md`** — anything a standing task proposed or did since the last run.

Any source unavailable: mark it and continue. Never block.

**Capture the link for everything you gather.** Every message and event, keep its permalink alongside the content. Going back for it afterwards costs an extra pass. If a tool doesn't return one, note that it didn't.

### The sent-mail index — one pull, before any thread is opened

**Pull sent mail for the whole window in one query here, in the gathering.** Not per counterparty, not per thread, not as a second pass while writing a line. The per-item version of this check is the one that gets skipped; a single query at the top either ran or it didn't.

- **Bounded by the scope's window** — 21 days for the whole picture, since the last brief for today's slice — and **never by a message count**, which truncates a heavy week and overreaches on a quiet one.
- **Indexed by recipient address and by domain**, To, CC and BCC alike. Keep each entry's thread and its send time, normalized to their zone.

What it settles, and what it can't:

- **It clears an item on its own** — a sent message to that address or domain after the message being called unanswered means they answered, and no thread needs opening.
- **It never establishes silence on its own.** An empty entry is where the gate's deeper checks start.
- **It is not the verification test**, which searches the whole history. "Not in the index" never means "no prior contact."
- **An index empty across the whole run is a broken connector**, per Step 2b.

### The calendar may not be enumerable, and it will not tell you so

Some calendar connectors expose only **semantic search** — no list-by-time, no "next event." That tool answers the question "does anything match these words" and it will happily answer "no" for a day that has four meetings on it.

Observed behavior worth planning around: a query for *"next upcoming appointment this week"* returned nothing at all, a query for *"upcoming events meetings"* returned a single event **from the previous year**, and only a broad query on the person's own name returned a usable set.

So:

- **Never treat one query's result as the calendar.** An empty result is evidence about the query, not about the day.
- **Over-fetch, then filter yourself.** Run several broad queries — their own name, their company name, the names in **Who Matters**, plain words like "call", "meeting", "review" — union the results, deduplicate by event id, then filter by date in your own head. Cheaper than being wrong.
- **Check the date on every event you get back.** Semantic search returns things from other years that read as relevant. An event dated last August is not on this week's calendar.
- **If a list-by-time call exists, use it and skip all of this.** Check first.

**When you cannot establish the day's events with confidence, say so instead of asserting the shape of the day.** This matters most in the brief's opening line. *"Two calls, a clear afternoon"* is a claim about the whole day; if the calendar could only be sampled, the honest version is *"Two calls that I can see — my view of your calendar is partial today."* A confident summary built on a search that silently missed three meetings is exactly the failure ground rule 8 exists to prevent.

---

## Step 2 — Verify before you rank

**Run `inbox-triage.md` in full here.** This step happens before ranking, not after, and nothing skips it.

Cold outreach is written to trip the exact tiebreakers in Step 7. If you rank first and filter second, a well-written sales sequence outranks a real client every time.

1. **Apply the prior-contact test** to every sender.
2. **Drop mass-sends silently** — with the exceptions `inbox-triage.md` names, which are never dropped silently.
3. **Verify any claim of prior contact**, searching sent mail **without a date limit** — the gathering window finds what's live, verification needs the whole history. If the search is limited, say so: "no prior contact in the last N days" is a weaker claim than "no prior contact."
4. **Separate real inbound inquiries from pitches** by asking who is proposing to pay whom.
5. **Also drop:** recruiters, and personal or family mail. Routine vendor billing drops too — **but a vendor decision with a deadline is not routine billing.** A lease or insurance renewal, a contract coming up for signature, a rate change requiring a response is a real fixed point.

**Unverified senders never enter the ranked sections.** They appear only in *First contact*, per the reporting rules in `inbox-triage.md`.

Among **verified** counterparties, when unsure, keep and mark low. That leniency does not extend across the verification line.

---

## Step 2b — The reply gate

**A second gate, run here, before anything is ranked.** Not a check you do later while writing the line — by then the item has already been sorted as though nobody answered, and the ranking is built on it.

Telling someone to chase a person they replied to yesterday is the single fastest way to lose their trust in the whole system, and it is the failure this plugin has actually produced in the field. The rules below existed as advice further down this file and were skipped. They are a gate now.

**When it has failed, it has failed by being half-followed** — a shallower call standing in for the enumeration, or the search stopping at the message it went looking for. That's why the first check happens once, up front, in Step 1.

### What the gate covers

Every candidate whose place in the picture depends on **the person not having answered** — *needs you*, *gone quiet*, *ball in their court*, *waiting on you*, *unanswered*, *no reply*, an overdue commitment of theirs. If the item survives only because of an assumed silence, it goes through this gate.

**And every candidate whose place depends on something not having been settled** — *still pending*, *still open*, *awaiting a decision*, *not signed yet*. Nothing in the mailbox saying a thing was done is not the same as the thing not being done. See *Resolved somewhere you can't see it* at the end of this step.

### The checks, in order

1. **Look the counterparty up in the Step 1 index**, by full address and by domain. A sent message timestamped after the message in question closes the item — answered, not waiting, out of the gate here. One pass, every candidate, before any thread is opened. **If the index wasn't built, build it now**; nothing gets ranked off a gate that skipped its first check.

2. **Open the thread and enumerate every message — a full thread fetch, not a search result.** Search and list calls return matching messages with snippets; they are summaries and they drop messages, including the person's own.

   - **Sort by timestamp and name who sent the last message.** If you can't name it, the gate hasn't run on that item.
   - **Read past the inbound message.** Finding what you came for is the middle of the check, not the end — the observed failure is exactly this: four replies sent later the same day, never read, the thread called unanswered for four days.
   - **Compare timestamps, not dates.** A reply hours after the message it answers lands on the same calendar day.
   - Thread endpoints have been observed returning a thread without the person's own reply inside it, and a reply mid-thread is the one most often missed. First-and-last is not enumeration.

3. **Search sent mail directly for what the index can't key on** — their name, a subject fragment, another address of theirs, and past the window's edge when the thread started before it. Steps 1 and 2 coming back empty is the reason to run this, not a reason to skip it.

4. **Check the shapes that sit outside the thread.** A reply sent as a new message rather than a reply. A reply nested under a forward. A reply that quoted the message instead of threading to it.

5. **Only after 1–4 come back empty** may a line say the ball is in their court.

**Normalize every timestamp to their zone before comparing dates.** Connectors return message times in UTC, in the sender's zone, or in whatever the account is set to, and they don't say which. A reply that looks like it predates the message it answers, or a thread whose last message lands a day off, is a zone artifact — not evidence. Where the order of two messages decides whether someone replied, say which zone you worked in.

### A silence claim carries its receipt

Every line asserting that someone hasn't answered records, on its evidence line, **what was searched, how far back, and who sent the last message in the thread**:

> *Priya Venkatesan — no reply. Sent-mail index, 21 days by address and by @venkatesanpartners.example: nothing since Aug 4. Thread fetched and enumerated, 4 messages, last is Priya's, Aug 11 14:02 ET.*

**The last sender and their timestamp are the load-bearing part.** "Thread enumerated," without saying what the enumeration found at the end of it, is the failure with a receipt stapled to it.

No receipt, no claim. The line softens to what is actually known — *"the last message I can see in this thread is Priya's, on the 11th"* — which is true, useful, and cannot blow up in their face.

This is not bookkeeping for its own sake. The receipt is what makes the omission visible: a line asserting silence with no record of a sent-mail search is a line nobody ran the search for, and that is legible on the page instead of arriving as a correction from the person a day later.

### An empty sent-mail search is a failure signal, not evidence

**This is the actual observed failure mode.** The sent-mail search returned thin, and thin got read as silence.

So: if the Step 1 index comes back **empty across the whole run** — no sent messages of any kind in the window — that is a broken or unauthorized connector, not a person who wrote no email this week. Say so in *What I couldn't see*, hold every silence claim in the run down to the softened form, and don't dress the failure up as a finding. An index far thinner than the inbox implies reads the same way.

The same applies at the item level in weaker form: if the search for a specific counterparty is inconclusive rather than clean, the claim softens. **The asymmetry is the whole point — a missed reply of theirs costs far more than a missed message from someone else.**

### If sent mail isn't connected at all

The gate cannot run. Say so in *What I couldn't see*, and no line anywhere in the output asserts that anyone is waiting on a reply. Everything becomes the softened form. A picture that hedges every silence is mildly annoying; a picture that invents one is finished.

### Resolved somewhere you can't see it

A decision made in a portal, a form signed, an invoice paid leaves no mail at all, so a thread whose last message reads *"still deciding"* is evidence about the thread, not about the decision. Observed: an item reported as pending had been settled through a portal, with no mail trace until a follow-up arrived half an hour after the brief was built.

**A later message referring to an action already taken supersedes every earlier framing of it** — *"I saw you already purchased"*, *"since you signed"*, *"thanks for getting that sorted."* That sentence is the resolution arriving out of band; it closes the item rather than updating it. Ground rule 6, pointed at the world instead of the mailbox.

**Sweep for it before ranking.** Before calling anything pending, read the counterparty's most recent messages for language that assumes it's already done.

**Where nothing is visible either way, the claim is about the mail.** *"Nothing in your mail says this was decided"* survives contact with them; *"this is still pending"* is a claim about their life, which includes a browser tab you cannot see.

---

## Step 3 — Place each survivor, with evidence

Put every survivor on the ladder for their operating model and **cite the evidence** — the email and its date, the meeting, the file path. One citation per line, minimum.

**Make the citation clickable where you can.** If the tool returned a permalink, link the citation text to it, so the picture is somewhere they act from rather than a report they read. `https://` only, never a constructed or guessed URL, and plain text when no link exists.

If the evidence doesn't support a stage, say `unclear` rather than guessing. Some real relationships have no stage at all — a dormant referral source, a landlord, an advisor. **Leave the stage off rather than forcing one.**

---

## Step 4 — Check sent mail before you recommend anything

**This is the step that protects credibility, and it is not optional.**

For every counterparty, take the last 7 days out of the sent-mail index and read the most recent message in each live thread. The index is already built; this step reads it rather than re-querying.

- Never recommend something they've already done. Recommend the true next step instead — the timing of a nudge, prep for the call, the close itself.
- When sent mail and a file, note or memory disagree about **what was done**, sent mail wins. It's evidence; the other is a claim.
- This does not mean files are worthless. A note recording a commitment, a number, or a decision is often the only place that information exists — use it, and let sent mail settle conflicts about whether something was actually sent.

### A thread is not its messages

**The reply gate in Step 2b covers this, and it has already run by the time you get here.** What's left in this step is the other half: not *did they reply*, but *what did they say* — the sent message that changes what the next step actually is.

Read the most recent sent message in each live thread and let it set the next step. They replied with a full scope document on Tuesday; the next step is not "reply to them," it's whatever their reply left open. A picture that knows a reply exists but not what was in it produces a correct silence verdict and a useless recommendation.

**Enumerate messages, never trust a thread-level summary** — same reason as the gate. If Step 2b's searches surfaced a reply the thread view didn't return, that reply is part of this thread for every purpose downstream.

---

## Step 5 — Find the commitments

Separate pass, and often the most valuable thing on the page.

**In sent mail**, last 30 days, search the language of commitment: *I'll send · I'll get you · I'll have · by Friday · by end of week · let me put together · I'll circle back · leave it with me · I'll look into · next week.*

**In their notes and working files**, the same thing in the first person — "told him I'd," "said I'd," "need to send," "haven't." People record their own broken promises in notes far more honestly than in mail, and this is usually where the most overdue item in the business is hiding.

For each, determine whether it was kept — a later sent message, a file, a calendar event that discharges it. Then sort into **due and not done** (with the date promised and how many days ago) and **coming due this week**. Don't list discharged ones.

Then the same for commitments made *to* them: things someone said they'd send and haven't. Most people track these even worse than their own.

---

## Step 6 — Find what's gone quiet

**Every line in this section is a silence claim, so every line goes through the Step 2b gate and carries its receipt.** This is the section where an unrun sent-mail search does the most damage, because "gone quiet" is precisely the verdict a missed reply produces.

Threads with genuine back-and-forth where the last message is theirs and it's been **5 or more days**, at a late stage. Also anyone **Active** in the People tiers — or in a roster or referral list in their files — with no contact in 30 days.

**Background and Dormant names don't generate quiet lines.** That's what the tiers are for: someone who last came up in March is not "gone quiet," they're just not current, and reporting them as slipping is how this section fills with noise nobody acts on. A Dormant name earns a line only when something new arrives from them — and then they're Active again anyway.

For each, say how long and where it stalled. Don't editorialize.

---

## Step 7 — Rank

Ranking is where this fails. A flat priority list produces a pile; the point is a judgment.

**First, deduplicate.** One underlying thing gets one line, even when it arrived through three signals. Unpaid invoices from one client, plus a staff question about that same client, plus an aging report line, are **one item**. Merge, and cite all three sources on the merged line.

**Then sort into two bands.**

### Band A — dated and immovable

Anything with a date that cannot move, **inside its lead time**: filing and statutory deadlines, compliance and grant reports, court dates, event and ship dates, a decision deadline that forfeits something, a board packet cutoff. Include the profile's own dated rule from `operating-models.md`.

**Lead time** is the working time the thing actually needs, plus a buffer. Work it out where you can — "four working days once the statements arrive" is a stated lead time — and where you can't, **default to 14 days**. Outside its lead time, a date belongs in *Fixed points ahead*, not in the ranking. When you've assumed, say so on the line: *"decision due 30 Sep — three weeks out, but your filing block takes most of next week."* An unstated assumption is what makes two runs disagree.

**Order Band A by date, soonest first.** Same date: the larger consequence first. Nothing else reorders it. Work backwards from each date: if something must be true beforehand — a document received, a review done, a decision made — that dependency is part of the item, not a separate one.

**Band A takes at most four of the seven slots** in the whole picture, three of the five in today's slice. At filing season or in event week, hard dates can fill the whole page and squeeze out the judgment that makes it useful. Beyond the limit, the rest go to *Fixed points ahead* with their dependencies intact, and say so: *"three further dated items moved to Fixed points."*

### Band B — everything else that hits a tiebreaker

Score each item against the five universal tiebreakers in `operating-models.md`. An item can hit several.

Order by:

1. **How many it hits.** Something tripping four rules — money named, ball in their court, meeting today, commitment overdue — outranks something tripping one. Breadth is the strongest signal that a thing is genuinely live.
2. **Then what another week of delay costs.** Judge the consequence, not the rule number. A promise 16 days overdue to a paying client outranks an unanswered invitation to an unpaid committee, even though "the ball is in their court" is a lower-numbered rule than "a commitment has come due." Rule order breaks ties between rules; it does not rank items.
3. **Then size of consequence.**

### Then cap it

**Seven for the whole picture, five for today.** Extras move down — real, but not this week's judgment. A page with fourteen urgent items has made no decision and will be read as a list.

**Say when the cap bit.** *"Four more qualified and moved to Also open."* Silent truncation looks identical to an empty week, and they need to know which one they're reading.

Anything hitting no tiebreaker and carrying no date goes to *Also open*. **Do not pad.** A short top section on a quiet week is the correct output and it's what makes a busy week believable.

**A prep item belongs in today's slice**: something tomorrow that goes better if they read, decided, or drafted today. It needs a concrete anchor — the document to skim, the number they'll be asked for, the decision to arrive holding. "Prepare for the board meeting" is not a prep item; "the finance committee will ask why Q2 program spend is under budget" is.

**Chronic conditions the profile flags** — uncollected work, unbilled time, a referral source gone quiet — are guaranteed a place *somewhere* and must never be silently dropped. They rank by the normal rules; they don't get promoted to Band A just for existing.

---

## Step 8 — Check for repeats

*Whole picture only.*

Compare against the previous dashboard state and the last four session notes.

If something has appeared three or more times without moving, say so on its line: *"Third time running — hasn't moved since July 12."*

**On a first run**, neither exists. Don't report the check as a finding and don't apologize for it. Instead look for self-documented repetition inside their own notes — "third time I've said this," a commitment restated across weeks, the same request made twice — and report it under **Circling**. That's usually the most quotable thing on a first run, so it must not end up in a footnote. If nothing is circling, drop the section rather than writing that nothing is.

A thing that keeps appearing and never moves is information. Usually the next step is wrong, it isn't actually theirs, or they've silently decided not to do it. Surfacing the pattern is worth more than surfacing the item a third time.

---

## What every rendering owes the reader

Whatever the output looks like, three things are not optional.

**The next step is a noun phrase, not an order.** "The projection." "A decision on statements." "Numbers in hand for the 3pm." Not "send the projection," and not "yes or no to Amir" — that's an order with the verb deleted. Name the thing; they decide.

**Empty sections carry a reason, and the reason matters.** "Nothing found" and "couldn't look" are different claims, and a blank heading reads as the first when it's often the second. Looked and found nothing → one short line. Couldn't look → `Unavailable — [why]`, and the blind spot goes in *What I couldn't see* as well.

**A chronic item with no data source is a blind spot, not a line.** If the profile says never to drop uncollected work but nothing can see the billing, name it in *What I couldn't see* rather than writing a contentless "check your AR." Evidence or it doesn't go in.

---

## If it's thin

Say it's thin. Don't manufacture a pattern out of four signals, and don't apologize for a quiet week. Say what you looked at, what you found, and what would make the next one better — usually a connector that isn't attached yet.
