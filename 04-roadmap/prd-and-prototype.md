# PRD & Prototype Sprint

> **Module 4 · Lab 2.** Repo file `04-roadmap/prd-and-prototype.md` — part of your submission.
> It deepens the top feature from your `roadmap-prd-prototype.md` and feeds the **Roadmap, PRD & Prototype** slide of your Module 6 deck.

## Responses

- **The "Now" feature I'm scoping (name + one-line core description):** Spotlight Curated Rail — hand-picked homepage rail that bypasses the algorithm.

- **My finalized Must-Haves (after overriding the AI):**
  - Rail on the home screen, above the fold, capped at 5–7 titles
  - Title and thumbnail on every card
  - Curation input for editorial — CMS entry or spreadsheet, not bespoke tooling
  - A path from card to playback, reusing the existing title detail page if one exists rather than building a new one
  - Rail attribution on play events — a "played from rail" flag, so the six-week metric read can tell whether Spotlight caused the change
  - A first-run onboarding animation the first time a viewer sees the rail — reveals who chose the titles and how often they change, plays once, never blocks a tap, with a static fallback under reduced motion
  - A persistent subline under the rail heading, "Chosen weekly by our editors" — always rendered, so a viewer who misses the animation still sees that a human picked these

- **What I demoted from Must → Should/Won't, and why:** Curator's note on each card, Must → Should. Having context for the recommendation is great and makes discovery more fun. For an MVP, the discovery can work without it, just letting thumbnail and title speak for themselves.

- **One thing my PRD makes explicit that a vague brief would have missed:** The eligibility rule. A vague brief says "a hand-picked rail of great titles" — and that rail would cheerfully serve a viewer six films they had already seen, which is exactly the failure it exists to fix, since the metric counts *new*-title plays only. Making it explicit forced two decisions nobody writes down otherwise: what counts as eligible, and what the rail does when there aren't enough eligible titles to fill it.

- **Where the prototype revealed a gap in my PRD logic (what I updated):** Building it exposed that **a Must-have depended on a Should-have**. FR7 requires every play event to record `is_new_to_viewer` — but that value needs watch-history integration, which I had demoted to Should. As written, the Must list could not be satisfied by the Must list. I updated FR7 so `played_from_rail` is always recorded while `is_new_to_viewer` is written as `unavailable` when watch history is absent, never inferred — a defaulted value would silently inflate the primary metric.

  Three smaller gaps came out of the same build. "Fewer than 5 **eligible** titles" was the trigger for hiding the rail, but the PRD never defined *eligible*, so I added FR10. The Screens section listed a one-line synopsis that no functional requirement actually called for, so a strict build to the FRs would have shipped a detail page without one — added as FR9. And nothing said what the rail does after a viewer returns from playback; I specified that the played title stays, because removing it would shrink the rail below its own minimum.

- **My shareable prototype URL:** https://claude.ai/artifact/2GmsgAN6hgAKsFa1Q5qhxP

---

## The rapid validation loop — three iterations

The PRD was not written once and handed over. It changed three times, each time because building or reviewing the prototype exposed something the document had got wrong.

**Loop 1 — the build.** Prompting the first prototype from the PRD exposed that FR7 required `is_new_to_viewer` on every play, which needs watch-history integration that had been demoted to Should. A Must-have depended on a Should-have. Fixed by writing the field as `unavailable` rather than inferring it. Three smaller gaps came out of the same pass: *eligible* was undefined, the Screens section promised a synopsis no requirement called for, and nothing said what the rail does after playback.

**Loop 2 — attribution had nowhere to live.** Reviewing the launch plan showed the rail would ship with nothing telling a viewer a human chose it, because the curator byline is a Could-have. Added FR11 and FR12: a first-run onboarding introduction, with a reduced-motion fallback. Built into the prototype and republished.

**Loop 3 — a one-time introduction is not enough.** A viewer who misses or forgets the animation sees a rail indistinguishable from any algorithmic row. Added FR13: a persistent subline under the heading, "Chosen weekly by our editors." Built and republished again.

None of these would have surfaced from re-reading the document. Each needed something clickable to exist first.

## Full MoSCoW

The builder holds the Must list and one demotion. The complete scoping, for the record:

**MUST HAVE**
1. Rail on the home screen, above the fold, capped at 5–7 titles
2. Title and thumbnail on every card
3. Curation input for editorial — CMS entry or spreadsheet, not bespoke tooling
4. A path from card to playback, reusing the existing title detail page where one exists
5. Rail attribution on play events — a "played from rail" flag
6. First-run onboarding animation — one-time, non-blocking, reduced-motion fallback (added 2026-10-01)

**SHOULD HAVE** — curator's note on each card · exclude titles already watched, with backfill · rail-level impression and card-open counts · save for later

**COULD HAVE** — curator byline and taste descriptor · "New picks every Thursday" cadence label · dismiss a card · rail position A/B · Hidden Gem badge

**WON'T HAVE (NOW)** — multiple themed rails · expandable notes · personalisation per taste profile (A5, cut) · curator profiles and following (A7, Next) · AI-generated reasons (A2, Next) · mood or occasion entry (A4, cut) · filters or sort on the rail · offline, social, watch party

### Removal test applied

*If cutting it still lets a casual browser start something new within two minutes without the choosing becoming the evening, it is not a Must.*

### Demotions in full

Three items came off the Must list:

| Item | Move | Reason |
|---|---|---|
| Curator's note on each card | Must → Should | Context makes discovery more fun, but for an MVP discovery works without it — thumbnail and title can speak for themselves. |
| Exclude titles already watched, with backfill | Must → Should | With five to seven titles changing every week, the chance a viewer has already seen all of them is small, so the MVP holds up without it. It is still a feature we need — it is what `is_new_to_viewer` depends on — but if engineering capacity is tight it can wait. The condition is that editorial does not pick titles most people have already watched. That is a selection rule, and it gets most of the benefit for none of the build cost. |
| Rail-level impression and card-open counts | Must → Should | Play events already exist, so only rail attribution is genuinely new. The "played from rail" flag stayed in Must to protect the six-week metric read; the richer counts can follow. |

Four moved Should → Could: curator byline, cadence label, dismiss, rail position A/B. Two moved Could → Won't: multiple themed rails and expandable notes — both add breadth to a feature whose entire argument is subtraction.

One promotion: save for later, Could → Should. One addition: title and thumbnail on every card, which the AI list left implicit.

