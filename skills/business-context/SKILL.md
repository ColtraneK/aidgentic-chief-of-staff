---
name: business-context
description: Research the person's business from public sources, draft what you found, and have them correct it — then connect their calendar, email and files on a permissioned basis and enrich the draft from what those show. Writes Business Context.md, the file every other skill reads first. Trigger when the user says "tell you about my business", "set up my context", "update your context", "you don't know enough about my business", "here's how my business works", "that's not how we work", "make these corrections", "you keep getting this wrong", "stop treating X as", "that's not right about", "connect my tools", "connect my email", "hook up my calendar", "add a connection", "what can you see", "why can't you see my email", or when the setup command reaches its context or connect stage. Also use when a brief or dashboard is visibly wrong because the underlying context is thin or stale.
---

# Business Context

This is the file that makes the difference between a search tool and a chief of staff. Every other skill reads it first.

Read `${CLAUDE_PLUGIN_ROOT}/reference/voice-and-ground-rules.md` and `${CLAUDE_PLUGIN_ROOT}/reference/operating-models.md` before starting.

---

## The order, and why it's this way round

**Research first. Confirm second. Interview never.**

Go and find out what you can from public sources, draft the context file yourself, then show it to them and ask them to correct it. **People are far better at fixing a wrong draft than at answering an open question about their own business.** "How do you make money?" gets a shrug and a sentence. "Here's how I think you make money — which of these is closest?" gets a correction, and the correction is worth ten times the sentence.

It also means the whole thing works with no connectors at all. Someone who can't or won't connect an account still ends up with a real, populated file.

**If they're only here to add a connector** — they said "connect my email," nothing else is wrong — skip to *Connect what it can see*, do that, update **What's Connected**, and stop. Don't drag someone into a context conversation when they asked you to fix one thing.

---

## Step 1 — Ask for the two things you can't find

One turn, and it's the only typed answer in the whole build.

> "Two things and then I'll go do the reading: your website, and your name as it appears on it."

**Ask it in plain prose and wait for them to type. Never put this in a picker.** Neither answer can be enumerated — you cannot offer someone a choice of what their own URL is — so a picker here either fails validation for want of real options or insults them with guesses. Every other question in this skill is clickable; this one is not, and that is deliberate.

**The website** is the seed for everything. **Their name** is what lets you learn about the person rather than only the company — in a founder-led business those are not the same subject. The site says what it sells; the person's history says what they actually do all day and what they're trying to build.

No website? Take the business name and the city, or a LinkedIn URL. Say it'll be a thinner draft and carry on. Never make this a negotiation.

---

## Step 2 — Research, and be thorough about it

This is the stage that earns the whole design. Budget about a minute of real work, and do it properly — a shallow pass produces a draft so generic that correcting it is more effort than answering questions would have been, which loses the entire advantage.

**On the business:**

- The homepage, and what it leads with
- The about, services, pricing and team pages — pricing especially, because it tells you how the money works without asking
- Case studies, client logos, testimonials — this is where the real client type lives, not on the services page
- A search on the business name, for press, directories, reviews, anything they didn't write themselves

**On the person, by name:**

- LinkedIn — headline, current role, history, what they post about
- Interviews, podcast appearances, conference bios, guest articles
- Anywhere they describe the business in their own voice rather than in marketing copy

**Date what you find.** Anything you carry into the file from a page carries the page's date, per `${CLAUDE_PLUGIN_ROOT}/reference/grounding-outside-sources.md` — a pricing page from two years ago describes a business that may not exist any more, and an undated claim written in as fact is the kind of thing they correct once and never trust again.

**If the search turns up little on them**, say so and offer the browser rather than giving up:

> "Not much comes back on you by name from search. If you open LinkedIn in the browser I can read your profile from there — thirty seconds, and it's the difference between me knowing what the company sells and knowing what you actually do."

Take no for an answer immediately and carry on with what you have.

---

## Step 3 — Triangulate, and keep the disagreements

You now have up to three accounts of the same business: **what the site says**, **what they say about themselves**, and — once connectors are in — **what their calendar and inbox show them actually doing.** These will not fully agree, and where they don't is the most valuable thing you found.

A site selling three services where every case study is one of them. A LinkedIn headline describing work the site doesn't mention. A services page about strategy and a calendar full of delivery calls.

**Don't silently pick one.** Put the disagreement in the draft as a line they can correct:

> "Your site leads with fractional CFO work, but eight of your last ten meetings look like bookkeeping and monthly close. Which one is the business right now?"

That single question does more than any interview round, and it's only askable because you looked first.

---

## Step 4 — Draft the file, then ask two questions

Write `Business Context.md` from research. Fill in everything you can infer, mark inferences as inferences, and **show it to them**. They should be reading their own business back before they're asked anything.

Then two questions, both clickable, both drawn from what you just read. Not three, not six.

**Question one — what the business is.** Three real phrasings taken from their own material, plus their own words if none fit.

> "Here's how I'd describe what you do. Which is closest?"
> - Fractional CFO work for design studios and restaurants in Brooklyn
> - Books and tax for small businesses and nonprofits
> - An accounting practice — books, tax, and part-time CFO work

**Question two — what they're trying to move.** Their goals, not their billing model. This is the one that shapes every judgment downstream, and it's the one research can only guess at.

> "What are you actually trying to move this year?"
> - Fewer, larger clients — trade the small monthly work for advisory
> - More of the same — capacity is the constraint, not demand
> - Get the practice off my desk so it runs without me
> - Something's broken and I need to see it clearly before deciding

Draw the options from what you found: their pricing page, what they post about, what they said in an interview, what the site is plainly trying to sell. **Generic options waste the research.** Four plausible-sounding goals that could belong to any business teach them the options aren't real, and they'll click the first one.

**Don't ask about money directly.** How the money works is derived — from pricing pages, from the profile in `operating-models.md` their answers point at, and from invoices and proposals once mail is connected. Ask what they're trying to move, and the money framing follows from it.

**Don't ask about vocabulary either.** Take their nouns from their own site copy and their own answers, write them into the Vocabulary table, and let the correction loop fix what you got wrong. A person who calls them *matters* has written *matters* on their website forty times.

Then write the file and show it. Something has to happen before you ask anything else.

---

## Step 5 — Connect what it can see

Say the permission story in plain language first. Thirty seconds, out loud, not buried in a caveat. For a lot of people this is the deciding moment.

- **Each tool is granted separately.** Calendar doesn't imply email.
- **It's revocable.** They can pull any grant at any time, from their own account settings, without asking anyone.
- **It reads.** It does not send email, reply, change calendar events, or touch a client system. It writes only into their workspace.
- **The files are theirs.** Everything it learns lands as plain text they can read, edit, or delete.

### Roles, not products

Sort what's available into four roles. The person cares about the role; the product name is an implementation detail.

| Role | What it gives the chief of staff | Typical |
|---|---|---|
| **Calendar** | the shape of the day, who they're meeting, what just happened | Google Calendar, Outlook |
| **Email** | commitments, asks, what's gone quiet, what's already been sent | Gmail, Outlook |
| **Files** | proposals, contracts, budgets, notes | Google Drive, OneDrive, Dropbox, or the workspace itself |
| **Everything else** | the systems the business actually runs on | CRM, accounting, project tool, chat, forms |

**Calendar first** — it's the fastest grant, it almost always succeeds, and it gives an early win. **Email second**; it carries the most signal. **Files and everything else are not part of setup** — offer them the first time something is missing that they'd have caught. Three consent screens in a row is where a first-time person gets lost, and files is the one whose absence costs least.

### One at a time

Request one grant. Wait. Confirm it worked by reading something small — the next three calendar events, the five most recent email subjects — and show them what came back. **Seeing real data from their own account is the moment this becomes real.** Don't summarize it; show the actual subject lines.

If a grant fails or stalls: **don't debug it in front of them.** Note it, say what they'll be missing, move on.

> "Calendar's in — I can see three meetings tomorrow. Email didn't take; we'll come back to it. Without it I won't catch commitments that live in threads, but everything else works."

### The long tail, later

Once the brief is running, one question is worth asking: *"What else does the business actually run on — a CRM, your books, wherever bookings or cases come in?"* Connect at most **one**. Naming their actual system beats connecting three generic ones. If there's no connector for what they name, say so and record it under **Blind Spots** — a known gap is manageable, an unknown one isn't.

---

## Step 6 — Enrich from what you can now see

Connectors turn the researched draft into a specific one. Go read, then bring back what you found and **ask them to confirm or correct it** — never write inferences in as fact.

Apply the prior-contact test from `${CLAUDE_PLUGIN_ROOT}/reference/inbox-triage.md` before proposing anyone. A cold sender who emailed four times in a sequence looks exactly like a recurring name, and putting one into **Who Matters** poisons every brief afterwards — this file is supposed to be the thing that *prevents* that mistake.

Look for:

- **Recurring names.** Who appears repeatedly in calendar and inbox over the last 30 days, and passes the prior-contact test? **Write these in with their sources rather than asking about them** — a question you could have answered by looking is a question not worth their attention. The correction loop on the first dashboard catches what you got wrong.
- **The rhythm.** Standing meetings, weekly patterns, when their days start and end, which days are meeting-heavy.
- **Money signals.** Invoices, proposals, contracts, grant correspondence. Not amounts — the shape: who owes whom, and what's outstanding.
- **Their own commitments.** Search **sent** mail, last 14 days, for the phrases people commit in — "I'll send," "I'll get you," "by Friday," "let me put together," "circling back," "next week." This search alone usually produces something they'd forgotten.
- **What's gone quiet.** Threads with a real back-and-forth where the last message is theirs and it's been more than a week.

---

## Write the file

`Business Context.md` in the workspace root, resolved per ground rule 7a.

```markdown
# Business Context

*Written [date]. Updated as things change — say "update your context" any time.*

## The Business
[one paragraph, in their words where you have them. What they do, for whom, and what makes it work.]

**Operating model:** [profile name — derived, not asked]

## What They're Trying To Move
[Their answer to question two, concretely. This is the standard the brief measures against.]

## Vocabulary
The words used in this business. Use these, not generic substitutes.

| Concept | Their word | Where it came from |
|---|---|---|
| unit of work | [matter / booking / grant / project / case] | [their site / their answer] |
| the people who pay | [client / funder / customer / patient] | |
| the pipeline | [caseload / grant cycle / bookings] | |

## Who Matters
| Who | What they are | Why they matter now | Source |
|---|---|---|---|
| [name] | [client / funder / partner] | [one line] | [the email, meeting or page it came from] |

## What Money Looks Like
[Retainers, grants, deposits, invoices — however it actually flows. Derived from their pricing and their mail, marked as inferred until confirmed.]

## Fixed Points
Things that cannot move. Dates, filings, renewals, reports.
- [thing — date — consequence if missed]

## Rhythm
[Standing meetings, weekly patterns, when the week starts and ends, which days are heavy.]

## Currently Behind
[From sent mail and their notes, each with a date and a source. Not asked — found.]

## Open Questions
Things the research disagreed with itself about, or couldn't settle. Cleared as they're answered.
- [what the site says] vs [what the calendar shows] — [which is right?]

## Blind Spots
What the chief of staff cannot see, and what that means in practice.
- [system — what lives there that won't surface]

## Corrections
Things it got wrong once and shouldn't again. Newest first.
- [YYYY-MM-DD] [what it assumed] → [what's actually true]

## Already Suggested
Ground rule 10 gives one chance per thing. This is what remembers it was used.
- [YYYY-MM-DD] [what was suggested] — [declined / said later / done]

## What's Connected

*Last checked: YYYY-MM-DD*

| Role | Source | Status | Notes |
|---|---|---|---|
| Calendar | [source] | connected | |
| Email — received | [source] | connected | |
| Email — sent | [source] | connected | *searchable by address and by domain: [yes / no]* |
| Files | [source] | not connected | |

**Not connected:** [role — the consequence, in one clause]
**No connector available:** [system — what has to be handled by hand]
```

Under "not connected," write the consequence, not the fact. Not "email not connected" but "email not connected — commitments made in threads won't surface."

**Sent mail gets its own row, and it is not a formality.** The reply gate in `deriving-the-picture.md` runs on it, and a mail grant that reads the inbox but can't search sent messages produces the worst output this system has: telling someone to chase a client they answered last night. Check it at connection time by running one real search, and record what came back. If sent mail can't be searched, say so here and in **Blind Spots** — every claim that someone hasn't replied then softens to what can actually be seen.

**What's Connected is a registry, not a note.** Every scheduled run reads this table to decide what to check, rather than working from a fixed list written into the task months ago. Two things follow, and both are worth saying out loud when someone adds a connector:

- **Adding one is enough.** Nothing needs rebuilding, no task needs recreating. *"That's your books connected — every brief from tomorrow includes it."*
- **A row here is a promise that the thing gets checked.** So don't list something that isn't really reachable, and when a grant expires, change the row rather than leaving it saying `connected`.

**When they mention a system you have no connector for**, record it under **Blind Spots** with what lives there — a known gap is manageable, an unknown one isn't — and say plainly that it's out of reach for now rather than implying it might work.

**Mark what's inferred, and hedge it in the sentence.** A source is not enough on its own — *"X is an AI automation agency (thesite.com)"* still reads as fact, where *"reads like an AI automation agency, from how the site pitches it"* is the same thing delivered honestly. Write a guess as a guess: *reads like*, *as far as I can tell*, *from one interview, so possibly stale*.

Only what you read out of a connected account is a fact, and even then report the observation rather than the conclusion — a recurring payment is a recurring payment, not proof of a productized offering. A confident wrong claim about their own business is the fastest way to lose them.

---

## The deep read comes later, and it does the heavy lifting

Everything above is what can be established in fifteen minutes. It is deliberately thin.

The **deep-read** skill runs unattended on the first scheduled run and reads *months* of threads and calendar — who they really deal with, what they get asked for, their actual role, their rhythms, what precedes work that lands, and what reliably falls through. It writes back into this same file.

So don't try to do that work here, and don't apologize for what's missing. Say it once, at the close, as something that's already arranged:

> "That's what I could work out in a few minutes. Tonight it goes back through the last several months properly — your first brief will know a lot more than I do right now."

---

## Corrections — the loop the whole thing runs on

Someone opens a chat and says what's wrong. This is the most important thing that happens after the first brief, and it has to change behavior rather than politely logging a note.

**Read how much they gave you before you touch anything.** A dense correction — three things, specific, with names — is a rewrite session: work it through and confirm at the end. A thin one — *"that's wrong," "the brief's off"* — is worth exactly one question first: *"Which part?"* Guessing at a thin correction and rewriting the wrong entry costs far more than asking does, and it teaches them that correcting you is risky.

Then three moves, in order.

**1. Find everywhere it's true.** A correction is about their business, not about a file. *"Marguerite isn't a client any more"* is true in the People roster, in anything currently ranking her as live, and possibly in a standing task chasing her. **Look before you edit — the second place is the one that gets missed.**

**2. Change it where it lives, in whichever form fits.**

| The old thing is | What to do |
|---|---|
| Now false — a relationship, a date, a word, a role | **Rewrite it**, and move the old version to **Corrections** with the date |
| Still true, just incomplete — another person, one more fixed point | **Append** |
| A judgment of yours they're overruling | Rewrite, and record what the evidence had been, so a later run doesn't re-derive the same conclusion and quietly reverse them |
| About what the weekly primer covers, not about the business | **Not this file.** `Learning Log.md` → **What they've said**. This file is what the system knows about their business; that one is what it knows about their reading |

Annotating under a wrong entry and leaving the entry in place is how a system agrees with you and then does the same thing tomorrow.

**3. Say what changes, not what you edited.** They don't want a changelog; they want to know the thing they corrected is actually fixed:

> "Marguerite's marked as a past client, so she drops out of *Gone quiet*. The Tobias task is retired — that frees a slot. And it's engagements, not projects, starting with tomorrow's brief."

**The one that's easy to miss, and it's the expensive one:** a correction that should have changed something *running* and only changed a file has not been applied. They can see the file; they cannot see the schedule. If they say stop chasing Tobias, the task is retired, not annotated. If they say send it at six, the task's prompt is rewritten — see `${CLAUDE_PLUGIN_ROOT}/reference/scheduled-runs.md`. **Say the schedule out loud when you've changed one**, because it's the only part they have no way to verify.

**Never argue with a correction.** They know their business. Apply it, keep the evidence as context rather than as a defense, and move on.

---

## Keeping the file worth reading

This file is read at the start of every session, so its length is a cost everyone pays. Left alone it only grows.

**The People tiers do most of this on their own.** Active, Background and Dormant are maintained by every deep read and by every correction that touches someone — no cap, no pruning, nothing deleted. A relationship that goes quiet drops to one line; a name that reappears in the mail comes straight back up with its history. That's the mechanism, and it needs no permission because nothing is lost.

Two things it doesn't handle, and both are worth mentioning **once** when they're true:

**Corrections older than a year** can collapse into a few standing rules — *"uses 'engagements', not 'projects'. Doesn't want the newsletter surfaced."* Those are the durable part; the dates and the incidents aren't. Offer it, don't do it.

**A file that's grown past what a session should carry** — long enough that reading it is noticeably slow — usually means something is being recorded that should live elsewhere: session detail belonging in `03 Session Notes/`, or an inventory belonging in a file of its own. Say what you'd move and where. Never restructure their file without asking.

---

## When updating rather than creating

Never rewrite the file wholesale. Add to the relevant section, keep what's still true, and move anything superseded into **Corrections** with the date. Then say in one line what changed — they should be able to see what you did without diffing it.

---

## Close

Show them the file. Then one line, and it should sound like this:

> "That's what I know. It'll get better every time you tell me I'm wrong."

Don't summarize the file back to them. They just read it.
