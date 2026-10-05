# Decisions & open questions

Running log. Anything here that resolves gets applied to the deliverable files, not just recorded.

---

## RESOLVED · 2026-09-24 · Persona is Casual Browsers

Was: the Module 1 hook targeted "our most valuable viewers", which maps to Power Users. Spotlight's measured churn effect on that segment is **N/A (low churn anyway)** — the initiative was aimed at the one segment showing no response.

**Decision:** pivot to Casual Browsers. You cannot win back a segment that is not leaving. Power users stay regardless and already consume 58% curated; casual browsers are the largest revenue pool, are measurably churnable, and have somewhere to go.

### Segment data behind it

| Segment | % base | Monthly LTV | Sessions/wk | Curated / Trending | Churn if Spotlight-exposed |
|---|---|---|---|---|---|
| Power Users | 22% | $14.20 | 4.8 | 58% / 22% | N/A (low churn anyway) |
| Casual Browsers | 37% | $11.40 | 2.3 | 31% / 44% | −14 pts vs non-exposed |
| Wanderers | 41% | $8.40 | 1.1 | 18% / 61% | −22 pts vs non-exposed ✓ |

Per 1,000 subscribers — revenue today: Casuals ~$4,220, Wanderers ~$3,440, Power ~$3,120. Spotlight-retained revenue: Wanderers ~$758/mo, Casuals ~$590/mo (~$7,100/yr), Power none measurable.

### Why not Wanderers, despite the ✓ — revised 2026-10-03

The snapshot's critical signal flags Wanderers explicitly and ticks that row. On raw retained revenue they win: roughly $758 a month per 1,000 subscribers against $590. We are deliberately not following it, and the reason is a strategic judgement the churn delta cannot express.

**Prevention beats recovery on a decay path.** The three segments are one gradient, not three populations: LTV falls $14.20 → $11.40 → $8.40, about $3 a step, with sessions falling 4.8 → 2.3 → 1.1 alongside. Casual browsers are mid-decay; Wanderers are late-decay. A −22 point improvement among Wanderers measures a problem already suffered — those subscribers have lost $5.80 of monthly value getting there. Preserving a casual browser protects $11.40 *and* prevents the $3.00 fall, so they never enter the Wanderer bucket at a lower value at all.

**The competitive situation makes this the stronger play.** The brief describes specialists gaining ground on discovery. They do not take viewers who still open the app two or three times a week — they take the ones who have stopped expecting anything from it. A casual browser is contestable. A Wanderer at 1.1 sessions has largely gone, and the M1 value proposition already says win-back costs more than retention.

**The cost:** about $168 a month per 1,000 subscribers in measured retained revenue, traded for a prevention benefit we cannot size, because nothing in the data gives a casual-to-wanderer decay rate.

**Two earlier arguments withdrawn**, both refuted by the snapshot images:
- "Wanderers can't be reached by a home-screen rail because they rarely open the app" — the −22 points is *measured* from exposed Wanderers. They are reached and they respond.
- "Wanderers have no headroom" — backwards. They sit $3.00 below casual browsers and $5.80 below power users. A longer ladder, not an absent one.

**Standing answer if challenged:** Spotlight is a surface in the app, not a targeted campaign. Wanderers get it too and are measured separately. The persona sets who the design is optimised for, not who has access. Optimising for the segment with the largest churn delta means helping the group that has already lost the most, which is not the same as doing the most good.

### Applied

- `01-product-thinking/problem-hook.md` — rewritten 2026-09-24.
- `02-discovery/competitive-and-journey.md` — redone as M2 Lab 2, all three steps, 2026-09-24.
- `02-discovery/journey-map.html` + `journey-map.md` — built 2026-09-24. Kept as a deliberate pair; both must be updated together.
- `03-analytics/hypothesis-and-metrics.md` — rewritten 2026-09-24.

---

## RESOLVED · 2026-09-24 · Spotlight curates for accessibility, films and series

The scenario brief describes Spotlight as "a premium space within the app dedicated to curated cinema." We are deliberately departing from that on two counts:

1. **Accessibility over connoisseurship.** The promise is a confident, well-reasoned pick for tonight, not a cinephile syllabus.
2. **Films and series both.** Cinema-only excludes the behaviour the research actually shows — UXR-03's four comfort *shows* are series, and series are what this persona already falls back on.

**Why:** the persona and the product have to match. A viewer who re-watches four comfort shows is not the audience for curated cinema. Holding the brief's framing would have meant building a premium film space for an audience that does not want one.

**The cost, acknowledged:** this removes the sharp edge the specialist services have. "Good things, explained" is a weaker differentiator than curated cinema. The defence is attributable curators with followable taste — a named person whose picks you can follow is not something a better home screen provides. Carried as sharpen item 2 in `problem-hook.md`; still needs one clean sentence.

---

## RESOLVED · 2026-10-03 · A11 "Play Something" added to the backlog, held for Later

**How it came up:** adding touchpoints to the M2 journey map exposed that **Give up is the only stage with no touchpoint at all**. At the moment the viewer most needs the product, nothing is there to meet them. The question followed naturally — should a feature address that gap directly, or is preventing it enough?

**Decision:** prevention stays the primary strategy, and the intercept is recorded rather than built. A11 is a one-title, one-tap offer when a session passes the give-up threshold — UXR-12's "just tell me what's good tonight" taken literally, and the Netflix "Play Something" archetype from the M1 material.

**Why Later despite a Quick Win score (V4/E2):**
- Re-serving the same curated picks in an interruption fixes nothing; the viewer already scrolled past them. A11 only earns its place as a *different* bet from curation, which makes it a second experiment rather than a second feature in this one.
- Running it alongside A1 confounds the six-week read.
- The read answers whether it is needed. If new-title play rate moves, prevention was sufficient; if it does not, an intercept carrying the same content would not have rescued it.

**Also applied:** the future-state journey map now carries an **unhappy path** — a viewer can meet Spotlight, scroll past it, and reach the same give-up point. The experience gap is moved, not closed. The map previously ended on a guaranteed success, which was not honest.

Added via the M4 lab's blank backlog row, which exists for a feature discovered in M2 or M3.

---

## OPEN · The biggest risk in the case: avoidance is not appetite

UXR-03 — *"Discovering anything new feels like a chore, so I don't"* — is someone opting out, not someone asking to be guided. The clearest demand signals for curation (UXR-09, UXR-12) both come from older participants, so the appetite may not generalise across the casual segment.

The entire initiative rests on casual browsers *using* a curated surface rather than merely having abandoned the current one. Nothing in the research proves that yet.

**Where it should land:** this is the assumption an experiment should test first — see `05-experimentation/experimentation-plan.md` when M5 starts.

---

## FINDING · 2026-09-24 · A failed decision has two exits, not one

The friction was written as though giving up always ends in a re-watch. It does not. UXR-03 re-watches; UXR-01 closes the app with nothing played and goes back to a DVD; UXR-08 "gave up and opened YouTube." Leaving entirely is the second exit, and it is the more expensive one — it is literally the mechanism by which a casual browser becomes a wanderer at 1.1 sessions a week and $8.40 per head.

**It broke the metric, not just the wording.** New-title play rate was defined as a share of "sessions ending in a play." An abandoned session ends in no play, so it fell out of the denominator — the failure mode the metric exists to detect would have been invisible to it. Corrected: the denominator is now **every session opened**. Defined that way one number catches both exits — a re-watch lands in the denominator but not the numerator, and so does walking away.

**Applied:** `hypothesis-and-metrics.md` (friction, metric definition, reading version), `competitive-and-journey.md` (Step 1 friction, Step 2 process), `journey-map.html` and `journey-map.md` (both show the branch). **Not applied:** the M3 Hypothesis Builder's verbatim export block still carries the single-exit phrasing — re-open the builder and re-export if you want them to agree.

---

## RESOLVED · 2026-10-01 · Attribution ships as a first-run onboarding animation, inside the feature

**How it came up:** the M6 GTM plan proposed an in-app introduction card as its first channel. That was a scope addition arriving through the back door — it appeared in a launch plan, not in the M4 PRD, and it created two problems at once. M5's variant definition described a rail with no such card, so the two documents described different products. And a launch communication cannot be targeted to one experiment arm, so it would have had to wait until after the week-6 read, leaving the rail unexplained for the whole test.

**Decision:** the attribution becomes part of the product — a first-run onboarding animation, added as a Must-have. The first time a viewer sees the rail, it reveals who chose the titles and how often they change. One-time, non-blocking, with a static fallback under reduced motion.

**Why it had to be product rather than comms:** the curator byline is a Could-have, so without this the rail carries nothing saying a human chose it — and a hand-picked rail that looks identical to a well-tuned algorithmic row is not testing what it claims to test. A product that has to be explained by marketing has a design problem.

**Applied to:** `prd-spotlight-rail.md` (FR11, FR12, three smart behaviours, decision log entry 3, Screen 1), `prd-and-prototype.md` (Must list), `prototype-spotlight-rail.html` (built and republished, with a replay control), `experimentation-plan.md` (variant definition, and the stated limitation grows from two mechanisms to three), `gtm-and-dashboard.md` (no longer a channel; tier justification now rests on the second exit alone).

**Knock-on:** the GTM channel set became Digest Email, app-store listing, and curator editorial — all Phase 3, because none can be targeted by arm. That produced the general rule now stated in the plan: *any channel that cannot be targeted by experiment arm cannot run during the test.* It also moved app-store submission out of Phase 1, where it would have shown control-arm subscribers screenshots of a feature they do not have.

---

## OPEN · 2026-09-29 · A1 and A6 cannot both ship inside the test window

The M5 isolation check surfaced a conflict with the M4 roadmap. **A1 Spotlight Curated Rail** and **A6 Spotlight Digest Email** are both in the Now lane, same three-week sprint. The experiment randomises on A1 alone. If A6 ships mid-test, the two Now features confound each other and neither result is attributable.

**Options:** withhold A6 until the week-6 read (cleaner, and it protects the only causal read we get), or run A6 identically across both arms (keeps the sprint intact, but means A6 gets no read of its own).

**Recommendation:** withhold. A6 was chosen precisely because it reaches the second exit — the viewer who stopped opening the app — which is a different mechanism from the rail. Running it un-measured wastes that.

**Consequence if withheld:** the Now lane still ships both in sprint 1, but A6 stays dark until week 6. Worth stating in the roadmap so it doesn't read as a slip.

Also recorded: rail-originated plays must be excluded from recommender training for the test duration, or arm B's "Because you watched" row diverges from arm A's and the arms stop differing by one change.

---

## FINDING · The "low churn anyway" figure is survivorship-biased

UXR-04 is a lapsed subscriber who left for a competitor's hand-picked weekly selection — high-intent, already churned, therefore no longer in the base being measured. "Low churn anyway" describes the viewers who stayed, after the defectors had gone.

Less central now that the persona has moved, but still the right answer if anyone argues Power Users should have been the target.

---

## FINDING · The curated-mix column cannot prove who sourced a play

The mix column records *what* was watched, never *where the decision was made*. A subscriber who picks a title elsewhere, opens StreamLine, searches for it and plays it produces a curated-play event identical to one Spotlight sourced.

**Consequence for M3 — applied 2026-09-24.** The 14-point churn delta became the north-star. In-app-originated play share was not demoted but **dropped entirely**: it described the previous persona's failure (discovering on Reddit, arriving with a title). Casual browsers are not discovering elsewhere — they are not discovering at all — so **new-title play rate** replaced it as the leading indicator. Both churn and prior-viewing history are already instrumented, which removes the tracking dependency that was the weakest part of the earlier hypothesis.

---

## CLOSED · M1 self-review action 1 — "get a real clock"

The why-now had no evidence behind it. Now carried by the 14-point churn delta and roughly $7,100 per 1,000 subscribers per year in retained revenue, plus the decay argument: every quarter of delay moves more casuals into wanderer behaviour at $8.40 per head, where win-back costs more than retention.

---

## Related

Live synthesis doc: https://claude.ai/code/artifact/cc8c02c1-6609-4b42-b4de-45861a1963ae
