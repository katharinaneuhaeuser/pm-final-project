# Experimentation Plan

- **Module 5 · ★ Deliverable 5** · Scenario: StreamLine Spotlight (B2C)
- Becomes the **Experimentation Plan** slide. Tests A1, specified in [`prd-spotlight-rail.md`](../04-roadmap/prd-spotlight-rail.md)

## Overview

A 6-week, 50/50 user-randomised A/B test of the Spotlight Curated Rail against the current home screen, run on casual browsers only.

**The question changed, because the data answered the old one.** We had planned to test whether casual browsers would use a curated selection at all. The Module 3 cohort data settles it: Spotlight has been running since the December cohort, those groups stay 12–15 points better at Month 1, and the gap is still growing. It works for the people who find it.

**Only 18% find it.** That is what this test is for. The question is no longer whether curation keeps people watching. It is whether putting those picks at the top of the home screen reaches the other 82%, and whether reaching them turns into longer sessions.

The primary read is **sessions reaching 30+ minutes** at six weeks, against a measured baseline of 11% (down from 19%). Retention is observed to 90 days as a follow-on. The test is deliberately scoped to hand-picking alone — curator notes are a Should-have, not a Must — so it measures the surface, not the surface plus explanation.

## What you're testing

Short form — this is the M6 deck slide. Full reasoning for every row is in the sections below.

| Parameter | Decision |
|---|---|
| Feature under test | Spotlight: a hand-picked rail of 5–7 films and series pinned to the top of the home screen, chosen by editors rather than the algorithm |
| Persona | The Resigned Browser: a casual viewer who opens the app two or three times a week with no title in mind and settles for whatever is trending |
| Expected outcome | More casual browsers start a title they haven't seen, instead of re-watching a known one or leaving with nothing played |
| Primary success metric | % of casual browsers with **at least one 30+ minute session per week** — the case's own critical signal, measured per user to match the randomisation unit |
| Baseline rate | **11%**, down from 19% six months ago — measured, from the Module 3 funnel |
| Initiative signal | Spotlight reach — share of sessions that open the curated selection. Baseline **18%**, target 35% |
| Guardrail metric | Total weekly plays per casual-browser subscriber — not more than 5% below control; investigate at 3% |
| Guardrail boundary | Must not fall more than 5% below control. Investigate at 3% |
| Second guardrail | **Month-1 retention**, arm B vs arm A — must not fall more than 2 points below control. Equivalently: churn must not rise more than 2 points |
| Discovery indicator | New-title play rate, arm B vs arm A — distinguishes "the rail worked" from "people re-watched for longer" |
| **Retention indicator** | **Month-1 retention**, exposed vs control. Baseline ~79% (latest Spotlight cohort). Directional, not a gate — the test window barely covers one month |
| **Confirming metric** | **90-day churn**, exposed vs non-exposed. Prior: −14 pts for casual browsers. Read in Phase 3, after the ship decision |
| Minimum Detectable Effect | **+3 percentage points** (11% → 14%), recovering about a third of the 8-point decline. Below that the rail does not justify the ongoing editorial operation |
| Sample size per arm | **≈1,900 per arm** (≈3,800 total): baseline 11%, MDE 3 pts, power 80%, significance 5%. At a 2-point MDE it rises to ≈4,100 |
| Traffic split | 50/50 — casual browsers are 37% of the base, so an even split fills both arms well inside the window |
| Test duration | 6 weeks — at 2.3 sessions a week that's roughly 14 exposures per user; 14 days would give under 5 |
| Significance threshold | p < 0.05 (95%), two-sided — the rail could plausibly reduce new-title plays by narrowing choice, so the test must detect harm as well as benefit |

**Hypothesis, for the slide:** I believe that moving the already-proven Spotlight selection into the prime slot for the Resigned Browser will raise the share of casual browsers with at least one 30+ minute session a week from 11% to 14% within six weeks, while total weekly plays per subscriber does not fall.

**Decision rule, for the slide:** **Ship** at ≥ +3 pts with the confidence interval's lower bound also ≥ 3, p < 0.05, guardrails intact · **Iterate** if significant but the interval's floor falls below 3 pts · **Investigate** if the primary rises but a guardrail breaks or segments contradict · **Kill** if not significant or negative · Read date fixed at week 6.

## Get your documents ready

- **From M3, your hypothesis sentence:** Based on casual browsers taking 44% of their consumption from trending rows and only 31% from curated — at 2.3 sessions a week against 4.8 for power users — and on Spotlight-exposed casual browsers churning 14 points lower than non-exposed, I believe that closing the effort-versus-payoff gap in discovery for casual browsers will result in those viewers resuming discovery rather than cycling titles they have already seen or closing the app with nothing played.
- **From M3, your primary success metric & guardrail metric:** Primary: % of casual browsers with at least one 30+ minute session per week, baseline 11% (down from 19%). Initiative signal: Spotlight reach, baseline 18%. Guardrails: total weekly plays per casual-browser subscriber, not more than 5% below control; and Month-1 retention, not more than 2 points below control.
- **From M4, the feature you scoped in your PRD:** Spotlight Curated Rail — a hand-picked rail of 5–7 films and series at the top of the home screen, read from an editorial curation source, bypassing the recommendation engine.

## Why an A/B test, and what else is in play

Three filters decide the method: the question, the traffic, and the risk.

**The question is single-variable.** Does moving the curated selection into the prime slot raise reach and depth? One change, one comparison. That is an A/B test. Multivariate would be right if we were testing several things at once and expected them to interact — rail length, note style, placement. We are not, and it needs roughly ten times the traffic.

**The traffic is not a constraint.** An A/B test needs around 1,000 users; we need about 1,900 per arm and casual browsers are 37% of the base.

**The risk is low but not zero.** The rail displaces every existing row by one position for half the casual-browser population. That is a visible change to the home screen, which is why the guardrail on total weekly plays exists.

**All three methods are in use, not just one.** The module's framing applies directly here:

- A **feature flag** controls exposure. It assigns the 50/50 split, and it is what makes the staged rollout in the GTM plan possible — 50% during the test, 100% at the launch moment, with instant rollback if the guardrail breaks.
- The **A/B test** measures whether it works.
- A **canary** protects everyone else: the rail goes to a small percentage first to catch rendering or performance problems on older TV hardware, where BUG-1042 and BUG-1110 already show the estate is fragile, before the arms are populated.

## Define your experiment parameters

- **Feature under test:** Spotlight Curated Rail. First row on the home screen, above any algorithmic row; 5–7 titles; thumbnail and full title on every card; contents read from a single editorial curation source with no ranking or personalisation; card opens the existing title detail screen; every play records `played_from_rail`.
- **Persona:** Casual browsers — "The Resigned Browser." 37% of the base, $11.40 monthly LTV, 2.3 sessions per week, 31% curated against 44% trending consumption. Opens the app with no title in mind and settles for whatever is trending.
- **Expected outcome:** Casual browsers resume discovery — starting titles they have not seen, instead of cycling known titles or closing the app with nothing played.
- **Primary success metric:** **% of casual browsers with at least one 30+ minute session per week.** A strategic metric by the module's test — time-bound, and it proves the evening actually happened rather than that someone clicked. A session abandoned at the point of misery never reaches it, so both exits from a failed decision count as failures without needing a separate rule.

  **Measured per user, because that is the unit we randomise on.** Counting sessions would mismatch the two: sessions belonging to one person are correlated, and the sample-size maths assumes independent observations, so the effective sample would be smaller than a session count implies. One user, one observation, removes the problem. It also matches the case's own reporting — the funnel header reads "% of homepage *visitors* who reach each stage", so the 11% was visitor-level all along.
- **Baseline rate:** 18% — assumed, not measured. The case data gives content mix, never repeat-versus-new, so no measured baseline exists. Reasoned from the two documented failure modes at 2.3 sessions per week. To be confirmed in weeks 1–2; MDE, sample size and duration all recalculate if it moves.
- **Guardrail metric & boundary:** Total weekly plays per casual-browser subscriber. Investigate at −3% against control; halt the test at −5%. Spotlight narrows choice deliberately, so suppressed consumption is a failure rather than a trade-off.
- **Second guardrail:** **Month-1 retention**, arm B against arm A. Must not fall more than **2 points below control**. This catches a harm the first guardrail cannot see: the rail could raise session depth while making people less likely to come back — by displacing familiar rows enough to irritate them, or by satisfying them so completely in one sitting that they do not return. Depth bought with retention is not a win, and retention is what the whole initiative is for.

  Baselined at **~79%**, the latest Spotlight cohort, not the Full-Library 63%. Spotlight exists in both arms, so this measures better reach against buried reach.

  **Requires simultaneous enrolment.** The full cohort joins at week 0 rather than on a rolling basis, so every subscriber reaches their Month-1 mark by week 4 and the guardrail is readable on the whole sample inside the window.
- **Secondary metric (not a gate):** Median time from session start to playback start. The persona's own standard is "a couple of minutes." Carried from the PRD's Eval 1 target of under 120 seconds. Reported at the read, does not block shipping.
- **Discovery indicator (not a gate):** New-title play rate, arm B against arm A. Distinguishes "the rail worked" from "people re-watched for longer" — a 30-minute session spent on a known comfort title is depth without discovery. No historical baseline exists, because the case data reports content type and never novelty, but none is needed: the control arm supplies it and the between-arm difference is the answer.

- **Retention indicator (not a gate):** **Month-1 retention**, exposed against control. The cohort heatmap makes this the most comparable number in the case — it is where the pilot shows its 12–15 point effect, and where the snapshot identifies the single largest leak regardless of cohort type. Baseline is the latest Spotlight cohort at **79%**, not the Full-Library 63%: Spotlight already exists in both arms, so this test measures better reach against buried reach, not Spotlight against nothing. Expect a smaller movement than the pilot's for that reason.

  *Window caveat:* six weeks is about 1.4 months, so only subscribers enrolled in week 1 reach their Month-1 mark inside the test. Measured on that first enrolment cohort alone, read at week 6, and reported directionally rather than gated.

- **Confirming metric (Phase 3):** **90-day churn**, exposed against non-exposed, with a prior of **−14 points** for casual browsers from the segment data. This is the business outcome the initiative is funded to move, and it lands after the ship decision rather than informing it. If the rail works only through novelty, this is where that shows.

**Retired from the previous draft:** the early-abandon guardrail. It existed to catch starts that never became watching, which a 30-minute threshold now catches by construction.
- **Minimum Detectable Effect (MDE):** **+3 percentage points** (11% → 14%, roughly +27% relative). Set against the measured decline rather than against a guess: the business lost 8 points over six months, and recovering about a third of that is the smallest result worth committing a permanent editorial operation to.
- **Sample size per arm:** **1,907 users per arm** at an 11% baseline and 3-point MDE, 80% power, p<0.05 — confirmed against the builder's calculator. At a 2-point MDE it rises to roughly 4,100. Randomisation unit and measurement unit are both the user, so no clustering adjustment is needed. Around 3,800 casual browsers in total, drawn from 37% of the base: recruitment is not remotely the constraint, so the 6-week duration is set by weekly behaviour cycles rather than by filling the arms.

  The requirement is also robust to the blended baseline. If casual browsers sit below the 11% mobile-base figure, variance falls and the sample needed drops — around 1,500 at an 8% baseline. If they sit above it, around 2,400 at 15%. 1,907 covers the plausible range.
- **Traffic split & test duration:** 50/50, user-level. 6 weeks — three full weekly cycles plus buffer, matching the M3 leading-indicator gate. Churn observed to 90 days as a follow-on read, not as the ship decision.
- **Significance threshold:** p < 0.05, two-sided. Two-sided because a curated rail could plausibly reduce new-title plays by narrowing choice — the test must be able to detect harm, not only benefit.

### The baseline, and the one assumption left in it

The baseline is measured, not invented: **11% of sessions reach 30+ minutes**, down from 19% six months ago, straight from the Module 3 funnel. That removes what had been this brief's largest weakness.

One assumption remains. The 11% is reported for the whole mobile user base, not for casual browsers specifically. Casual browsers open 2.3 times a week against 4.8 for power users, so their rate is plausibly lower than the blended figure — which would make the sample requirement slightly larger and the target slightly easier to hit.

It is used here as the base rate, and the first thing the week-2 look does is cut it by segment. If the casual-browser figure lands materially below 11%, the brief is re-issued with a corrected sample before any result is read.

## Define your control and variant

- **Control (A):** The home screen as it stands. Trending rows first; "Because you watched" answering a single viewing with near-duplicate franchise titles (BUG-1091); no curated surface anywhere. This is the experience that produces the documented moment of misery — the viewer opens with no title in mind, scrolls, and takes one of two exits: a re-watch from a handful of known titles (UXR-03), or closing the app with nothing played (UXR-01, UXR-08).
- **Variant (B):** Identical to control in every respect, with the Spotlight rail inserted as the first row above all algorithmic rows. Rail renders above the fold; 5–7 titles, never fewer or more, hiding entirely below 5 eligible titles rather than rendering short; every card shows thumbnail and complete title; contents read from a single editorial curation source with no ranking, personalisation or reordering; card opens the existing title detail screen with one primary Play action; every play records `played_from_rail` and, where watch history is available, `is_new_to_viewer`. A persistent subline under the rail heading reads "Chosen weekly by our editors." On a viewer's first exposure, a one-time onboarding animation emphasises that subline and brings the cards in — non-blocking, never repeating, with a static fallback under reduced motion. No curator notes in either arm — they are a Should-have, so this tests hand-picking alone.
- **Isolation check, what has NOT changed?** Identical across both arms: app version and release train, the recommendation engine and its ranking, all other home-screen rows and their order beneath the rail, search, notifications and push, onboarding, pricing and paywall, playback and resume behaviour, catalogue contents, email programmes.

  Two contamination risks requiring active control. First, rail-originated plays must be excluded from recommender training for the duration — otherwise arm B's "Because you watched" row diverges from arm A's over six weeks and the arms stop differing by one change. Second, the Spotlight Digest Email (A6) is in the same Now sprint; if it ships mid-test the two features confound each other and neither result is attributable, so it must be withheld until the read date or run identically in both arms.

### Stated limitation: the variant is one feature, but three mechanisms

The rail adds hand-picked content, **takes the prime slot** — demoting every existing row including Trending by one position in arm B — and **declares its own authorship** through the first-run onboarding animation. A positive result cannot separate "human curation works" from "anything in the top slot outperforms Trending" from "telling people a person chose it is what changed their mind."

None of the three is removable without testing a different product from the one that would ship. Above-the-fold is a Must, so placement is part of the treatment by intent. The onboarding animation is what carries attribution at all, since the curator byline is a Could-have — strip it and the rail is visually indistinguishable from a well-tuned algorithmic row, which is not the thing under test.

The unit under test is therefore **a curated rail in the prime slot that says who curated it**. Stated here deliberately: a reviewer who finds this unaided treats the whole result as unattributable, where a reviewer who reads it here can weigh it. Separating the three would need a four-arm design this sprint cannot fund.

### Accepted: novelty effect is not controlled for

The obvious control would be to discount weeks 1–2 and read only weeks 3–6. It was considered and rejected, for two reasons. The read date is fixed at week 6 precisely so nobody reads results early, and carving the window into periods reintroduces the interim look by another name. More importantly it would not work: novelty is per-user-exposure, not per-calendar-week, so an infrequent viewer who first opens the app in week 4 is still inside their own novelty window no matter which calendar slice is analysed.

The position taken is that the feature should survive its own novelty. Six weeks at 2.3 sessions a week gives roughly fourteen exposures per user, well past the point where a genuine effect and an attention effect look the same — and the 90-day churn follow-on is the real durability check. If the rail only works because it is new, churn at 90 days will say so.

## One primary metric, four supporting measures

The brief names five numbers. Only one of them gates the decision.

**Primary:** sessions reaching 30+ minutes. This is the only metric the ship criterion tests, so there is no multiple-comparison problem and no correction is needed.

**Supporting:** Spotlight reach, new-title play rate, Month-1 retention and 90-day churn are read for understanding, not for deciding. They tell us *why* the primary moved — whether reach rose, whether the depth came from discovery or from longer re-watching, and whether it held into the next month.

**Guardrails:** total weekly plays and Month-1 retention can trigger Investigate, which is a different job from defining success.

Stating this matters because five numbers in a brief usually signals a test fishing for anything that moves. Here the bar was set on one metric before launch and does not move.

## Segment analysis — planned before the read

The cuts are decided now, not after the numbers arrive, so a disappointing headline cannot be rescued by hunting for a segment that worked.

| Cut | Why |
|---|---|
| **Device** — TV vs mobile vs tablet | The most likely place for a contradiction. A rail navigated by TV remote behaves differently from one scrolled by thumb, and the bug data shows the TV estate is already fragile (BUG-1042, BUG-1110). If the headline hides anything, this is where it will be: a lift on mobile covering a fall on TV. |
| **Tenure** — under 3 months vs over | The cohort data names Month 0 → 1 as the largest leak regardless of cohort type. New subscribers may respond differently from established ones, and they are the group the retention argument depends on. |
| **Spillover** — Power Users and Wanderers | The rail ships to everyone, not only to casual browsers. We need to know it does not harm Power Users, who already consume 58% curated and have the most value to lose. |

A contradiction in any of these moves the result to **Investigate**, whatever the headline says.

## Formalize your hypothesis & shipping criteria

**Your hypothesis:** I believe that moving the already-proven Spotlight selection into the prime slot, for casual browsers — the 37% of subscribers who open StreamLine two or three times a week with no title in mind — will result in more of them committing to a title and staying with it, as measured by a **+3 percentage point (11% → 14%) change in the share of casual browsers with at least one 30+ minute session per week**, within 6 weeks. We will protect total weekly plays per casual-browser subscriber throughout the test.

**Your shipping criteria:**

> We will **SHIP** if the share of casual browsers with at least one 30+ minute session per week improves by **≥ 3 percentage points at p < 0.05, two-sided**, **with the lower bound of the 95% confidence interval also at or above 3 points**, **and** total weekly plays per casual-browser subscriber is not more than **5% below control**, **and** Month-1 retention is not more than **2 points below control**.
>
> We will **ITERATE** if the lift is **significant but the confidence interval's lower bound falls below 3 points** — a result of +3.2 points with an interval of [0.1, 6.3] is real, but the data supports an effect too small to be worth a permanent editorial operation. Also iterate if the point estimate itself lands below 3 points while staying significant. In both cases the first iteration is the curator's note, the Should-have this test deliberately excluded: a small but real lift suggests the selection is right and the reason to watch is missing.
>
> We will **INVESTIGATE** if the primary metric improves but **a guardrail breaks**, or if **segments contradict each other** — for example, 30-minute sessions rising overall while falling on TV. A broken guardrail alongside a real lift means the feature works for one group and harms another. Find out which before deciding. We cut by device, tenure and segment, then decide.
>
> We will **KILL** if the lift is **not significant**, or is **negative**. A positive but non-significant result counts as a kill, because the test was powered to detect the floor we set — failing to clear it means the effect is below that floor. It would tell us the prime slot is not what keeps the other 82% away, and the reach problem is somewhere we have not looked.
>
> The read date is fixed at the end of **week 6**. One pre-registered look at week 2, on the control arm only, to cut the 11% baseline by segment — no efficacy read, no stopping. If the casual-browser figure diverges materially from the blended rate, the brief is re-issued with a corrected sample before any result is read.

**Hardest parameter to define, and did it change your hypothesis?** The success metric itself — and yes, it changed the hypothesis twice over.

The first draft of this brief measured new-title play rate against an 18% baseline I had reasoned out rather than found, because the segmentation snapshot gives content mix and never repeat-versus-new. Reading the funnel snapshot later made two things obvious. The case names its own critical signal — sessions reaching 30+ minutes, 11%, down 8 points — and it comes with a measured baseline. And the 18% I had reasoned to was, coincidentally, the number in the data for something else entirely: Spotlight's reach.

Switching to 30+ minute sessions changed the whole shape. The metric became strategic rather than diagnostic — it proves the evening happened, not that someone clicked. The MDE could be set against a real decline rather than against a guess at what curation costs. The sample requirement fell from 6,039 per arm to roughly 1,900, because a lower baseline carries lower variance. And the early-abandon guardrail became unnecessary, since a session someone bails on never reaches thirty minutes.

The lesson is less about metrics than about reading all the data before committing to one. Two of three snapshots went unread for a fortnight, and both of them changed the answer.

## Why this brief is shippable — and where it isn't

The variant is a single feature. The primary metric measures both exits from the moment of misery, because its denominator is every session opened rather than every session that ended in a play. The two guardrails catch genuinely different harms — suppressed volume, and starts that never become watching. Every threshold was committed before launch, and the decision rule distinguishes a significant small lift from noise. A stakeholder could hold the PM to it.

Two things a reviewer should know before trusting it, both stated in full above rather than buried:

**The baseline is blended, not segment-specific.** 11% is measured, but it is reported for the whole mobile base. Casual browsers open less often, so their rate may sit below it. The week-2 look cuts it by segment, and the sample requirement stays provisional until it does.

**One feature, three mechanisms.** The rail moves curated content into the prime slot and declares its own authorship. A positive result cannot separate "the curation is good" from "anything above Trending gets used" from "telling people a person chose it is what changed their mind." Separating them needs a four-arm design this sprint cannot fund — and the first of the three is, in fairness, already evidenced by the pilot.

## Findings & decision _(after running it)_

_Not yet run._

