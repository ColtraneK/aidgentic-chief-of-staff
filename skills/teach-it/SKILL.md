---
name: teach-it
description: Turn something the person does repeatedly into a playbook — do the job with them once, capture how they actually want it done, then write it to their workspace so it runs the same way every time after. Trigger when the user says "learn how I do this", "make this repeatable", "I do this every week", "can you remember how to do this", "turn this into a playbook", "save this process", "do this the same way next time", "run my [playbook]", or describes a recurring task they're tired of explaining. Only fires when a Chief of Staff workspace exists — an attached Project or selected folder containing CLAUDE.md or Business Context.md; if another installed plugin also claims these phrases, that workspace is the tiebreaker.
---

# Teach It

The chief of staff reads. This is how it starts doing.

Take one thing they redo every week, do it with them once, and capture the version they actually wanted — so next time it's one sentence instead of twenty.

Read `${CLAUDE_PLUGIN_ROOT}/reference/voice-and-ground-rules.md` first.

---

## Where playbooks live, and why

A playbook is a **markdown file in `04 Playbooks/` in their own workspace**, indexed in `CLAUDE.md`.

That placement is deliberate. `CLAUDE.md` is read at the start of every session in this folder, so a playbook listed there is found reliably, today, with no installation step and nothing to enable. It's also a plain file they can open, edit, email to their bookkeeper, or delete — which is the promise the whole system makes.

**Running a playbook:** when they ask for one, by name or in their own words, open its file and follow it exactly, Rules section included. Don't reconstruct it from memory of a previous session.

---

## Pick the right thing

The best candidates are **frequent, repetitive, and have a clear right answer they can recognize when they see it**. The weekly client update, meeting prep from a calendar invite, the monthly funder report, turning a call into a follow-up, chasing unpaid invoices, the same intake reply for the fortieth time.

Bad candidates: one-offs, anything needing judgment they can't articulate, and anything where they don't know what good looks like. If they can't tell you what a good output is, you can't write a playbook for it — do the job with them a few times first.

Ask three questions, no more:

1. **What's the thing, and how often?**
2. **Do you have a good example of the finished version?** Their own past work beats any description. Ask them to paste one or point at a file.
3. **How do you do it now?** Their rough process, in their words. Don't tidy it up — the messy version carries the real constraints.

---

## Do it once, live

Produce the output. Hand it over. Ask what's wrong with it.

Iterate. Two or three passes is normal, and **each pass is the raw material** — their corrections are the instructions. Watch for:

- Things they always want that you didn't do
- Things you did that they always cut
- Format, length and ordering preferences
- The words they change every single time

**Don't write the playbook until they say the output is right.** One built on a mediocre example produces mediocre output forever.

---

## Write it

`04 Playbooks/[Name].md` — a plain title they'd recognize, not a technical one. "Weekly Client Update," not `weekly-client-update-v2`.

```markdown
# [Name]

**Run this when I say:** [their trigger phrases, in their words]
**How often:** [weekly / monthly / whenever X happens]

## What good looks like
[One or two sentences.]

## What it needs
[Inputs — a file, a name, a date range, a calendar event. Say where each comes from.]

## Steps
[In order. Written for a capable colleague, not as a script.]

## Rules
[The corrections they gave, stated exactly as specifically as they said them.]
- [Always / Never …]

## Example
[Their approved output from the session.]
```

**The Rules section is the playbook.** Everything else is scaffolding. "Always lead with the number." "Never use the word 'excited'." "Under 150 words." "The ask goes in the last line, never the first." Vague rules produce vague output.

Then **add it to the Playbooks table in `CLAUDE.md`** — name, trigger phrases, file path. This is the step that makes it findable next session, so don't skip it. Confirm the edit to `CLAUDE.md` with them first, per the ground rules.

---

## Hand it over

Show them the file. Tell them what to say to run it. Then the thing most people don't realize:

> "Change it whenever you want. It's a text file — if it gets something wrong, tell me and I'll edit it, or open it and edit it yourself."

**If they want it everywhere, not just this folder** — a job they do across several projects — offer to save it as an installed skill as well, so it travels with them. Keep the workspace copy either way; that's the one they can read and edit.

---

## Doing this with someone watching

If you're building a playbook alongside another person — a colleague, a client, a room — keep it tight: one genuinely repetitive job, one pass, one playbook. Don't try to perfect it in front of them.

The point they need to see is a capability being created out of a conversation, and then existing as a file with their own words in it. Polish comes later.
