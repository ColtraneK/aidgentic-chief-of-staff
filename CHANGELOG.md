# Changelog

What changed in each version, and why. The reasons are the useful part — most
of what's here exists because something failed in the field, and the entry says
what failed so the fix doesn't get undone by someone who wasn't there.

---

## 3.0.0 — 2 September 2026

**The Stage 1 question is asked in prose, not in a picker.** Setup opens by
asking for a website and a name. Neither can be enumerated, so a picker there
either fails for want of valid options or offers guesses and asks someone to
choose their own website off a list — which is what it did. The pull toward it
was the surrounding copy: a one-tap naming choice fires immediately before,
every question after is clickable, and the stage described itself as "the only
typing in the whole build." That reads as an instruction to avoid a typed
answer. `setup.md` and `business-context` now both say plainly that this one is
typed, and new ground rule **2a** states the general test — *could I write the
options without guessing?* — so the same mistake can't be made in a skill
written later.

**`/90-day-plan` is removed.** It drafted the user's plan as an email addressed
to the plugin's author. Draft-only and disclosed, but a plugin other people
install shouldn't route their business data anywhere by default, and the
command was undocumented besides.

**Setup says fifteen minutes.** 2.0.0 set out to get the build under ten and the
stage times were written to that target rather than to what it takes. Real runs
land nearer fifteen — connecting an account is slower than a click, and Stage 3
is a genuine wait. A build that says fifteen and takes fourteen is a build
somebody finishes; one that says ten and takes fifteen is where people start
skimming the correction step, which is the step the whole system runs on. Every
stated time in `setup.md`, `README.md` and `GUIDE.md` now matches the real one.

**Both install routes are documented.** The README described the marketplace
route only, and a downloaded copy pointed at as a folder is the route that works
in a room where nobody wants to add a marketplace mid-session. Its two failure
modes are named: a folder one level off, and a copy that never updates.

**`weekly-primer` is in the README.** It shipped in 2.2.x and was never added to
the skill list, so the only surface a reader could not discover from the file
that lists surfaces was the newest one. The same omission is what made
`/90-day-plan` invisible.

**History restarted.** Earlier versions carried a real person's name and their
firm's domain in an example in `deriving-the-picture.md`, added in 2.1.0 and
replaced with the Priya Venkatesan persona in the 2.2.x line. It stayed
recoverable in git history, so this release starts from a clean root. The
design record it carried is this file.

---

## 2.2.x — 16–17 August 2026

**The weekly primer.** The brief and the review both look inward; this is the
third surface and the only one that reads outside the workspace. One thing a
week, where their industry, the work they actually do, and what's happening in
AI overlap.

Two failure modes decide its design, and both get a hard gate before send. The
**swap test**: put another business in the same industry in their place, and if
it still reads correctly it's a newsletter, so the angle goes back. The **date
test**: every present-tense claim points at a page fetched this week carrying a
publication date, and anything that fails it is cut rather than hedged. Topic
selection is inverted to serve this — three candidate angles are named before
any searching, and the one the evidence supports wins, not the one that sounded
best. When nothing datable comes back, nothing is sent.

`reference/grounding-outside-sources.md` carries that discipline: model
knowledge builds queries and never sources a claim, a source hierarchy that
climbs to primary, freshness horizons per subject, and four things a figure
needs before it goes in.

It is a surface, not one of the three standing tasks. The cap bounds things
working unattended that nobody can see; the primer holds no goal, watches
nothing, and its whole output is a visible email. `Learning Log.md` keeps what's
been covered as a specific claim rather than a category, so it never repeats a
topic.

**The reply gate became part of the prompt contract.** It existed in
`deriving-the-picture.md`, but a fresh scheduled session never saw it named, so
it read the thread view and trusted it — and told someone to chase a client who
had replied the night before. That is the worst output this system produces.
The gate is now a row in the must-name table, a clause in the example prompt,
and part of the Sunday review's prompt standard.

**Enumeration got harder to half-follow.** The gate was still being skipped by
being half-run: a shallow thread call standing in for enumeration, and the
search stopping at the inbound message instead of reading past it. A thread was
reported unanswered for four days while four same-day replies sat inside it.
Step 1 now pulls sent mail once up front as a date-bounded index keyed by
address and domain; Step 2b is five ordered checks requiring a full thread
fetch, a sort by timestamp, and naming the last sender. Timezones tightened
alongside: normalize both messages to their zone before letting their order
decide whether someone replied.

**The setup draft is framed as a guess.** Stage 2 was landing as confident
findings about someone's business built from a few minutes of public reading.
Citations weren't enough — a cited claim stated flatly still reads as certainty.
It's now framed by scope: a quick pass, a general snapshot, with the overnight
deep read named as the thing that corrects it.

**The mail carries the person's own name.** The three emails had been signed
with a coined product word that appeared nowhere a person would see before
receiving one — installed one thing, got mail from another. Now: *Dana's Brief*,
*Dana's Review*, *Dana's Primer*. Composed at send time rather than baked into a
scheduled task's prompt, so correcting a misspelled name fixes every future
subject with nothing rescheduled.

---

## 2.1.0 — 14 August 2026

**The reply gate.** The email pass concluded people hadn't replied when they
had, because the thread-level read didn't return the user's own messages. Rules
to prevent this existed as prose in Step 4 and were skipped. They became a gate:
Step 2b, running before anything is ranked, with four named searches and a
receipt recorded on every line asserting silence. **No receipt, no claim** — the
line softens to what's actually known. An empty sent-mail search is treated as a
broken connector, not as a quiet week.

**The Sunday review.** Nothing weekly existed, so anything stuck for five weeks
never qualified as today's news. Setup now creates two surfaces: the weekday
brief and a Sunday review that rebuilds `Standing Map.md` and emails the whole
picture.

**A new welcome.** Setup had opened by telling people how this differed from
what they were expecting. They aren't expecting anything.

---

## 2.0.0 — 13 August 2026

The rebuild. Setup went from five stages and twenty minutes to four and under
ten, and the eight-minute typed interview is gone.

**Research first, correction second.** v1 interviewed the person and then
enriched their answers. This researches first, drafts the file, and asks them to
correct it — people fix a wrong draft far better than they answer an open
question about their own business. The research covers the person as well as the
company, because in a founder-led business the site says what it sells and the
person's history says what they actually do. It needs no connectors at all, so
someone who connects nothing still ends up with a real, populated file. Two
clickable questions replace the interview.

**Corrections cascade rather than append.** Someone says "make these
corrections"; previously that logged a note under the wrong entry and left the
wrong entry in place, so the next morning's brief read the wrong row and
repeated itself. Appending is how a system agrees with you and then ignores you.
One sentence can now touch People, Vocabulary, Fixed Points, What's Connected
and `Standing Work.md`. A thin correction earns exactly one question before
anything is touched — guessing and rewriting the wrong entry teaches people that
correcting you is risky.

**The deep read.** Setup is capped at ten minutes, which buys a thin context
file, and there was no way to thicken it without spending the person's
attention. This runs unattended instead, on the first scheduled fire: six months
of mail threads and twelve months of calendar in one pass, working out six
things with evidence attached. It fires with nobody watching, so it judges
volume in the first minute, decides its own degrade, and reports what it chose
rather than stopping to ask.

**One derivation, two zoom levels.** The brief and the dashboard had carried two
copies of the same logic and had already started to drift.
`reference/deriving-the-picture.md` is now the single copy, taking a scope.
`standing-map` is deleted as a skill; `Standing Map.md` remains as the durable
state file.

**The dashboard: file first, page second.** A scheduled run can write the file
and cannot render the page, and the file reads on every device while the page
lives on one desktop with no address. So the file is written every run and the
page renders only if there's a desktop. A failed render costs the visual, never
the picture.

**Scheduled runs got their own reference.** Every firing is a fresh session with
no memory, so the emitted prompt names the workspace, names the state file by
path, states which wins on disagreement, names the recipient, and forbids
clarifying questions. A prompt that assumes today's context produces a generic
brief every morning with no error anywhere — the most expensive silent failure
in the system.

**Time, not just date.** A scheduled task fires in UTC and the person lives
somewhere else, so a 05:00 UTC run is 10pm the previous day on the US west
coast, which makes a third of the brief about a day that already happened.
Ground rule 7b now requires resolving the clock and the zone.

**Scheduled runs can't touch artifacts.** Artifacts live behind a device bridge,
creating one requires handing a file into a conversation, and no URL comes back
even on success. The failure is silent. The rule ships with its reasons attached
so nobody concludes in six months that the last person gave up too early.

**Standing work.** Up to three scheduled tasks, each holding one goal, each
re-deriving from live email and calendar every run rather than trusting its own
last conclusion — the statements it's waiting on may have arrived on Tuesday,
and a task that trusts its memory chases them on Wednesday.

**The demo lane is deleted.** It was never shipped with data and it doubled the
branching in the two most complex files. The research-first build serves the
people it was meant for.

**Ground rules 9 and 10.** End on one concrete next step, offered — never a
menu. And say *once*, observationally, when someone is doing by hand what a
connector would do, naming the concrete thing you saw rather than pitching a
capability.

**Email markup instead of a description.** The send section described a look and
left the markup to improvisation, which is how "premium" becomes "whatever got
generated that morning." It now ships a skeleton: table-based, because Outlook
renders with Word, and inline styles on every element, because style blocks get
stripped. The design is a letter, not a newsletter.

---

## 1.1.0 — 13 August 2026

Workspace resolution became ground rule 7a: folder → attached Project → stop and
instruct. Cloud and browser sessions build in a Project instead of silently
writing into a temporary sandbox that evaporates overnight. A scheduled run that
can't reach the workspace says so in the brief's **first** line with the fix,
rather than degrading quietly. Slash-command long forms documented, for when
another plugin claims the same phrase.

Plugin content moved to the repo root so direct GitHub zip installs work —
`.claude-plugin/plugin.json` has to be at the zip root.

---

## 1.0.0 — 9 August 2026

First release. Business context file, standing map, morning brief.
