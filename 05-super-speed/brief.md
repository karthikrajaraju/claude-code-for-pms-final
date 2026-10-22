# Brief: a fair way back for responders who go quiet

**For:** Helen Achebe · **From:** PM, Rook Dispatch · **Status:** proposal, before any code changes · **Source:** Rook database, 29 Jun – 6 Sep 2026
**Prototype:** `prototype.html` (handler and responder screens, release-day message), shown to Desmond or Kip by **6 Nov**, before Marcus.
**Dates:** Wen decides the fade rule by **30 Oct** · Phase 1 ships **12 Nov** · review **10 Dec**

## What happened to The Undertow
Before 4.2, The Undertow was Harborside's responder: 75 pings, 1 missed, about 9 jobs a week. 4.2 cut the **ping wait** from 90 to 60 seconds, and he missed 5 pings between 12 and 14 August. Routing scores a **missed** ping like a **turned-down** one (−0.12, against +0.08 for a **taken** one), with no recovery. Our leading explanation: this sank his **routing priority** (why these four missed more is unconfirmed). He took his last job on 17 August, and by September was going 9 days between pings.

Desmond Okafor's 11 tickets are all still open. The Undertow asked whether he was "still even in the system." Farlight, Vesper and Meteor Mite went the same way; six others took on their work.

## What we'd build
**1. A miss counts for much less than a no.** The code can't tell whether a ping arrived, so Phase 2 removes the penalty for undelivered pings. *The Undertow sees:* "Missed. This counts for much less than saying no."

**2. A bad week fades.** Wen's 2019 note weighed it both ways: a bad month shouldn't carry into the spring, but someone who has stopped taking work should stay down. *Proposal for Wen:* misses fade quickly and turn-downs fade slowly. Someone who has stopped working marks themselves unavailable, and their handler is told. Design choice: standing is shown in words, never a number ("Asked less than usual since August; your standing is being recalculated").

**3. Handlers see it first.** Desmond: "The Undertow: 1 ping this week, usually 12. 5 missed pings, 12–14 Aug. These count for less from 12 Nov." Kip sees Meteor Mite quiet while The Gale is overloaded.

**4. Release day is visible, not silent.** People are told before anything changes. The Undertow sees: "Since August you've been asked less. We're changing how missed pings count, and you may be asked more as your standing recovers." Support replies to each of the 45 tickets individually.
*Your decision: recalculate or reset.* **Recommend recalculating:**
- Marcus exports the current scores by 6 Nov.
- Ravi replays the pings table under the new rules and checks it against August by 6 Nov.
- This keeps the evidence, and the replay tests whether the four move back up.

A reset is faster but erases the evidence. Wen confirms by 30 Oct whether a restart already resets scores.

**Phases.** *12 Nov:* items 1–4 (lighter miss, fade, handler warning, release messages). *Phase 2* (Marcus sets the date by 30 Oct): "received" and "opened" signals, no penalty if a ping wasn't delivered, extra time once opened. Supply must be told before the availability record's format changes. Proximity keeps its 4.2 weight: not a revert.

## How we'll know (10 Dec, Phase 1)
- No available responder (not marked unavailable) goes more than 7 days without a ping.
- The four are back to at least 75% of their pre-4.2 jobs.
- Callouts where nobody came are back to 4–12 a week; after 4.2 it was 14–17.
- No new "gone quiet" tickets per week by week 4.
- *Phase 2 review:* missed pings under 5% (2.3% before 4.2, 18% now).
- *To watch:* The Gale's load, 21 pings a week against a usual 13.

**Who:** Wen Li decides the fade rule · Marcus Oyelaran builds · Sofia Marino designs · Ravi Menon measures · Nadia Hoffmann replies · Helen Achebe decides recalculate or reset.
**Open:** why the four missed more (delivery receipts); whether to cap workload.
*Separately: Helen to decide whether this replaces Availability Confidence in Q3.*
