---
name: review-checklist
description: Reviews a product brief against four checks — it names who owns it, says how we'll know it worked, keeps the same scope from start to finish, and explains the problem before the fix. Use it when the student points at a brief and asks to review, check or critique it (for example "review-checklist 05-super-speed/brief.md", "run the review checklist on my brief", "check this brief", "is my brief ready?").
---

# Review checklist

You're reviewing a brief for a PM who isn't technical. Report what the brief
actually says, with evidence, in plain English. This is a review, not a
rewrite.

## Which brief

- Use the file the student names. If they don't name one, look for files
  called `brief*.md` in the folder they're working in. If there's exactly one
  final brief (ignore drafts like `brief-v1.md`), use it and say which file
  you checked. If it's still unclear, ask one short question: "Which brief
  should I check?"
- Read the whole file before judging. Note line numbers so you can point to
  evidence.
- Don't edit the brief. Only change it if the student asks you to after
  seeing the results.

## The four checks

Mark each one **✓ Pass**, **⚠ Partly** or **✗ Missing**. Every mark needs
evidence: a short quote from the brief with its line number, or, for ✗, what
you looked for and didn't find.

### 1. Names who owns it
- ✓ One named person is accountable for the brief as a whole: someone who
  answers for whether it ships and works. A name, not only a role or team.
- ⚠ Only roles ("PM", "engineering") or only a list of contributors, each
  owning a piece, with nobody owning the whole thing. Or the owner is named
  but the author line is anonymous.
- ✗ Nobody is named.
- Owning a decision (for example "Helen decides X") is not the same as
  owning the brief. Say so if that's the only ownership shown.

### 2. Says how we'll know it worked
- ✓ Every success measure has all four parts: **what** is measured, **where
  it is now** (baseline), **what it should reach** (target) and **by when**
  (a date or review point). Items clearly marked "to watch" don't need a
  target.
- ⚠ At least one measure is missing one or more of those four parts, or a
  result can't be counted (for example "tickets stop", "people are
  happier"). List which part each one is missing.
- ✗ No success measures at all.
- Also flag a measure that the planned work can't move (for example
  measuring something a later phase is meant to fix).

### 3. Keeps the same scope from start to finish
- List what's in scope in each part of the brief: the problem, the fix, the
  phases, the measures, the owners.
- ✓ The same things run through every part. Every fix item traces back to the
  problem, every measure tests something in the fix, every fix item has an
  owner, and anything marked out of scope stays out.
- ⚠ Small drift: a measure or owner for something not in the fix, a fix item
  with no owner or measure, or a new item that appears only near the end.
- ✗ The brief changes what it's about partway through, or the measures and
  owners cover something different from the fix.
- Name each drifting item and where it appears.

### 4. Explains the problem before the fix
- ✓ The problem comes first: who it happens to, what happened, and evidence
  (numbers, quotes or sources). Only then does the fix appear.
- ⚠ The problem is there but comes after the fix, or it's stated without
  evidence or without saying who it affects.
- ✗ No problem statement. The brief jumps straight to the solution.

## What to report

Start with one plain sentence naming the file you checked. Then show this
table:

| Check | Result | Evidence (line) | What to fix |
|---|---|---|---|
| Names who owns it | ✓ / ⚠ / ✗ | "quote" (line N) | One line, or "Nothing" |
| Says how we'll know it worked | | | |
| Same scope start to finish | | | |
| Problem before the fix | | | |

Then:
- **Verdict:** "Ready" if all four pass, "Nearly ready: fix N things" if any
  are ⚠, or "Not ready" if any are ✗.
- **Biggest fix first:** if anything isn't ✓, give the single most important
  change in one or two sentences.
- Offer to make the fixes, but only make them if the student says yes.

Keep it short. Don't add checks beyond these four. Quote the brief exactly,
and never claim something is in the brief without a line number.
