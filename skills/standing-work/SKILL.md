---
name: standing-work
description: Set up, review, change and retire everything the chief of staff does without being asked — standing tasks that hold a goal and re-derive from live email and calendar every run, capped at three, and one-time reminders that fire once on a date and retire themselves, which don't count against the cap. Trigger when the user says "keep an eye on", "watch this for me", "chase that until it's done", "work on this without me", "remind me on", "remind me to", "don't let me forget", "nudge me before", "what are you working on", "what's running", "what's scheduled", "stop doing that", "retire that task", "take that off", or asks for something to happen on its own or on a particular day. Only fires when a Chief of Staff workspace exists. Never runs inside a scheduled run.
---

# Standing Work

The brief tells them what needs them. This is the part that works on something between briefs.

Read `${CLAUDE_PLUGIN_ROOT}/reference/voice-and-ground-rules.md` and `${CLAUDE_PLUGIN_ROOT}/reference/scheduled-runs.md` before creating or changing anything.

**This skill only ever runs with a person in the session.** Standing tasks are created by someone who said yes. See the rule in `scheduled-runs.md`: a scheduled task never creates a scheduled task, and that rule is the reason this system can be audited at all.

---

## What a standing task is

One goal, held by one scheduled task, that wakes up on a schedule and asks the same question every time: **what would move this forward, and has anything changed since I last looked?**

Three properties make it different from a reminder.

**It re-derives.** Every run starts from live email and calendar, not from what it concluded last time. Its own last conclusion is the thing most likely to be stale — the statements it's waiting on may have arrived on Tuesday, and a task that trusts its own memory will chase them on Wednesday. Read the state file for *what it did*; read the inbox for *what is true*.

**It proposes by default.** Acting is opt-in, per task, granted out loud. A task with no explicit grant writes what it would do and the next brief carries it.

**It writes state every run**, including the runs where nothing happened. A quiet run that writes nothing is indistinguishable from a broken one.

---

## A reminder is not standing work, and it doesn't cost a slot

**Most of what people want is a reminder, and offering them a standing task instead is how three slots get spent on things that needed one date each.**

A one-time reminder fires once, sends one short email, deletes its own task and is gone. No re-derivation, no goal held over time, no end condition to reason about — the fire date *is* the end condition. It cannot drift, because there is no second run to drift in, which is why the cap that governs standing tasks has nothing to do with it. See the four kinds in `scheduled-runs.md`.

**The test is one question: is there anything to work out between now and then?**

| | |
|---|---|
| *"Remind me to send Priya the scope on the 12th"* | reminder — nothing to work out, just a date |
| *"Tell me the day the Hollis statements land"* | standing task — it has to check the inbox every morning to know |
| *"Don't let me forget the board thing on the 9th"* | reminder |
| *"Chase Tobias until he replies"* | standing task |

**Make reminders freely, including at three.** Someone at the cap asking to be reminded of something on the 12th gets the reminder. Quoting a limit at a request for a one-off nudge is a rule applied without understanding what it's for.

### Creating one

Two things, and neither is a question if they've already said them: **the date**, and **what it should say**. Take the wording from the commitment itself rather than asking — *"the scope to Priya, per what you told her on the 4th."*

Then write it, per `scheduled-runs.md`: the emitted prompt names the workspace, the recipient in full, what to say, the date, and that it must delete its own task after sending. One short email, in the brief's visual language, no derivation, no sections.

Confirm in one line with the date and the wording, and say what it'll look like: *"That'll arrive on the morning of the 12th as its own short email, then delete itself."*

### Recording one

In `Standing Work.md` under **Reminders** — not among the three:

```markdown
## Reminders
*These fire once and retire themselves. They don't count against the three.*

| Fires | What it says | Why | Set |
|---|---|---|---|
| 2026-09-12 | The scope to Priya | promised her the 14th, in your mail of the 4th | 2026-09-05 |

### Fired
- **2026-09-12** — the scope to Priya — sent, task deleted
```

**Every run reads this table before proposing anything**, so the same reminder never gets offered twice, and a date already covered never turns up in the brief as though nothing were watching it.

**Ten live reminders is the smell test.** Past ten it has become a to-do list nobody agreed to keep. Say so once and offer to fold the recurring ones into a standing task.

---

## Choosing what goes into the three

Read the schedule-versus-brief judgment in `scheduled-runs.md` and apply it. The short version: **date-bound with something to work out** is standing work; **a date with nothing to work out** is a reminder; **needing their judgment, their voice, their relationship or their money** is a line in the brief; **unsure** is a line in the brief.

Two more filters before you offer to create one.

**Is there a real end?** A standing task with no finish condition runs forever and nobody remembers approving it. "Until the statements arrive." "Until the filing goes in." "Until they reply or the 30th, whichever first." If they can't name the end, it isn't standing work yet.

**Would they notice if it silently stopped?** If not, it wasn't worth a slot. Say so and put it in the brief instead.

---

## The cap is three, and it binds

Three, per `scheduled-runs.md`, not counting the surfaces or any reminders. **The weekly primer is a surface, not one of the three** — it holds no goal, watches nothing and acts on nothing, so there is nothing running unattended for anyone to lose track of. The reasoning is in `scheduled-runs.md` under *The weekly primer*.

At three, stop and say it plainly:

> "That's the third, which is where I hold the line. Anything else goes in the brief until one of these retires — or we retire one now if this is better than what's running."

Then show the three and let them choose. Never quietly make it four.

---

## Creating one

Four things get settled, and three of them are clicks.

1. **The goal, in their words.** Typed. A goal offered as options is your goal wearing theirs — this is the one thing here you cannot infer.
2. **When it wakes up.** Offer two or three concrete cadences drawn from the goal itself, not a generic list. For a filing blocked on a client: *"Every weekday until the 15th" / "Mondays and Thursdays" / "Once, on the 12th."*
3. **Propose or act.** Two options, and the difference stated in one line each:
   > - **Propose** — it works out the next move and puts it in your brief. Nothing happens without you.
   > - **Act** — it does the thing and tells you afterwards. Only for [the specific action], nothing else.
4. **The end condition.** Offered from the goal: *"When the statements arrive" / "After the 15th" / "When you say stop."*

Then write the emitted prompt per `scheduled-runs.md` — naming the workspace, naming `Standing Work.md` by path, stating that the state file wins, giving per-source failure behavior, and forbidding clarifying questions — and create the task.

**Acting is never granted in general.** A grant covers one named action on one named goal. "You can chase Tobias for the statements" is a grant. "You can handle the Tobias matter" is not, and if that's what they say, narrow it back and confirm the narrow version.

**Never grant acting on anything that leaves.** Ground rule 3 stands: no sending as them, no replying, no calendar changes, no client systems. An acting task's range is what it writes into the workspace and what it puts in front of them. If a goal only makes sense with outbound action, say so plainly — *"the doing part of this is yours; what I can do is have it in front of you on the right morning with everything you need"* — and make it a proposing task.

---

## The state file

`Standing Work.md` in the workspace root. One section per task, newest run first inside each.

```markdown
# Standing Work

*Up to three. Say "what's running" to see them, "stop [name]" to retire one.*

## [Short name]
**Goal:** [their words, verbatim]
**Wakes:** [cadence] · **Mode:** proposes | acts on [the one named action]
**Ends:** [condition] · **Started:** [date]

| Run | What was true | What it did |
|---|---|---|
| [date] | [what the live sources showed] | [proposed X / did Y / nothing had changed] |

---

## Retired
- **[name]** — [goal] — ran [start] to [end], ended because [reason]
```

**Retired tasks stay in the file.** One line each. It's the only record of what the system used to be doing on their behalf, and deleting it makes the history unauditable.

---

## What a run does

The scheduled prompt points back here. In order:

1. **Read `Standing Work.md`** for this task's goal, mode, end condition and what previous runs did.
2. **Check the end condition first.** If it's met, write the final row, move the task to **Retired**, note it for the next brief, and stop. A task that outlives its goal is the thing that makes people distrust everything running unattended.
3. **Re-derive from live sources.** Run `deriving-the-picture.md` narrowed to this goal — what does mail, calendar and the workspace say is true about it *today*? Sent mail settles anything the state file claims about what was done.
4. **Decide what would move it forward.** One thing, not a list.
5. **Propose it, or do it.** Proposing means writing it into the state file for the next brief to carry. Acting means doing the one named action and recording it. Either way it's one row.
6. **Write the row, always.** Including *"nothing had changed."*

**If a run concludes something new should be standing**, that is a proposal, not an action. It goes in the state file and the next brief carries it. The person creates it, or doesn't.

**Never ask a question in a scheduled run.** Nobody is there. Take the reading the state file supports, do the work, and note the ambiguity in the row.

---

## Reviewing, changing and retiring

**"What's running"** — show all three in about six lines. Name, goal, when it wakes, propose-or-act, and the last thing it did. Not the whole table. **Then the surfaces and any live reminders**, in one line each: *"Plus your brief every weekday at 6:40, the review on Sunday at 5, the primer on Friday mornings, and one reminder — the scope to Priya, on the 12th."* They asked what's running; the answer is everything that is, including the things that don't cost a slot.

**Changing one** — a cadence or an end condition changes in place, and the emitted prompt is rewritten with it. A goal that has genuinely changed is a new task: retire the old one and create the replacement, so the history stays honest about what was running when.

**Retiring** — takes one sentence from them and needs no confirmation beyond that. Move it to **Retired** with the reason, delete the scheduled task, and say which slot is free. Never argue for keeping it.

**Offer to retire without being asked** when a task has run five or more times with nothing changing, or its end condition has drifted past. One line, observational, no pitch:

> "The Hollis chase has run nine times since the 2nd and the statements haven't moved. Worth retiring, or changing what it's watching for?"
