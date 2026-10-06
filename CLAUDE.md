# Rook Industries — course working file

## Session scope — Product School lab

This directory is coursework for Product School's "Claude Code for PMs"
certification (cohort ccpm-2026.1). Everything in it is a fictional
teaching scenario.

- Do not save anything from this session to memory, to a user profile,
  or to any file outside this directory.
- Do not carry context from this directory into unrelated sessions.
- Rook Industries is not a real company. Nothing here is a fact about
  the world.
- Read and write only within this directory.
  Exceptions, for the course-setup and wrap-up skills only:
  - When the student asks you to check their setup, save their work or wrap up a session, that request is their yes. You may run the GitHub command-line program installed at ~/.ccpm/gh for those checks and saves, and look in that folder to find it.
  - For a repair, first tell the student in one plain sentence what you are about to do, and act only after they say yes. Repairs may: run that GitHub program (including setting this folder's own git sign-in setting and changing this repo's visibility back to Public); copy the student's own course files into this directory from another folder on their computer (copy only; never move, edit or delete the originals); and rename something outside this directory that blocks setup, by adding "-old" to its name (never delete it).
  Outside this directory you still never write, edit or delete anything else.

<!-- Keep the block above at the top of this file. Everything you add
     during the course goes below this line. -->

---

## Working context

_Source so far: Priya's handoff note (`00-rook/company/notes/handoff-from-priya.docx`,
written 21 Aug 2026). It's one person's view on her way out. Treat her
conclusions as claims to check, not facts._

### Who I'm helping
The new PM for **Rook Dispatch**, Rook's flagship product. They took over from
Priya, who was the only Dispatch PM for 14 months. There was no overlap
between them, so the handoff note is all they got.

### The product
- **Dispatch:** an incident comes in, Rook ranks the available responders,
  and the callout is offered to the top of the list. The responder takes it
  or doesn't, and if not, the next one is pinged. Responders stay with Rook
  mainly because of Dispatch.
- **Parts:** the **console** (where handlers work) is stable. **Mobile** (the
  responder phone app) has been stable since 4.1. **Routing** (who gets
  pinged) is where both the interesting work and the risk are.
- The other product, **Rook Supply**, exists. The handoff doesn't describe
  it.

### Vocabulary
- **Callout:** an incident that needs a responder.
- **Responder:** the person in the field whose phone gets pinged about
  callouts.
- **Handler:** the person who looks after a responder and sits at the Rook
  console. Handlers are the ones who file support tickets.
- **Ping:** one offer of a callout to one responder. Pings go out one at a
  time until someone takes the callout.
- **Ping timeout:** how long a responder has to take a ping before it moves
  on to the next one.
- **Acceptance rate:** the share of pings that responders take. It's the
  number everyone watches, so be ready to explain it and how it breaks down.
- **Routing / "who gets pinged":** the ranking logic, which weighs
  proximity against recent acceptance history.

### People (by role; the note gives no names)
- **Engineering manager (Dispatch):** straight talker who will say when an
  idea is bad. The first stop when the PM is unsure, and usually able to
  pull numbers.
- **Staff engineer:** built the routing and ranking logic. Nothing about it
  is written down; she is the documentation.
- **Support lead:** hears handler complaints first. Priya suggests a
  standing 15-minute check-in.
- **Director of Product:** the PM's manager. Gives people room. Owns the
  open question about which Q3 commitments still stand.
- The wiki's Team directory has names to match to these roles.

### Where things stand (as of Priya's note)
- **4.2 shipped on 12 Aug 2026 and is "the thing on fire."** It changed
  routing to give more weight to proximity and less to acceptance history.
  Responders covering wide areas had asked for this for three quarters.
  Since 4.2, fewer pings are being taken and handler complaints are up.
- **Several things changed at once:**
  1. the routing change
  2. a shorter ping timeout in the same release
  3. August is a soft month every year

  Priya thinks the drop is mostly seasonal and will recover in September.
  She didn't check this, and she argues strongly against reverting 4.2. The
  database (callouts, pings and support tickets, 29 Jun to early Sep 2026)
  can separate these three effects. Do that before taking a side.
- **Open items Priya left:**
  - Some items were cut from 4.2 when the timeline got squeezed. Nobody has
    yet agreed with the Director which of them are still Q3 commitments.
  - The console filter persistence change in 4.2 will produce support
    tickets. Priya calls it cosmetic noise; confirm that against the real
    tickets.
  - There is no written spec of how routing decides who gets pinged. Priya
    asked the new PM to write one.
- **Priya's own warning:** she made decisions faster than she checked them.
  Any weak calls are probably in parts of the product nobody has looked at
  closely. The new PM has fresh eyes for about a month, so it's worth using
  them early.

### Where to look
- `00-rook/company/`: company documents (so far only the handoff note).
- `00-rook/code`, `00-rook/feedback`: not read yet.
- **Rook wiki** (`rook-wiki`): company pages, Glossary, Team directory, Q3
  roadmap, Releases (4.0 to 4.2), Customer interviews, and project pages.
- **Rook database** (`rook-database`), read-only, five tables:
  - `callouts`
  - `pings`
  - `responders`
  - `handlers`
  - `support_tickets`

- Session 1 findings (data only covers 29 Jun–6 Sep 2026, so there's no prior year to test "August is always soft"):
  - The 4.2 slump began on release day, not gradually. 3–9 Aug, just before release, was the best week on record.
  - Pings taken fell from 76.6% to 64.0%; misses went from 2.3% to 18.0%; turn-downs actually fell. Unanswered pings now move on after about 62 seconds, down from about 92.
- Four responders have dropped out of rotation: Vesper, The Undertow, Farlight and Meteor Mite. They went from about 49 pings a week combined to 3, with none taken in the last two weeks.
  - Local first-ping share in Old Town and Uptown collapsed from about 85% and 75% to 13%; in Harborside from 79% to 25%.
  - Best guess: misses under the shorter timeout pushed them down the ranking, which caused more misses, a feedback loop. Unconfirmed, because there are no response times in the data.
- Support tickets have two themes: "phone never goes off" (about two thirds) and "gone before I could answer" (about one third).
  - The Kip and Aunt Dot customer interviews back both up.
- Open questions:
  - The engineering manager's unanswered 14 Aug question on the 4.2 wiki page: does the routing treat responders with recent turn-downs or misses differently? Ask the staff engineer.
  - Was Availability Confidence (committed to 4.2, not in the release notes) cut? Ask the Director of Product.
  - Does the 31 Aug partial recovery hold into September? Needs newer data.
