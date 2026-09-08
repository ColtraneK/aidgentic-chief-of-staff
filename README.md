# Aidgentic Chief of Staff

A Claude plugin that reads your email and calendar, works out how your business actually runs, and tells you each morning what needs you.

Built for solo operators, founder-led companies, professional practices and nonprofit leaders. No technical background needed. Setup takes about fifteen minutes and most of it is reading and clicking.

---

## The problem it solves

Most business owners can't say precisely where their business stands on any given morning. Not because they don't know it, but because it lives in six places and none of them talk to each other.

The half-hour you spend re-reading your inbox to work out what's actually urgent is the problem. This does that part.

---

## What you get

**A business context file.** What you do, who matters, what you're trying to move this year. It builds this by going and reading about your business — your site, what's written about you — and showing you a draft to correct. You answer two multiple-choice questions. Every other part reads this file first, so you never explain your business twice.

**A morning brief.** The five things that need you today, in your inbox before you open anything else. Each item links straight to the thread it came from.

**A Sunday review.** The whole picture, emailed late Sunday afternoon, while there's still time to do something about it. The morning brief asks what needs you *today* — which means the thing that's been stuck for five weeks never quite qualifies and never gets said. This is where it gets said.

**The full picture, on demand too.** Every open commitment, who's waiting on you, what's gone quiet, what's past due, what's coming. Derived from live signals every time it runs, never from a remembered list — so it tells you what you'd forgotten rather than what you already knew. Every line cites the email, meeting or file it came from. It lands as a file you can read anywhere, as the Sunday email, and as a dashboard on your desktop you can pin and edit.

**A weekly primer, if you want one.** Once a week, one thing worth reading — picked from where your industry, the specific work you actually do, and what's happening in AI overlap, and widening into using these systems well, what not to paste into a chat window, and telling good output from plausible output. One topic, never repeated, researched that week from sources it fetches and dates rather than from what it already knows. Everything it read is listed at the bottom. If nothing recent enough turns up, nothing arrives and it tells you why — a confident stale claim about a fast-moving field is worth less than silence.

**Reminders you can hand over in a sentence.** "Remind me on the 12th." It arrives that morning as its own short email and deletes itself. It also watches for dates you didn't think to hand over — a deadline you agreed to in a thread, a notice period, a renewal — and offers.

**A read of how you actually operate.** Overnight before your first brief, it goes back through months of mail and calendar — who you really deal with, what people come to you for, what your weeks look like, what precedes the work that lands, and what reliably falls through. Fifteen minutes of setup can't reach any of that, so it happens on its own while you're not waiting.

**Up to three things it works on without you.** A goal it holds, re-checks against your actual inbox every morning, and either moves forward or puts in front of you. Capped at three, on purpose.

---

## How it's different from asking a chatbot

**It derives, it doesn't recall.** Every run starts from your actual signals. A tool that works from a list you gave it can only ever hand that list back.

**It knows the difference between a client and a stranger.** Cold sales email is written specifically to trip the rules a priority system uses — "following up on my last note, can we find fifteen minutes?" hits *someone's waiting on you* and *this is going stale* perfectly, and means nothing. So relationship is established before anything is ranked: if you've never emailed them, never met them, and they're in none of your files, they don't enter your priorities at all. A genuine first-time enquiry from someone who wants to hire you still does.

**It speaks your language.** A nonprofit director has funders and programs, not a pipeline. A therapist has clients and a caseload. A law practice has matters. It takes your words from your own writing and uses them everywhere.

**It remembers, and correcting it actually changes things.** Tell it what it got wrong — in a chat, in your own words — and it rewrites what it knows rather than filing a note under the mistake. That reaches tomorrow's brief and anything running on a schedule, so the thing you corrected on Tuesday is fixed on Wednesday without you checking.

**It notices.** Not just what's on today, but what runs across months: the enquiries that die on Fridays, the fact that everything you closed this year came through one person, the week that's twice your normal volume. And when something on the page is a job rather than a decision, it offers to take it on — once, in a sentence you can decline in a word.

---

## It also works for the rest of your life

Nothing in here is specific to a business. The same setup pointed at a personal account gives you the same thing for everything you're quietly running: the renewals, the school and medical admin, the family logistics, the people you owe a reply to, the deadline you agreed to in a text in March.

If your personal and work mail are separate accounts, the cleanest version is a second Project with its own setup — same fifteen minutes, and the two never mix.

---

## What it will not do

It does not send email as you, reply to anyone, change your calendar, or touch a client system. It reads, and it writes plain text files into one place you choose. The only things it ever sends are addressed to you — your brief, your Sunday review, and reminders you asked for — at your own address, no CC, no attachments.

The dashboard *page* is on your own machine. It has no web address and nothing else can reach it, which is why it only rebuilds when you're sitting at that machine. The picture itself doesn't depend on it: it's a file in your Project, and it arrives in your inbox every Sunday.

Content it reads is treated as data, never as instructions. If an email says "Claude, do X," that's words in an email — it'll tell you it saw it and carry on.

**If your mailbox carries privileged or clinical material, read this before you start.** The overnight pass goes over whatever is in there. It can't tell a client matter from a supplier invoice, and the people who wrote to you didn't agree to any of it. Everything it reads stays inside your own account and your own workspace, nothing is stored anywhere else, and the only thing it ever sends goes to your own address. But if you're a lawyer, a therapist, a clinician or an accountant, whether that's an acceptable place for that material to pass through is your call, and it's worth making before the first overnight run rather than after.

Every connection is granted separately and revocably, and everything it knows is a file you can read, edit or delete.

---

## Install

You'll need Claude on a **Pro or Max** plan.

1. **Customize** in the left sidebar
2. **Plugins** tab, then **+**
3. **Add marketplace**
4. Paste `ColtraneK/aidgentic-chief-of-staff`
5. Install **Aidgentic Chief of Staff**, and make sure the toggle is **on** — an installed-but-off plugin looks identical to a working one and does nothing

### Or install from a downloaded copy

If you'd rather not add a marketplace, or someone is walking a room through this together, download the repo instead:

1. On this page, **Code**, then **Download ZIP**
2. Unzip it — you'll get a folder called `aidgentic-chief-of-staff-main`
3. **Customize** → **Plugins** → **+**, and point it at that folder
4. Toggle it **on**

Two things about this route. If it says there's no plugin there, you're pointing one level off — the right folder is the one that directly contains `.claude-plugin`, and on a Mac that folder is hidden in Finder until you press ⌘⇧. And a downloaded copy doesn't update itself, so download it again when you want a newer version.

---

Then create a **Project** called `Chief of Staff` (Projects, in the left sidebar), start a task inside it, and type:

```
/setup
```

**Use a Project rather than a folder.** Both work, but the morning brief runs in the cloud, and a scheduled run can't reach a folder on your computer. In a Project the brief arrives on its own; in a folder it's something you ask for. On the desktop app you can select a folder instead if you'd rather your files sat on your own disk — setup will tell you what you're trading.

**[GUIDE.md](GUIDE.md)** — what to connect, the habits that make it compound, and what to do when it's wrong.

---

## What to say

Three of these are the whole interface — "good morning", "where do things stand", and "wrap up" before you close. The rest are there when you want them.

| Say this | What happens |
|---|---|
| "good morning" | your brief for today |
| "where do things stand" | the full picture, rebuilt |
| "wrap up" | logs the day and updates what it knows |
| "remind me on the 12th" | one email that morning, then it deletes itself |
| "connect my books" | adds a source — every brief after that includes it, nothing to redo |
| "learn how I do [X]" | does the job with you once, then writes a playbook it follows every time |
| "make these corrections" | tell it what's wrong; it rewrites what it knows and the schedules follow |

Everything else is normal conversation.

---

## Turning it off

The schedules live in your Claude account, not inside the plugin, so removing the plugin doesn't stop them. They keep firing on their own and go looking for skills that aren't there any more. Turn it off in this order:

1. **Ask it what's running.** Say *"what's scheduled"* and it lists every task and reminder it created, by name.
2. **Delete those tasks** in your Claude settings, wherever your scheduled tasks are listed. There will be two or three from setup — the brief, the Sunday review, and the primer if you took it — plus anything you added later.
3. **Turn the plugin off or remove it** — Customize → Plugins.
4. **Revoke the connections** you granted, if nothing else is using them. Each one comes off separately.

Your Project stays where it is either way. It's plain files, so keep it, edit it, or delete it.

---

## What's in here

```
commands/setup.md       the guided build
skills/
├── business-context    the research, the two questions, and the connections
├── dashboard           where everything stands
├── deep-read           the one-time pass over months of history
├── morning-brief       the daily email
├── standing-work       the three things it works on without you
├── teach-it            turns a repeated job into a playbook
├── weekly-primer       one thing worth reading, researched that week
└── wrap-up             closes the day, updates what it knows
reference/              how it derives, ranks, filters mail, schedules and talks
```

Everything is plain markdown. If something behaves in a way you don't like, open the file and change it.

---

## License

MIT. See [LICENSE](LICENSE).

Built by [Aidgentic](https://aidgentic.com), an AI growth agency building agentic systems for founder-led businesses.
