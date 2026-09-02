---
name: deep-read
description: Read months of mail threads and calendar history in one pass to work out how this person actually operates — who they deal with regularly, what they get asked for, their role, their rhythms, what precedes work that lands, and what reliably falls through. Writes the result into Business Context.md. Runs once, unattended, on the first scheduled run, and again on request. Trigger when the user says "go through my history", "read my last year", "what do you know about how I work", "do the deep read", "learn how I actually operate", "re-read my inbox", or when a scheduled prompt asks for the first deep pass. Only fires when a Chief of Staff workspace exists.
---

# Deep Read

Setup is fifteen minutes, so it buys a thin file. This is the pass that makes it thick, and it happens while nobody is waiting.

Read `${CLAUDE_PLUGIN_ROOT}/reference/voice-and-ground-rules.md` and `${CLAUDE_PLUGIN_ROOT}/reference/inbox-triage.md` first, and `Business Context.md` before writing anything into it.

---

## When this runs

**Once, on the first scheduled run**, before that run's brief. Then never again unless asked.

Check whether `Business Context.md` already has a **How You Work** section. If it does, the pass has happened — skip it and get on with the brief. If it doesn't, do it now. That check is what makes this self-healing: a first run that dies halfway leaves no section, so the next run does it properly.

**It runs unattended, so it asks nothing.** Where something is ambiguous, write the ambiguity down rather than resolving it — the correction loop settles it later, and a wrong confident claim about how someone works is worse than an open question.

It's slow, and that's fine. Nobody is watching, and the brief that follows it is the first one they'll read. If it makes that brief twenty minutes late, nothing is lost.

---

## What makes this different from everything else here

Every other pass asks **what is live right now**. This one asks **what is true about this person**, and it needs a long window to see it.

The 21-day derivation can tell you Marguerite is waiting on a scope. Only a year can tell you that every engagement that closed began with a call inside two days, that the ones which waited a week didn't, and that six inbound enquiries died on Fridays.

**Threads, not messages.** Read at thread level and sample inside — the first message, the last, and anything that changed direction. Reading every message in six months of mail is neither affordable nor necessary; the shape is in the threads.

---

## The window

**Six months is the starting point, not the answer.** What you actually need is enough material to see a pattern three times, and a quiet inbox at six months has nothing in it. **Go back until you have signal, not until you hit a date.**

| Source | Start at | Extend when |
|---|---|---|
| Mail threads | **6 months** | Fewer than about 80 threads → go to 12 months. Still thin → 24 months, or as far back as the mailbox goes |
| Sent mail | same window as threads | — |
| Calendar | **12 months** | Fewer than about 100 events → go to 24 months. Annual rhythms need two cycles to be visible at all |
| Files | whatever is connected | — |

A consultant doing four large engagements a year and a practice doing forty small ones need completely different windows to show the same shape. The date is a proxy; the volume is the thing.

**Go the other way too.** A very busy inbox at six months may be more than can be read properly. Narrow it — three months read properly beats twelve skimmed — and say which you did.

**Say the window you ended up using, and why**, in the file and in the first brief. *"I went back two years — six months only had eleven threads in it."* That sentence is also a finding: it tells them the system is working from thin material, which is worth knowing before they trust a pattern.

**If even the longest window is thin**, say so and stop rather than inventing structure. *"Forty threads over two years isn't enough to tell you what precedes work that lands. It'll get there — this improves as the mail accumulates."* An invented pattern from four data points is the worst possible output here, because it arrives with a year of apparent authority behind it.

### When the inbox is bigger than the budget

**You are running unattended, so decide it yourself.** There is nobody to ask, and a run that stops for an answer nobody will give produces nothing at all. Judge the volume in the first minute, choose, do the work, and say what you chose afterwards.

**The default degrade, and it's usually enough:** read threads with **verified counterparties in full**, and everything else at **header level only** — subject, participants, dates, link. Cold and bulk mail contributes nothing to five of the six findings, and the sixth is still visible: an enquiry that came in and got no reply shows up in headers as clearly as in bodies.

If that's still too much, reach for these in order, cheapest loss first:

| Then | You keep | You lose |
|---|---|---|
| **Narrow the window** — twelve months to six, six to three | Everything, read properly | Long-cycle and annual patterns, which need two turns of the wheel to see |
| **Headers only throughout** | Who they deal with, how often, who initiates, what falls through | What people come to them for, and topics — the two findings that need the words |
| **Verified counterparties only, skip the rest entirely** | All six findings on the people who matter | Inbound enquiries and first contacts, so *what falls through* gets thinner |

**Three months read properly beats twelve skimmed.** When it's a choice between window and depth, cut the window.

Then **say what you did and what it cost**, in the file and in one line of the first brief — plainly, without apology:

> "Your mail runs about 200 a day, so I read your regular correspondents in full and everything else by subject line. Who you deal with, your rhythms and what falls through are solid. What people come to you for is thinner than I'd like."

**Then offer the alternative once**, as something they can take later rather than a question now:

> "If you'd rather I went deep on one part of it — just client mail, say — tell me which and I'll redo that properly."

**Interactive re-runs are different.** When someone asks for this in a session and the inbox is large, say the trade-off before you start and let them pick — they're right there, it costs one question, and they know which half of their mail matters.

**The calendar may not be enumerable.** Follow the calendar rule in `${CLAUDE_PLUGIN_ROOT}/reference/deriving-the-picture.md` — over-fetch with broad queries, filter by date yourself, and treat a long sweep as a sample rather than a census. Say which it was.

---

## What to work out

Six things. Each one is a claim about the person, so each one carries its evidence.

**1. Who they actually deal with.** Not everyone who emailed — the recurring counterparties. For each: how often, how recently, who starts the conversations, and what the relationship appears to be. Run the prior-contact test from `inbox-triage.md` before anyone goes in; a four-message cold sequence looks exactly like a recurring correspondent, and one of those in **Who Matters** poisons every brief afterwards.

**2. What they get asked for.** Read the *requests* coming at them, in aggregate. What do people want from this person? Approvals, quotes, decisions, expertise, introductions, the actual delivery? This is the single clearest signal of their real role, and it's usually narrower than their title.

**3. Their role, as their mail describes it.** Not the title on the website — what the traffic says they are. Someone whose inbox is 60% approvals and scheduling is running the business; someone whose inbox is client questions about the work is doing the work. Say which, and say what it's based on.

**4. Their rhythms.** Standing meetings. Which days are heavy. When the week starts and ends. Monthly and quarterly spikes — close, invoicing, board packets, filing season. Anything annual the calendar shows twice.

**5. What precedes work that lands.** Look at things that reached a good end — a signed engagement, a delivered project, a renewal — and look at what happened *before* each one. Compare against the ones that didn't. Time-to-first-reply, whether a call happened early, who initiated, how long the thread ran. **Only report a pattern if it's actually there in three or more cases.** Two is a coincidence, and a manufactured pattern here is worse than none because it will get believed.

**6. What falls through.** The recurring shape of dropped things. Inbound enquiries that never got a reply. Threads where they went quiet at the same stage every time. Commitments made in sent mail with nothing following. A day of the week where things die. This is usually the most valuable finding in the whole pass and the one they've never seen laid out.

---

## How to say it

The voice rules apply exactly as they do everywhere else, and this is the pass most likely to break them, because "here is what I learned about you" wants to become advice.

**Report the pattern. Never prescribe from it.**

| Not this | This |
|---|---|
| "You should call new enquiries within 48 hours." | "Four of the five engagements that closed had a call inside two days. The three that didn't close waited a week or more." |
| "You're dropping too many Friday enquiries." | "Six enquiries got no reply in the last year. Four arrived on a Friday." |
| "Your best channel is referrals — lean into it." | "Nine of your last twelve clients arrived through someone you'd already worked with. Two came from the website." |
| "You're spending too much time on admin." | "About half your inbound is scheduling and approvals." |

The finding is the value. They'll draw the conclusion faster than you will, and it'll be the right one, because they know things about their business that aren't in the mail.

**And it's a reading, not a verdict.** You are working from one partial record. Everything decided on a call, in a text, or over coffee is invisible to you, and it is often the deciding thing. So write these as what you can see — *"across the year I can see four of five closing after an early call"* — and never as a law of their business. Where you're unsure, say which part: *"that looks quarterly, though I can only see it twice."*

The difference matters most when the pattern is wrong. A finding stated as an observation invites a correction; the same finding stated as a fact invites them to doubt the whole file.

**Never grade, never score, never congratulate.** No "strong quarter," no "impressive close rate," no percentages against a target nobody set.

**Where the evidence is thin, say so on the line.** *"Possibly a quarterly rhythm — I can see it twice, which isn't enough to be sure."*

---

## Write it into Business Context.md

Add these sections. Everything else in the file stays as it is; **fold new findings into the existing sections rather than replacing them**, and move anything the deep read contradicts into **Corrections** with the date.

This is the moment `Business Context.md` stops being a setup artifact and becomes the state file the whole system runs on. **Write it as if the next session has never met this person and has only this file** — because that is exactly true of every scheduled run.

```markdown
## How You Work
[Their role as the mail describes it, one paragraph, with what it's based on.]

**What people come to you for:** [the two or three real ones, with rough proportions]
**Rhythms:** [standing meetings, heavy days, monthly and annual spikes]
**Where the week starts and ends:** [what the traffic shows]

## People
Everyone who recurs. Verified only. Three tiers, by last contact and whether anything is live.

### Active
Contact in the last 60 days, **or** anything live at any age — an open commitment, money outstanding, a Fixed Point with their name on it. Recency alone doesn't decide this: a client quiet for seventy days with an unpaid invoice is Active; someone who emailed once last week is not.

| Who | Where | What they are | How often | Last contact | What they usually want |
|---|---|---|---|---|---|
| [name] | [org] | [client / referrer / supplier / staff / advisor] | [~weekly] | [date] | [scope questions, approvals, invoices] |

### Background
Two months to a year, nothing live. One line each: name, what they are, when they last came up.

### Dormant
Over a year, nothing live. Name, what they were, when they went quiet. One line, and that's all they cost.

**Re-tier on every deep read and whenever a correction touches someone.** It's automatic and nothing is ever deleted — a dormant name that reappears in the mail is Active again on the next run, with its history intact. That history is often what makes a brief smart: *"Priya, who referred you two clients in 2025 and has been quiet since March."*

**If Active runs past about 25**, the tiering is wrong rather than the person being unusually busy — 25 is roughly the number of relationships anyone is actively carrying. Look again for rows that are recent but not live, and move them down.

Mark anyone whose relationship you inferred rather than saw stated, so a correction knows what to aim at.

## What They Care About
Where the attention actually goes — derived from volume and from what gets fast replies, not from what anyone said in setup.
- [thing] — [n threads, n meetings, over what period] *[evidence]*

## What Lands
Patterns that preceded work that reached a good end. Three or more cases each, or it doesn't go here.
- [pattern] — [the cases, with dates]

## What Falls Through
- [pattern] — [how many, over what period] *[evidence]*

## The Deep Read
*Ran [date]. Covered [n] threads over [window], [n] calendar events over [window]. Calendar was [enumerated / sampled].*
[One paragraph: what this pass could and couldn't establish, and what would make the next one better.]
```

Then fold findings into the sections that already exist — **Vocabulary** from how they actually write, **Rhythm** from the calendar, **Fixed Points** from anything annual, **Blind Spots** from what you couldn't see, **What Money Looks Like** from what the mail shows about how it moves.

**Anything the deep read contradicts moves to Corrections with the date** rather than being quietly overwritten. The file should show its own history of being wrong; that's what makes it trustworthy.

**Two things make this file load-bearing rather than decorative**, and both are easy to skip:

- **Every claim carries where it came from.** A name with no source can't be corrected, because nobody knows what to correct.
- **Separate what you saw from what you concluded.** "Marguerite writes weekly" is observed. "Marguerite is the main client" is a conclusion. The first is nearly always right; the second is what they'll want to fix.

---

## Then name what would sharpen it

This is the one place a connector nudge belongs, because it's the only moment where the gap can be named with a year of evidence behind it.

**Write into Blind Spots, and give the following brief one line.** Concrete, evidenced, no pitch:

> "Eleven of the threads I read this year are about invoices and payment. I can see the conversations and not the amounts, so anything I say about money is what people wrote, not what's actually outstanding. If your books are connected, I'll pick that up from the next run."

Then say the thing they don't know, once:

> "Anything you connect gets checked from then on — no need to set anything up again. Just say 'connect my books' and every future brief includes it."

That is a real mechanic, not a promise: scheduled runs read the connected list from **What's Connected** rather than a fixed list baked into the task, so a connector added in month three reaches tomorrow's brief on its own. See `${CLAUDE_PLUGIN_ROOT}/reference/scheduled-runs.md`.

**Name at most two gaps**, the two with the most evidence behind them. A list of everything they could theoretically connect is a feature tour, and it reads as one.

---

## When it's run interactively

Same pass, then show them what you found and ask the one question: **"What did it get wrong?"** Apply it, write the durable parts into **Corrections**, and say which ones you saved.

This is the highest-yield correction moment in the whole system — it's the first time they've seen a year of their own working life described back to them, and they will have opinions.
