# Scheduled Runs

Everything in this plugin that happens without being asked happens through a scheduled task. Read this before creating one, changing one, or writing the prompt that fires inside one.

---

## The one fact that governs all of this

**Every firing is a fresh session that remembers nothing.** Not yesterday's conversation, not the workspace, not who they are, not what the brief is for. It has the prompt you wrote and whatever it can find on disk. That's all.

So "run the morning brief" is not a scheduled task. It's a note to someone who isn't there.

The failure this produces is the worst kind in the whole system, because it is **silent and it is daily**: a generic, context-free brief arrives every morning, on time, looking correct, with no error anywhere. Nobody notices for three weeks and by then the habit is dead.

---

## The four kinds, and only one of them is capped

Everything that runs unattended is one of these. Knowing which one you're creating decides where it's written, whether it counts against the cap, and how hard you should think before offering it.

| | What it is | Cap | Ends |
|---|---|---|---|
| **The surfaces** | the daily brief and the Sunday review, always; the weekly primer, if they took it | none of them count | never — they're the system |
| **Standing tasks** | a goal held between briefs, re-derived every run | **three**, hard | at a stated end condition |
| **One-time reminders** | one date, one thing, fires once and retires itself | ten live | on its own, the moment it fires |
| **Playbook runs** | a taught job on a cadence they asked for | counts as a standing task | when they retire it |

**The first two surfaces get created at setup, together, and neither is optional.** The daily brief is today's slice; the Sunday review is the whole picture. A system that only ever sends the daily slice lets the medium-term rot quietly — the thing that's been stuck for five weeks never quite qualifies as today's news, so it is never reported at all.

**The third is offered, not assumed.** The brief and the review are the system; the weekly primer is a habit someone opts into. Setup offers it once and takes the answer — a decline is permanent, per ground rule 10, and the skill stays available on request forever.

**One-time reminders are cheap and should be treated as cheap.** They cost one line in a file, they delete themselves, and they cannot drift, because there is no second run to drift in. The three-task cap exists so nobody loses track of what is running on their behalf indefinitely; a reminder that fires once on the 12th and disappears is not that. Never make someone spend a standing slot on a date.

Ten live reminders is the ceiling, and it's a smell test rather than a rule to enforce loudly: past ten, the reminders have become a to-do list nobody agreed to keep, and the honest move is to say so and offer to fold the recurring ones into a standing task.

---

## What the emitted prompt must name

All of these, every time, with no exceptions and nothing left implicit.

| It must name | Because without it |
|---|---|
| **The workspace, explicitly** — the Project by name, or the absolute folder path | The fresh session writes into a temporary location that is discarded when the run ends |
| **The reply gate, by name** — one sent-mail pull up front, indexed by recipient, then full thread enumeration before claiming anyone hasn't replied | It tells them to chase someone they answered last night. **This is the most common failure this system produces.** |
| **The state file, by path** | It re-derives from nothing and repeats work it already did, or contradicts what it decided last time |
| **That the state file wins where the two disagree** | A prompt written in September is still asserting September's facts in March |
| **The recipient address, in full** | It guesses, or sends nothing, or asks — and nobody is there to answer |
| **What to do when a source is unavailable, per source** | It stops on the first connector that doesn't answer, and the run produces nothing at all |
| **That it must not ask clarifying questions** | It asks, waits, and the run times out having done nothing |
| **The person's timezone, by name** | The run works in UTC and writes a brief about the wrong day — see ground rule 7b |
| **Which file this run's output feeds** | The dashboard renders from a file that nothing updated |
| **That the connected sources come from the registry, not from this prompt** | A connector added in month three never reaches the brief |

**Never enumerate the connected sources in the prompt.** Name where the list lives and let the run read it. A prompt that says "check Gmail and Google Calendar" is a prompt that will still be checking only those two a year later, after they've connected their books, their CRM and their project tool and wondered why none of it ever shows up. The registry is the contract; the prompt is a pointer to it.

This is also what lets you say something true when someone asks whether adding a connector means redoing anything: *"No — anything you connect gets picked up by tomorrow's run on its own."*

**The state file wins.** Say it in those words. The prompt is written once and then it is frozen; the state file is rewritten every run. Anywhere they disagree — the recipient, the goal, what was already done, what the person corrected — the file is current and the prompt is a fossil.

---

## The shape of it

Write it as a complete instruction to a capable colleague who has never met this person. Not as a reminder to yourself.

> Run the morning brief for Dana Whitfield.
>
> **Workspace:** the Claude Project named `Chief of Staff`. Everything you need is there — read `Business Context.md` first, then `CLAUDE.md`, then the most recent file in `01 Briefs/`. Use the `morning-brief` skill from the `aidgentic-chief-of-staff` plugin and follow it exactly.
>
> **State file:** `Business Context.md` in that Project. **Where this prompt and that file disagree, the file is right and this prompt is out of date** — including about the recipient address and about what the business is.
>
> **Send to:** dana@whitfieldstudio.example, and nowhere else. One recipient, no CC, no BCC.
>
> **What to read:** the connected sources are listed in `Business Context.md` under **What's Connected**. **Check every source listed there, whatever it is.** That list is authoritative and it may have grown since this task was written — do not limit yourself to mail and calendar because this prompt happens to mention them.
>
> **If a source is unavailable:** calendar missing — say so in the closing line and carry on from mail. Mail missing — say so in the *first* line, not the last, and send what the calendar gives you. Workspace unreachable — send the brief anyway from live connectors, and open with the fact that it's running blind and what to do about it. Never skip a run because something is missing.
>
> **Start with one pull of sent mail** — everything Dana sent across the window, in a single query, keyed by recipient address and domain, before any thread is opened. Every candidate that only qualifies because nobody answered is checked against it first; a sent message to that address or domain after the message in question means she answered, and the item drops.
>
> **Before saying anyone hasn't replied:** run the reply gate in `deriving-the-picture.md` Step 2b in full. What the index doesn't settle gets a full thread fetch — not a search result — every message sorted by timestamp, read past the inbound message to the end, and **name who sent the last one and when on the evidence line.** A thread view has been observed returning a thread without Dana's own reply inside it, and a thread has been called unanswered for four days while four of her replies sat in it from the same afternoon. If the searches are inconclusive, or sent mail returns nothing at all across the run, soften every silence claim to what you can see — *"the last message I can see in this thread is theirs, on the 11th"* — and say so in the closing line. Never assert silence you didn't search for.
>
> **Timezone:** Dana is in `America/New_York`. You are firing in UTC. Convert once, at the top, before you decide what "today" and "tomorrow" mean, and say which zone you worked in. **Check the converted result against the clock rather than trusting the arithmetic** — a firing at 05:00 UTC is the previous evening on the US west coast, and every message timestamp you read may come back in a different zone again. If you can't establish the zone, say which one you assumed.
>
> **This run feeds:** `Standing Map.md` in that Project. Write it every run. Do not attempt to create or update an artifact — see below.
>
> **Do not ask any questions.** Nobody is reading this session. If something is ambiguous, take the reading the state file supports, do the work, and note the ambiguity in the closing line.

Every clause there is load-bearing. When you write one of these, read it back and ask: *if I knew nothing except this, could I do the job?*

---

## The first run does the deep read

The first scheduled run has a job before the brief: run the **deep-read** skill, once, over months of history rather than days. Setup is fifteen minutes, so the context file it produces is thin, and this is where it gets thick — unattended, with nobody waiting, so it can take as long as it needs.

Say so in the task prompt, and write it so it is self-limiting:

> **Before the brief, check `Business Context.md` for a `## How You Work` section.** If it isn't there, run the `deep-read` skill first and write its findings into that file — this is the one-time pass over the last several months. If the section is already there, skip it and go straight to the brief.

That check is the whole mechanism: it makes the pass run exactly once, and it makes a run that dies halfway harmless, because the next one finds no section and does it properly.

**The brief that follows it opens differently**, and this is the one time a brief may talk about itself:

> "Before this one I went back through the last six months. A few things I picked up, and then today."

---

## The Sunday review

The second surface, created at setup alongside the brief, and never counted against the cap.

**What it is:** the **dashboard** skill at whole-picture scope, run unattended once a week. It rewrites `Standing Map.md` and emails the whole picture as HTML — the same derivation the brief runs at today's slice, at the zoom level that catches what a daily slice structurally cannot.

**Why it has to exist.** The daily brief asks *what needs you today*. A thing that has been stuck for five weeks never needs anyone today, so it never qualifies, so it is never reported — and then it surfaces as a surprise in month three. The weekly is where commitments overdue by a fortnight, threads quiet for a month, and everything in *Circling* actually get said.

**Sunday, late afternoon or early evening**, in their timezone. Offer 4pm / 5pm / 6pm at setup. The point is to land before the week starts, while there's still time to do something about what it says — Monday morning is too late to change Monday.

**What it does, in order:**

1. Run `deriving-the-picture.md` at whole-picture scope, including Step 8, the repeat check.
2. Write `Standing Map.md`, overwriting.
3. Compose and send the weekly review email per the **dashboard** skill's mail skeleton.
4. Write a state line, even when the week was quiet.
5. **Never** attempt the artifact, and never create a task.

**It carries the week's proposals.** Anything a standing task proposed since the last review, anything the brief offered and never got an answer to, and any dated thing coming up inside its lead time that has no reminder on it. One list, at the end, and each line is declinable in a word next time they're in a session. This is the one place where a small pile of proposals is correct rather than a violation of ground rule 10 — a weekly review is exactly where someone expects to be asked what's worth setting up.

**The emitted prompt is a separate one**, written to the same standard as the brief's — the workspace by name, `Standing Map.md` by path, the state file wins, the recipient in full, per-source failure behavior, the reply gate, the timezone by name, no clarifying questions. **The reply gate matters more here, not less:** a week's worth of *gone quiet* lines is a week's worth of chances to tell them to chase someone who answered, and this surface is built to report exactly the old, silent-looking threads where a mid-thread reply is easiest to miss. Add one clause the brief's doesn't have:

> **This run rebuilds the whole picture, not today's slice.** Use the `dashboard` skill at whole-picture scope, write `Standing Map.md`, and send the weekly review email described in that skill. Do not attempt to create or update an artifact. Do not create, change or delete any scheduled task.

**Monday's brief says the map was rebuilt**, in the closing line, one clause. Otherwise the person has no way to know the weekly ran, and a surface nobody can tell is working is a surface nobody trusts.

---

## The weekly primer

The third surface, and the only one that reads anything outside their own workspace. Offered at setup rather than created with the other two.

**What it is:** the **weekly-primer** skill, run unattended once a week. It researches one topic fresh that week from dated sources, at the point where their industry, the specific work they do and what's happening in AI overlap, and emails it. That skill carries the whole job; this section carries only what's true of it as a scheduled thing.

### Why it isn't one of the three

**Because the cap is not a budget for scheduled tasks — it's a bound on things doing work on their behalf that they can't see.** A standing task re-derives against live signals, can be granted the ability to act, holds a goal, and has an end condition somebody has to remember. Four of those running at once is the point where nobody can say what the system is doing for them.

The primer holds no goal, watches nothing, acts on nothing, ends never, and its entire output is a visible email in their inbox every week. There is nothing hidden to lose track of. **Charging a slot for it would mean trading a thing that watches the Hollis statements for a reading habit** — the same mistake this file already names in *never charge a slot for a date*.

Auditability is kept the way it's kept for the other two surfaces, not by the cap: it's named in `CLAUDE.md` under **What arrives on its own**, it's listed by *"what's running"*, and it retires on one sentence.

### When it lands

**Friday morning by default**, with Wednesday morning, Tuesday afternoon, or a day and time of their own as the alternatives. Friday because the week's work is done and nothing is being started — the brief is for acting, the review is for planning, and this one is for reading, so it wants the moment when nothing is being decided.

**On any day the brief also fires, the primer lands at least two hours after it.** 10am against a 7am brief. The brief has to win the morning it arrives in, and two emails from the same system in the same hour means one of them gets skimmed — reliably the longer one.

### What its prompt names beyond the standard nine

Everything in *What the emitted prompt must name* applies unchanged. Four clauses on top:

> **This run is the weekly primer.** Use the `weekly-primer` skill from the `aidgentic-chief-of-staff` plugin and follow it exactly. One topic, researched this week from sources you actually fetch.
>
> **Ledger:** `Learning Log.md` in that Project. Read it before choosing a topic and write to it after — including on a run that sends nothing. Never repeat a topic it already lists.
>
> **Before anything else, check `Business Context.md` for a `## How You Work` section.** If it isn't there, the deep read hasn't run yet and the context is too thin to anchor a primer. Write the ledger row and stop — do not send.
>
> **If nothing datable was fetched, send nothing.** A primer built from what you already know rather than from sources fetched this week is the one outcome that is never acceptable. Write the ledger row saying why, and stop.
>
> **Do not create, change or delete any scheduled task. Do not attempt to create or update an artifact. Do not propose anything** — if this run concludes something is worth setting up, it goes in the ledger under **Proposed** and the Sunday review carries it.

**The next brief carries one clause** when a primer was due and didn't run, naming the reason. Same mechanism as Monday's *"the full picture was rebuilt last night"*, and for the same reason: a surface that fails silently is one nobody can trust.

---

## A scheduled run never touches an artifact — but it does send email

These are two different mechanisms and confusing them costs a whole feature, so be precise about which is blocked.

**The artifact is blocked.** Not "shouldn't" — cannot. Three independent reasons, each sufficient on its own:

1. **Artifacts live on the person's desktop**, reached through a device bridge. The tool reports back "created on the connected desktop." A scheduled run has no device bound to it, so there is no desktop to reach.
2. **Creating one requires handing a file into a conversation** to get an id back. A scheduled run has no conversation.
3. **No URL comes back**, so even a successful write could not be linked from the brief or opened on a phone.

This was tested. The failure is silent — no error surfaces anywhere, the run simply produces nothing and reports nothing — which makes it exactly the kind of thing that gets tried again in six months by someone who assumes the last person didn't try hard enough. **So: don't.**

**HTML email is not blocked, and it is the answer.** A scheduled run composes HTML and sends it to one address every weekday morning already — that is the entire daily brief. Nothing about the desktop bridge touches it. So anything visual the person needs from an unattended run gets delivered as mail, and the only thing lost by having no desktop is a page they can pin, not the picture itself.

**What a scheduled run owes, in order:**

1. **Write the data file.** `Standing Map.md` lives in the Project and reads on a laptop, a browser and a phone with nothing switched on. If everything else fails, the picture survives here.
2. **Send the mail.** The daily brief, or on Sunday the full review, rendered properly.
3. **Never attempt the artifact.** Don't try it, don't fall back to it, don't mention it. A session with a person in it will render the page next time they're at a machine.

**Email HTML is not the dashboard template.** `Dashboard Template.html` is a web page — `<style>` blocks, a script, grid layout, ask chips. Mail clients strip every one of those. The weekly review has its own table-based, inline-styled skeleton in the **dashboard** skill, in the same visual language as the brief. Never try to mail the template.

The brief still **links to nothing artifact-shaped**, because there is no address to link to. It can name the file.

---

## Before you create it — can it reach the workspace?

A scheduled run fires in the cloud. **A folder on their computer is not reachable from there.**

| Workspace | What to do |
|---|---|
| A Project | Create both surfaces — the daily brief and the Sunday review — and offer the primer. Name the Project in each prompt. |
| A folder on their computer | Say the consequence before creating anything: the run will fire, find nothing, and send a blind brief every morning. Offer the Project, or offer the manual version — *"say 'good morning' whenever you want it, and 'where do things stand' on a Sunday, and you'll get the same two things."* The primer is the same: something they ask for rather than something that arrives. |
| Neither | Nothing gets scheduled. Resolve the workspace first, per ground rule 7a. |

**Never schedule something you already know will wake up blind.** A task that fires correctly into an empty room is worse than no task, because it looks like it's working.

---

## Test the send path once, now

Before the close of setup, send one short real message to the confirmed address and watch what happens. This costs twenty seconds and it settles a question that otherwise gets answered on day two, badly.

| What happens | What to say |
|---|---|
| It sends | *"That's the pipe working — tomorrow it's the real thing."* |
| It can only draft | *"Your mail connection lets me write but not send, so the brief lands in your Drafts each morning rather than your inbox. Same brief, one extra tap."* Then say it again in the close, so it isn't a surprise. |
| It fails entirely | Say so plainly, say the brief will be saved to `01 Briefs/` instead, and note it in `Business Context.md` under **Blind Spots**. |

A promise of inbox delivery that quietly turns out to be a draft folder costs more trust than a draft folder stated plainly on day one.

---

## Noticing what should run on its own

Most of what belongs on a schedule never gets there, and the reason is not that the person declined — it's that nobody offered. They don't know a one-time reminder is available, they won't think to ask, and the thing they'd have wanted it for was mentioned once in a sentence in March.

**So this is an active job, not a request queue.** Every brief, every dashboard build, every session where a date gets said out loud, one question runs underneath: *is there something here whose whole value is in it happening on a particular day?*

### What to look for

These are the signals. When one fires and nothing is already watching it, there's a candidate.

| What you see | What it wants |
|---|---|
| A commitment they made with a date on it — *"I'll have it to you by the 14th"* | a reminder, a day or two before |
| A dated thing inside its lead time with a dependency — a filing that needs statements first | a standing task until the dependency lands |
| Something waiting on someone else with a natural check-back — a proposal sent Tuesday | a reminder on the day a chase becomes reasonable |
| A renewal, a lease, an insurance date, a notice period | a reminder inside the window where they can still act |
| A date said in passing in the session — *"the board thing is the 9th"* | a reminder, and ask nothing else |
| Something they've now done by hand three months running | a playbook, then a run on a cadence |
| A person who reliably goes quiet and reliably matters | a standing task, if they can name the end |

### Which of the four it becomes

**A date and nothing else → a one-time reminder.** No decision required, no re-derivation, no cap. This is the default, and the one most often skipped in favour of something heavier. If the whole job is *say this to them on the 12th*, that's a reminder — make it and move on.

**A date plus something to watch → a standing task**, if and only if they can name an end. "Every morning until the statements arrive." Re-deriving is what earns the slot; if nothing needs re-deriving, it was a reminder.

**Their judgment, their voice, their relationship or their money → a line in the brief.** Anything they'd want to word themselves. Anything where the right answer depends on something only they know. Anything involving a person where a mistimed or generic touch costs more than the reminder saves.

**Unsure → the brief.** The cost of a brief line that turns out to be unnecessary is one line they skim past. The cost of a standing task that turns out to be wrong is a thing running unattended every week doing something they didn't want, discovered late, making them distrust everything else that runs on its own. That asymmetry does not apply to one-time reminders, which is exactly why they're the cheap default: the worst case is one email on one morning about a thing that turned out not to matter.

### How to offer it

**One at a time, attached to the thing that prompted it, declinable in a word** — ground rule 10, unchanged. Name the date and the trigger, not the feature:

> "You told Priya the scope would be with her by the 14th. Want a nudge on the 12th?"

> "The Hollis lease notice period closes on the 30th and nothing's watching it. Reminder on the 23rd?"

Never *"would you like to set up a reminder?"* — that's a feature offer, and it puts the work of deciding what for back on them.

**When they say a date at you, that's not a proposal — that's an instruction.** *"Remind me Tuesday."* *"Don't let me forget the 9th."* Make it, confirm it in one line with the date and what it'll say, and don't spend the session's one proposal on something they asked for outright.

**Say what will actually happen when it fires**, because a reminder nobody can picture is a reminder they can't judge: *"That'll arrive as its own short email on the morning of the 12th, then delete itself."*

**Record it** in `Standing Work.md` under **Reminders**, with the date and the source of the commitment, so the next run knows it exists and doesn't offer the same thing twice.

**Retire on fire.** A one-time reminder deletes its own scheduled task after it sends and moves its line to **Fired**. A reminder that fires twice for the same date is the fastest way to make the whole system feel unmaintained.

---

## Changing a task that's already running

A correction that should have changed a scheduled task and only changed a file has not been applied. The person cannot see the task; the file is the only thing they can check, and it will look right while the wrong thing keeps happening every morning.

| They said | What actually has to change |
|---|---|
| "Send it at 6, not 7" | the schedule **and** the time named in the prompt |
| "Send it to my other address" | the recipient in **every** task's prompt — brief, weekly, primer, and every live reminder — **and** in `CLAUDE.md` |
| "Stop chasing Tobias" | retire the task, update `Standing Work.md`, say which slot is free |
| "I've moved to Denver" | the timezone in every task's prompt — all of them, not just the brief |
| "It keeps flagging X" | the state file, since ranking reads that, not the prompt |
| "I connected my books" | nothing in any prompt — the registry handles it. Say so, so they don't expect a rebuild |
| "Move the weekly to Friday" | the Sunday review's schedule **and** the day named in its prompt; say what they lose — Friday reports the week that just ended, Sunday sets up the one starting |
| "Actually make that the 14th" | the reminder's fire date **and** its line in `Standing Work.md` |
| "I don't need that reminder" | delete the task, move the line to **Fired** with the reason. No confirmation needed beyond them saying it |
| "Move the primer to Wednesday" | the primer task's schedule **and** the day named in its prompt. Keep it clear of the brief by two hours |
| "Stop the primer" | delete the task, record it in `Learning Log.md` under **What they've said**. Say which surfaces are still running |
| "Cover more security" / "not that topic" | `Learning Log.md`, not any prompt. The rotation reads the ledger, and the prompt is a pointer to it |

Judge which of these a correction actually touches rather than walking the list every time — most corrections touch one row, and the move to another city touches all of them.

**Rewrite the prompt rather than creating a second task.** Two tasks doing nearly the same thing is how someone ends up with two briefs a morning and no idea which one is current.

**Then say it out loud, naming the schedule**, because this is the one change they have no way to verify: *"Done — the 7am task now fires at 6 and knows you're in Denver. Tomorrow's the first one."*

---

## The cap, and the one thing that is never allowed

**Three standing tasks maximum**, not counting the surfaces or one-time reminders. The daily brief, the Sunday review and the weekly primer aren't among the three — the first two are the surfaces the three report into, and the primer is a read that holds no goal and watches nothing. A reminder isn't either: it fires once and is gone, so it can't be a thing running unattended that nobody remembers approving, which is the only thing the cap exists to prevent.

**Never charge a slot for a date.** If someone is at three and asks to be reminded of something on the 12th, they get the reminder. Saying "you're at your limit" to a request for a one-off nudge is a rule applied without understanding what it's for.

At three, stop and say so: *"That's the third standing task, which is where I hold the line. Anything else goes in the brief until one of these retires."* Offer to retire one if the new thing is better than something already running. Four things running unattended is the point at which nobody can say what the system is doing on their behalf, and a chief of staff nobody can audit is a chief of staff nobody should trust.

**A scheduled task never creates another scheduled task.** Not one, not "just this once," not as a follow-up to something it found. Standing tasks are created in a session with a person in it, by a person who said yes. A task that can schedule tasks is a system that grows in the dark, and there is no version of that anyone asked for.

If a run concludes that something new should be standing, it writes that conclusion into its state file as a proposal and the next brief carries it. The person creates it, or doesn't.

---

## Every run writes state — including the runs where nothing happened

A run that found nothing still writes: the date, that it ran, what it looked at, and that nothing had moved. Skipping the write on a quiet run makes a working system indistinguishable from a broken one — the file's last entry is three weeks old either way, and the person has no way to tell which they're looking at.

Two lines is enough. *"2026-09-14 — ran, no change. Statements not in yet; last chase was the 9th."*
