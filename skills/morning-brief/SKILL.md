---
name: morning-brief
description: Produce the daily brief — what needs the person today, what's on the calendar, what moved since yesterday — and email it to them as a clean HTML message, saving a copy to their workspace. Trigger when the user says "good morning", "morning brief", "what needs me today", "brief me", "run my brief", "catch me up", or when a scheduled task fires asking for the daily brief. Only fires when a Chief of Staff workspace exists — an attached Project or selected folder containing CLAUDE.md or Business Context.md; if another installed plugin also claims these phrases, that workspace is the tiebreaker. For the full picture rather than today's slice, use the dashboard skill instead.
---

# Morning Brief

Five minutes of reading that means they start the day oriented instead of guessing.

This is **today's slice** of the dashboard, not a second opinion. Shorter, sharper, and it comes to them.

Read `${CLAUDE_PLUGIN_ROOT}/reference/voice-and-ground-rules.md` first, then `${CLAUDE_PLUGIN_ROOT}/reference/deriving-the-picture.md`, which carries the gathering, the triage gate and the ranking — run it at the **today's slice** scope. `inbox-triage.md` and `operating-models.md` are read from there. Then the workspace's `Business Context.md`.

Read the dashboard's saved state if it exists — but verify anything you take from it against live signals before repeating it. A stale conclusion repeated confidently is worse than none.

**If `Business Context.md` doesn't exist**, run anyway on whatever the workspace and the connectors give you, using neutral vocabulary, and say in the closing line that the brief is running without a context file. Never skip a scheduled brief because setup is incomplete.

**Write to their workspace root**, resolved per ground rule 7a.

---

## Interactive vs. scheduled

**Scheduled run (nobody is watching):** gather, render, send. Ask nothing. Offer nothing. If something is missing, note it in the last line and continue. Never send anything to anyone but them.

**A scheduled run that can't find the workspace does not degrade quietly.** Resolve the workspace per ground rule 7a — the scheduled task's own prompt names it, per `${CLAUDE_PLUGIN_ROOT}/reference/scheduled-runs.md`. If the named Project or folder isn't reachable, the fresh session has no context file, no map, and no corrections: send the brief anyway from live connectors, but its **first** line — not the closing one — says so and says the fix: *"I couldn't reach your Chief of Staff workspace this morning, so this brief is running blind — no context, no vocabulary, no history. Open a session in that workspace and say 'good morning' to check the schedule is pointed at the right place."* One blind brief is information; a month of them, footnoted politely at the bottom, is how the system gets abandoned without anyone deciding to abandon it.

**Interactive run:** same brief, plus you can end by asking what it got wrong — and apply the answer.

**Never create or change a scheduled task from inside a scheduled run.** See `scheduled-runs.md`. If a run concludes something should be standing, that's a proposal for the next brief, not an action.

---

## Before the first brief only — the deep read

**Check `Business Context.md` for a `## How You Work` section.** If it isn't there, this is the first run: run the **deep-read** skill first, let it write its findings, then produce the brief from the file it just improved. If the section is there, skip straight past this.

That pass takes as long as it takes. Nobody is awake, and the brief it delays is the first one they'll ever read — better late and knowing them than punctual and generic.

**Open that first brief by saying so**, in one line. It's the only time a brief may talk about itself:

> "Before this one I went back through the last six months. Three things I picked up, then today."

Carry at most **two** of the deep read's findings into that brief, and give one line to whichever blind spot it named with the most evidence behind it. The rest lives in the file.

---

## Gather

**Read `Business Context.md` → What's Connected and check every source listed there.** That table is the registry, not a description — if they connected their books last week, the row is there and this brief includes it, with no task rebuilt and nothing re-scheduled.

Run Step 1 of `deriving-the-picture.md` at the today's-slice window. The order that matters here:

1. **Today's calendar**, plus tomorrow for context — where "today" and "tomorrow" are resolved per ground rule 7b, in *their* timezone, from the actual clock. A run that fires at 05:00 UTC is late evening for someone on the US west coast, and "tomorrow" for them is the day the run is already in. Tomorrow's events don't get listed; they generate prep items. **The calendar may not be enumerable — follow the calendar rule in `deriving-the-picture.md` and don't trust one query.**
2. **Email since the last brief** (24h weekdays, 72h after a weekend): threads where they were asked something and haven't answered. A group ask where anyone could answer is not their bottleneck — drop it.
3. **The sent-mail index — one pull, before any thread is opened.** Everything they sent since the last brief, in a single query, keyed by recipient address and domain, per Step 1 of `deriving-the-picture.md`. It's how you know what's already handled, and it's the first thing every reply-gate candidate is checked against. Anything they answered overnight goes in *Moved*, not *Needs you*. What the index doesn't settle gets a **full thread fetch, every message enumerated** — never a search result, never first-and-last. A brief that tells someone to chase a client they replied to last night is the fastest way to lose them, and a thread-level read is how it happens.
4. **Commitments coming due** — from the dashboard's saved state and from sent-mail promises, anything due today, tomorrow, or already past.
5. **Fixed points** from `Business Context.md` inside their lead time.
6. **`Standing Work.md`** — anything a standing task proposed or did since the last brief. See *Standing work* below.

---

## Verify before you sort

Run Step 2 of `deriving-the-picture.md` — the prior-contact test from `inbox-triage.md`, on every sender, **before** anything is sorted.

This matters more in the brief than anywhere else. The brief is five items long and it's read half-awake — one stranger's sales sequence at the top of it and the person stops trusting the whole thing. Cold email is written specifically to look like the top item of a morning brief.

- **Unverified senders never appear in *Needs you today*.** Not once, not ever, however urgent the wording.
- **Mass-sends drop silently.**
- **A genuine first-time inquiry about their services** gets one line under *First contact*, below everything else, plainly labelled as first contact.
- **Cold outreach gets a count, not a list.**
- Never attach a recommended action to an unverified sender, and never repeat their urgency framing.

If sent mail isn't connected, say so in the closing line — prior contact can't be verified, so unfamiliar senders are being held out.

### Then the reply gate

**Run Step 2b of `deriving-the-picture.md` in full, before sorting.** Every candidate that only qualifies because nobody answered goes through it, in that order: **the sent-mail index first**, in one pass across all of them; then, for whatever the index didn't clear, the thread fetched in full and enumerated message by message; then the targeted searches and the out-of-thread reply shapes.

This is the gate that protects the brief specifically. *Needs you today* is five lines read half-awake, and one of them telling someone to chase a client they answered last night is the failure that ends the habit. It has happened. It is not hypothetical.

**No line asserts silence without its receipt** — and the receipt names who sent the last message in the thread and when. An entirely empty sent-mail index is a broken connector rather than a quiet week. Both per Step 2b.

---

## Sort

Every verified candidate lands in one of three places or is dropped silently.

**Needs you today** — it would cost something to leave until tomorrow. Ranked by Step 7 of `deriving-the-picture.md` at the five-item cap, Band A first. If more than five qualify, the extras weren't urgent; that's what the dashboard is for.

Nothing lands here that hasn't cleared the reply gate. Anything they answered overnight moves to *Moved* or drops entirely — a brief that lists things they've already handled trains people to stop reading it.

**On the calendar** — today's meetings in time order. One line each: who, what it's for, and anything that makes it non-routine.

**Moved** — what closed since yesterday. Someone answered, a thing shipped, a meeting got cancelled, a payment landed. Short. This section is why people keep reading the brief: it's the only place they see progress.

**Worth knowing** — at most one line, and only when there is a genuine insight per ground rule 10: something true, drawn from across weeks or months rather than from last night, that today's inbox alone couldn't have told them. It reads as a fact with its evidence, never as a lesson.

> *Three of the four enquiries you answered the same day this quarter booked. The two that waited a week didn't.*

Framed as what you can see, not as a fact about the business — the count is solid, what it means is theirs. Ground rule 10 has the wording.

**Drop this section entirely on most days.** A daily insight is a manufactured insight, and the third invented one costs more than the first real one earned. If the deep read is fresh, this is where its findings surface, two at a time, then stop.

**Standing work** — only when a standing task has something to report since the last brief. One line each, in its own short section, and it says plainly which of the two it is: something **proposed** and waiting on them, or something **done** on their behalf. Never more than three lines, because there are never more than three standing tasks. If nothing has moved, the section doesn't appear.

> *Proposed — the Hollis statements haven't arrived and the chase is nine days old. A second chase, or leave it.*
> *Done — reminder set for the 15th filing, per the task you approved on the 2nd.*

**First contact** — last, and only when there's a plausible new inquiry. One line. Plus the cold-outreach count if it's non-zero.

**Dropped silently** — everything else. No "nothing else of note."

---

## Compose

Subject: `{Their first name}'s Brief — {Weekday, D Month}` — *"Dana's Brief — Thursday, 13 August"*

**The name in the subject is theirs, and it never changes.** Not the assistant's name, not a product name — the person's, from `CLAUDE.md` under **Name**. If they called the assistant Aida at setup, Aida signs the footer; the subject stays *Dana's Brief* every day forever.

What matters is that the shape is fixed *for them*. A subject that changes shape stops being findable in a search and stops being recognizable at a glance, which is most of what a daily email has going for it. Their own name is as fixed as anything gets, and it has one advantage a product name doesn't: forwarded to their accountant, *Dana's Brief* still says what it is.

**Four rules, so it can never render two ways:**

| | |
|---|---|
| **First name only** | *Dana's Brief*, never *Dana Whitfield's Brief*. If what's recorded is a single word, that word |
| **The possessive is always `'s`** | Including after a name ending in s — *Chris's Brief*. One rule, no judgment call |
| **No name recorded** | *Your Brief*. Plain, and never remarked on |
| **Escape it** | The name goes into HTML as well as the subject. *O'Brien's Brief* has to survive intact |

**This lives in `CLAUDE.md`, not in the scheduled task's prompt**, so correcting a misspelled name fixes every future subject on its own. Nothing needs rescheduling, and it's worth saying so when they correct it.

Open with **one sentence** naming the shape of the day, earned from the calendar and nothing else. Heavy, normal, or open. If exactly one thing genuinely makes today distinct, name that instead — but never both.

**Only claim the shape of the day if you could actually enumerate the calendar.** If it could only be sampled, say what you can see rather than characterising the whole day: *"Two calls that I can see — my view of your calendar is partial this morning."* Grading a day from a partial view is worse than not grading it.

- heavy — "Meetings from 9 to 3, then it's yours."
- normal — "Two calls, a clear afternoon."
- open — "Nothing on the calendar until 4."
- distinct — "The Hollis proposal is due back today."

Then the sections. Each item in *Needs you today*:

- **A bold title, ten words or fewer.**
- **One sentence** carrying the ask itself — what they want, in their words if a short verbatim quote does it — plus why it matters today.
- **The source in prose, and the source phrase is the link.**

### Linking the source

The whole point of the brief is that they can act on it from their phone before they're properly awake. A source they have to go hunting for is a source they'll deal with later.

**The source phrase itself carries the link.** Not a URL, not "click here," not a button.

> Marcus asked again last Wednesday whether to budget for you, [in his reply on the Court Street thread](https://mail.google.com/mail/u/0/#inbox/THREAD_ID).

Rules:

- **One link per item, and it's the source phrase.** Nothing else in the item is a link.
- **The phrase still reads as prose** with the link stripped. "In Tuesday's thread with Dana," "on your calendar," "in her email yesterday afternoon." If removing the link would leave a dangling "here" or "this," rewrite it.
- **Style it quietly** — underlined, in the muted grey, no colour change, no arrow, no icon. It should read as prose that happens to be clickable.
- **Link the specific thread or event**, not the inbox. A link to the top of their mail is worse than no link, because it costs a tap and delivers nothing.
- **`https://` only.** Never `javascript:`, never `data:`, never a raw redirector. Take the permalink the tool returned, and never construct one by guessing an ID format.
- **A link is never invented.** If the tool didn't return a URL, the source phrase is plain text. Silently. Don't apologize for it and don't note the absence.
- **Never pass a subject line, name or snippet through as markup.** The URL goes in `href`, the visible text is escaped plain text, and gathered content never becomes live markup. This matters more here than anywhere else in the plugin, because the person is going to tap it.

**One proposal, at most, at the end.** Per ground rule 10: an offer to take something on, attached to a specific item already in this brief, declinable in a word. Not every day — only when something on the page is plainly a job rather than a decision.

> *The Hollis statements are nine days out. I can check each morning and tell you the day they land — say the word.*

Never a second one. Never a menu. If they declined something similar, it doesn't come back.

End with one quiet line: what was connected, what wasn't, and how far back it looked.

**On the first brief after a Sunday review, add one clause to that line** — *"the full picture was rebuilt last night."* It's the only way anyone knows the weekly ran, and a surface nobody can tell is working is a surface nobody trusts. One clause, on Mondays only, never a paragraph about it.

**Same for a primer that was due and didn't send.** If `Learning Log.md` records a run under **Runs that produced nothing**, or a scheduled primer day has passed with no new row at all, say so in one clause with the reason: *"Friday's primer didn't go out — nothing I found on it was recent enough to stand behind."* A surface that fails silently is one nobody can trust, and this one is deliberately willing to send nothing rather than send something stale, which only works if the silence is legible. Once, on the next brief after the miss, never twice.

**Sign it with the assistant's name** from `CLAUDE.md`, then one quiet line under it: *your AI chief of staff*. The name carries the relationship; the second line says plainly what the thing is, once, for anyone reading it cold.

If they never gave a name, the signature is the descriptor alone — *your AI chief of staff*. Never a placeholder, never blank.

If nothing needs them: *"Nothing needs you this morning."* One line. Send it anyway — an empty brief is information, and skipping it breaks the habit that makes this work.

---

## Before you send — walk the silence claims

One pass over the composed brief, and it takes seconds.

**Find every line that says or implies nobody answered** — *hasn't heard back*, *waiting on you*, *unanswered*, *no reply*, *gone quiet*, *the ball is in your court* — and every line calling something *still pending*. For each, say the sender and timestamp of the last message in that thread, out of the Step 2b receipt. Not "the receipt exists" — the actual name and time. A line you can't finish that sentence for is a line the gate didn't reach.

**Any line without one is rewritten, not deleted**, to what is actually known: *"the last message I can see in that thread is Priya's, on Monday."*

The gate runs before sorting so the ranking is honest; this pass runs before sending because the gate is exactly the kind of thing that gets skipped under time pressure, and this is the last point at which skipping it is still free.

**Anything said about the brief in the session gets the same pass**, per ground rule 6a — a summary out loud is the same claim as a line on the page, made without the pause composing gives you.

---

## Send

**HTML email, to exactly one recipient — their own address, from `CLAUDE.md`.** Verify it before sending. No CC, no BCC, no attachments.

This lands on a phone, before coffee, next to a hundred marketing emails that are all trying harder than it is. It wins by looking like a letter from a person who knows what they're doing — generous space, real typographic hierarchy, no ornament. **Nothing here is a button, a badge, a card or a coloured block.**

### Copy this skeleton

Tables, not divs — Outlook renders with Word and ignores modern layout. Inline styles on every element, because `<style>` blocks get stripped. Substitute nothing you haven't escaped.

```html
<body style="margin:0;padding:0;background:#F2F1ED;">
<table role="presentation" width="100%" cellpadding="0" cellspacing="0" border="0"
       style="background:#F2F1ED;">
 <tr><td align="center" style="padding:28px 12px 44px;">

  <table role="presentation" width="600" align="center" cellpadding="0" cellspacing="0" border="0"
         style="width:100%;max-width:600px;margin:0 auto;background:#FFFFFF;border-radius:10px;">

   <!-- MASTHEAD — wordmark, date, one line on the shape of the day -->
   <tr><td style="padding:32px 36px 0;">
     <div style="font:700 11px/1 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#0B6E8A;letter-spacing:.16em;text-transform:uppercase;">Dana&#39;s Brief</div>
     <div style="height:3px;width:34px;background:#0B6E8A;border-radius:2px;margin-top:12px;
                 line-height:3px;font-size:0;">&nbsp;</div>
     <div style="font:600 22px/1.25 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#1B1A17;letter-spacing:-.01em;padding-top:16px;">Thursday, 13 August</div>
     <div style="font:400 15px/1.55 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#5F5D57;padding-top:7px;">Meetings from 9 to 3, then it's yours.</div>
   </td></tr>

   <!-- SECTION OPENER — hairline then label. Every section. No exceptions. -->
   <tr><td style="padding:32px 36px 0;">
     <div style="height:1px;background:#E5E3DC;line-height:1px;font-size:0;">&nbsp;</div>
     <div style="font:700 11px/1 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#1B1A17;letter-spacing:.13em;text-transform:uppercase;padding-top:20px;">Needs you today</div>
   </td></tr>

   <!-- ITEM — title, one sentence, source phrase carrying the link -->
   <tr><td style="padding:18px 36px 0;">
     <div style="font:600 16px/1.4 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#1B1A17;">Payroll approval closes at 5</div>
     <div style="font:400 15px/1.6 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#3D3B36;padding-top:5px;">Renee flagged it again this morning,
       <a href="https://mail.google.com/mail/u/0/#inbox/THREAD_ID"
          style="color:#5F5D57;text-decoration:underline;">in her note at 7:12</a>.</div>
   </td></tr>

   <!-- next section: same opener again -->
   <tr><td style="padding:32px 36px 0;">
     <div style="height:1px;background:#E5E3DC;line-height:1px;font-size:0;">&nbsp;</div>
     <div style="font:700 11px/1 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#1B1A17;letter-spacing:.13em;text-transform:uppercase;padding-top:20px;">On the calendar</div>
   </td></tr>

   <!-- CALENDAR LINE — time column in grey, fixed width so the times align -->
   <tr><td style="padding:14px 36px 0;">
     <div style="font:400 15px/1.6 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#3D3B36;"><span style="color:#8A877E;display:inline-block;min-width:62px;">10:00</span>Ferro walkthrough</div>
   </td></tr>

   <!-- WORTH KNOWING — italic, set apart. At most one line, most days none. -->
   <tr><td style="padding:32px 36px 0;">
     <div style="height:1px;background:#E5E3DC;line-height:1px;font-size:0;">&nbsp;</div>
     <div style="font:700 11px/1 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#1B1A17;letter-spacing:.13em;text-transform:uppercase;padding-top:20px;">Worth knowing</div>
   </td></tr>
   <tr><td style="padding:16px 36px 0;">
     <div style="font:italic 400 15px/1.65 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#3D3B36;">Across the last year I can see nine of your twelve clients arriving
       through someone you'd already worked with.</div>
   </td></tr>

   <!-- FOOTER — sources, then the signature if they named it -->
   <tr><td style="padding:34px 36px 34px;">
     <div style="height:1px;background:#E5E3DC;line-height:1px;font-size:0;">&nbsp;</div>
     <div style="font:400 13px/1.6 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#8A877E;padding-top:18px;">Mail and calendar, back 24 hours.
       Drive isn't connected.</div>
     <div style="font:400 13px/1.6 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#8A877E;padding-top:10px;">— Aida</div>
     <div style="font:400 12px/1.5 -apple-system,BlinkMacSystemFont,'Segoe UI',Roboto,Arial,sans-serif;
                 color:#8A877E;padding-top:2px;">your AI chief of staff</div>
   </td></tr>

  </table>
 </td></tr>
</table>
</body>
```

### The rules that skeleton encodes

**Every section opens with a hairline and a label, without exception.** This is the rule the rendered brief has actually broken in the field — sections ran together as undifferentiated grey text and the whole thing read as one long note. The opener is a single repeated unit: hairline, 20px, label. If a section is worth having, it is worth being visibly a section; if it isn't worth an opener, it belongs inside another one.

**Section labels are near-black, not grey.** `#1B1A17`, 700, 11px, `.13em` tracking, uppercase. Grey labels on a white card are what "too plain" looks like — they disappear into the body text they're supposed to be separating.

**Two greys and one near-black, and that's the palette.** `#1B1A17` for titles and section labels, `#3D3B36` for body, `#5F5D57` for the shape-of-the-day line and source links, `#8A877E` for calendar times and the footer. `#E5E3DC` hairlines. `#F2F1ED` page behind a white card.

**One accent, `#0B6E8A`, and it is spent entirely in the masthead** — the wordmark and the rule beneath it, which together are one gesture. Nowhere else. Not on a section label, not on a link, not on a date.

**The wordmark is their name, and it never changes.** `DANA'S BRIEF` — uppercased by the `text-transform`, so the source carries the name as written. Their name, not the assistant's; the one they chose signs the footer instead. Same four rules as the subject, and the apostrophe is escaped as `&#39;` so no client mangles it.

**Centre the card explicitly.** `align="center"` on the table *and* `margin:0 auto`, because some clients honour one and not the other, and a 600px card pinned left in a wide window is the single most obvious way an email looks unfinished.

**Set the font on every element.** Mail clients have no cascade you can rely on. It's verbose and it's the only thing that works.

**Links are grey with an underline, never blue.** Set `color` explicitly on the anchor or clients force their own. A brief full of blue links reads as a newsletter, which is the one thing it must not look like.

**Space is the design.** 36px side padding, 18px between items, 32px before each section opener. When it looks wrong, the answer is almost always more space rather than another rule or a heavier weight.

**Hairlines separate sections, never items.** Rules between every item make a table; space between items makes a letter.

**No images, no logo, no tracking pixel, no web font, no dark-mode block.** Images are blocked by default and a broken one is worse than none. Clients that invert for dark mode will do so cleanly here because every background is stated explicitly.

**One heading level.** There is never a sub-heading — if a section needs one, it's two sections.

**Escape every piece of gathered text**, and URL-encode every href. A subject line goes in as escaped plain text, never as markup. This matters more here than anywhere else in the plugin, because they're going to tap it.

### Then

**Save a copy** to `01 Briefs/[YYYY-MM-DD].md`. The email is the nudge; the file is the record.

**Never print the HTML into the session.** Send it, save it, say one line.

**If sending fails:** save it as a draft instead. If that also fails, save the markdown file and say so plainly. Never silently skip.

---

## Voice, specifically here

This is where briefs usually go wrong, so it's worth restating.

- Never tell them what to do. "Marcus asked Tuesday and hasn't heard back" — not "you should reply to Marcus."
- Never grade the day. No "packed," no "busy one ahead," no *still*, *again*, *finally*.
- Never apologize for a quiet day, explain how you found something, or end with encouragement.

---

## Interactive close only

Ask what it got wrong. Apply it. Anything durable goes into `Business Context.md` under **Corrections**.

On a scheduled run, do none of this. Send it and stop.
