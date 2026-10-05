# Data-Backed Hypothesis, Module 3

- **Scenario:** StreamLine Spotlight (B2C)
- **Bet type:** Optimizing the existing — Spotlight is a live pilot; the rail is how people reach it

## What Spotlight is, and what we are building

The data distinguishes two things the project had been treating as one.

**Spotlight** is the curated space itself — the area of the app the brief describes. It launched for the December cohort and reaches **18%** of visitors. It works: the people who get it stay 12–15 points better at Month 1.

**The Spotlight Curated Rail** is what we are building — a row at the top of the home screen that puts those picks in front of people, instead of leaving them somewhere you have to go and find.

That difference is the whole bet. We are not asking anyone to believe that curation keeps people watching; the pilot already showed it does. We are saying something that works is only reaching 18% of people, and we know where to put it.

*Interpretation note: the case does not state the relationship outright. It is inferred from the cohort table contrasting "Spotlight" with "Full Library" — an offering contrast rather than a feature toggle — and from the brief describing Spotlight as "a premium space within the app." A space you navigate to explains an 18% reach that a home-screen rail would not.*

## Short form — the M6 deck slide

| Parameter | Decision |
|---|---|
| Problem | Spotlight retains the people who use it, and 82% of visitors never do |
| Persona | Casual browsers, "The Resigned Browser" — 37% of base, 2.3 sessions/wk |
| Primary success metric | % of casual browsers with **at least one 30+ minute session per week** |
| Baseline | **11%**, down from 19% six months ago |
| Target / MDE | **+3 pts** (11% → 14%), recovering about a third of the lost ground |
| Initiative signal | Spotlight reach — share of sessions that open the curated selection. **18% → 35%** |
| Discovery indicator | New-title play rate — proves depth came from discovery, not longer re-watching |
| Guardrail | Total weekly plays per casual-browser subscriber — not more than 5% below control |
| Second guardrail | Month-1 retention, arm B vs arm A — not more than 2 pts below control |
| Confirming metric | 90-day churn, exposed vs non-exposed — prior −14 pts, read in Phase 3 |
| Decision window | 6 weeks on the leading indicators; 90-day churn read before scaling |

**Hypothesis, for the slide:** Based on an 18% Spotlight reach alongside pilot cohorts retaining 12–15 points better at Month 1, I believe that moving the curated rail into the prime slot for casual browsers will raise the share with at least one 30+ minute session a week from 11% to 14% within six weeks, while total weekly plays per subscriber does not fall.

---

## Pre-work — the qualitative baseline

What we believed before looking at any numbers, carried from Modules 1 and 2. The reconciliation below checks each snapshot against it.

| | |
|---|---|
| **Role** | Casual browsers, "The Resigned Browser" — the 37% who open StreamLine two or three times a week with no title in mind |
| **Goal** | Start watching something decent within a couple of minutes, without the choosing becoming the evening |
| **Friction** | Discovery costs more than the evening is worth, so they abandon the search — falling back to a title already seen, or closing the app with nothing played |
| **Workaround** | Memory: a shortlist of four known titles, used instead of the product's discovery. Some leave for a second screen |
| **Problem hook** | We're spending blockbuster money on a library only our most committed viewers can use, while the 37% who open with no title in mind pay for it in scrolling and leave having watched nothing |
| **Value proposition** | Bring Spotlight to the home screen: a small, human-picked selection in place of the infinite scroll |

Note that this baseline is itself post-pivot. The original version named high-intent viewers who discovered on Reddit and Letterboxd. Snapshot 3 refused that premise, and the table above is what replaced it.

## The reconciliation — three snapshots against the M2 findings

### Snapshot 1 · Funnel and engagement health

| Stage | % of homepage visitors |
|---|---|
| Homepage visit | 100% |
| Browse titles | 71% |
| Title detail page | 48% |
| Start playing | 29% |
| **30+ min session** | **11%** |

Daily active users 1,490,000, down 21%. Average session length 24 minutes, down 23%. Sessions reaching 30+ minutes 11%, down 8 points. Content searched then played 34%, down 7 points. **Spotlight feature (new): 18%.**

**Reconciliation.** This confirms the M2 friction and locates it precisely. The top of the funnel is healthy — 71% browse, 48% reach a title page — so people are not failing to look. They are failing to *commit*: only 29% start anything, and only 11% stay. The collapse is at depth, not at entry, which is exactly the moment-of-misery we documented from interviews. Someone who scrolls for twenty minutes and closes the app is inside that 71-to-29 gap.

The 8-point fall in 30+ minute sessions is the business crisis stated as a number, and it is the metric this initiative should be judged on.

### Snapshot 2 · Subscriber retention cohort heatmap

| Cohort | Mo 0 | Mo 1 | Mo 2 | Mo 3 | Mo 4 | Mo 5 | Mo 6 |
|---|---|---|---|---|---|---|---|
| Sep · Full Library | 100% | 68% | 51% | 39% | 29% | 21% | 16% |
| Oct · Full Library | 100% | 66% | 49% | 37% | 27% | 19% | |
| Nov · Full Library | 100% | 63% | 47% | 34% | 24% | | |
| Dec · Spotlight | 100% | 74% | 61% | 52% | | | |
| Jan · Spotlight | 100% | 77% | 64% | | | | |
| Feb · Spotlight | 100% | 79% | | | | | |

**Reconciliation — and this is the snapshot that changes the project.**

**It is a leak, not a ceiling.** Read vertically, Full-Library cohorts were getting *worse*: 68 → 66 → 63 at Month 1. Newer users were retaining less well than older ones, which the module classifies as a regression. A regression needs a fix, not an improvement — and we have evidence of what the fix is.

**Spotlight is already that fix, and it is working.** The December cohort onward retains 12–15 points better at Month 1, and the trend is still climbing: 74 → 77 → 79. This is not a projection. It is measured, from real exposed cohorts.

**Month 0 → 1 remains the biggest single leak regardless.** Even the best Spotlight cohort loses 21% in the first month. Spotlight improves the leak; it does not close it.

**What that says about onboarding.** The first month is where a subscriber decides what to expect from the product. Losing a fifth of them inside it — after curation has already been added — means the problem is not only that discovery is hard, but that the first few sessions do not show anyone what the product is for. That matches the M2 journey map, where the viewer's expectation falls a little with every failed search.

It also points at a fix we had already scoped for a different reason. The first-run onboarding introduction in the M4 PRD (FR11) exists to say who chose these titles. Its second job is this one: making the first session legible, so the viewer forms an expectation worth returning for.

**What this does to our stated risk.** Our largest open risk was "avoidance is not appetite" — that we had no behavioural evidence anyone would *use* a curated surface, only interview quotes saying they would like one. Snapshot 2 is that behavioural evidence. People use it, and they stay longer. The risk is substantially answered, and we should stop carrying it at full weight.

### Snapshot 3 · User segment performance

| Segment | % of base | Monthly LTV | Sessions/wk | Curated / Trending | Churn if Spotlight-exposed |
|---|---|---|---|---|---|
| Power Users | 22% | $14.20 | 4.8 | 58% / 22% | N/A — low churn anyway |
| Casual Browsers | 37% | $11.40 | 2.3 | 31% / 44% | −14 pts |
| Wanderers | 41% | $8.40 | 1.1 | 18% / 61% | −22 pts |

**Reconciliation — this is where the bet changed, and it changed twice.**

**First, the data refused our premise.** Module 1 and Module 2 targeted high-intent, discovery-driven viewers — the loyal, high-value subscribers who open without a title in mind. In this table they are **Power Users**, and their churn response to Spotlight is **N/A, low churn anyway**. You cannot win back a segment that is not leaving. The snapshot says so outright: *Power Users are not the primary opportunity.*

**Second, we did not go where the data pointed.** The critical signal flags **Wanderers** — 41% of the base, the biggest churn improvement at −22 points. On raw retained revenue they win: roughly $758 a month per 1,000 subscribers against $590 for casual browsers. We chose casual browsers anyway, and the reason is a strategic judgement the churn delta cannot express.

### Why casual browsers, against the data's own tick

**The three groups are not three different kinds of people. They are three stages of the same slide.** Value per subscriber falls $14.20 → $11.40 → $8.40, about $3 a step, and sessions fall 4.8 → 2.3 → 1.1 at the same time. Casual browsers are halfway down. Wanderers are near the bottom.

**The −22 points for Wanderers measures damage that has already happened.** By the time someone is in that group they are worth $5.80 a month less than they used to be. Going after the biggest churn number means helping the group that has already lost the most. That is not the same as doing the most good.

**Keeping a casual browser protects $11.40 and stops the $3.00 drop.** Someone who never becomes a Wanderer never ends up in that group at the lower price. The cohort data shows the slide happening: Full-Library cohorts kept 68%, then 66%, then 63% at Month 1 — each group slightly worse than the one before.

**The competitive picture points the same way.** The brief says smaller, curated services are gaining ground. Those services do not take people who still open our app two or three times a week. They take the ones who have stopped expecting anything from it. A casual browser is still ours to keep. Someone down to 1.1 sessions a week has mostly gone already — and as the Module 1 value proposition says, winning someone back always costs more than keeping them.

**What it costs.** About $168 a month per 1,000 subscribers in measured retained revenue, given up for a prevention benefit we cannot size — nothing in the data gives a decay rate from casual to wanderer. It is a judgement, not an arithmetic result, and it should be presented as one.

**Two earlier arguments withdrawn.** We had claimed Wanderers could not be reached by a home-screen rail because they rarely open the app. The −22 points is measured from exposed Wanderers, so they are reached and they respond. We had also claimed Wanderers carry no headroom. That was backwards: they sit $3.00 below casual browsers and $5.80 below power users, so they have more room to grow, not less.

This is the pivot the module describes — the moment the data contradicted the gut and the bet moved. It cost a rewrite of the Module 1 problem hook and value proposition, which was the right trade.

---

## Where the bet is

**Optimizing the existing.** Spotlight is live at 18% reach with measured retention gains. We are not proving that curation creates value — the pilot did that. We are fixing why 82% of visitors never get to it. The metrics to chase are therefore Retention and Conversion, not Activation-of-a-new-idea.

One blue-sky risk remains, and it is small but real: the rail itself is new. The pilot proves the *content* retains people. It does not prove the prime slot is how you reach the other 82%.

## Where it sits in AARRR

| Stage | Our metric | Why here |
|---|---|---|
| Acquisition | — | Not our funnel. The top is healthy: 100 → 71 → 48 |
| **Activation** ⭐ | Spotlight reach (18%) · **users with a 30+ min session (11%)** · time to first play | The aha delivered. A 30-minute session is the key action; time to first play is time-to-first-key-action |
| **Retention** ⭐ | Month-1 retention (~79%) · sessions per week (2.3) · 90-day churn | Whether the habit holds and they come back |
| Revenue | LTV $11.40, ~$4,220 per 1,000 subscribers | Downstream result, not a lever we pull directly |
| Referral | — | Out of scope for this initiative |

Our bet sits in **Activation and Retention**, the two stages the module identifies as the ones a product build most directly controls. The funnel data put the failure there, so that is where the metrics are.

## The hypothesis

### The components

| Field | Answer |
|---|---|
| **Qualitative evidence (M2)** | UXR-03: "Honestly I just re-watch the same four comfort shows. Discovering anything new feels like a chore, so I don't." Supported by UXR-01, who scrolls twenty minutes, plays nothing, and goes back to a DVD. |
| **Quantitative evidence (M3)** | Only 11% of homepage visitors reach a 30+ minute session, down from 19%, while the top of the funnel holds at 71% browsing. Spotlight reaches 18% of visitors; the cohorts that have it retain 12–15 points better at Month 1. |
| **Persona** | Casual browsers — 37% of the base, $11.40 LTV, 2.3 sessions a week. Goal: start something decent in a couple of minutes. Confirmed friction: the search costs more than the evening is worth. |
| **Problem we are solving** | Choosing takes longer than it is worth, so people give up. We already have something that fixes this — a hand-picked selection that keeps people watching — but only 18% ever find it, because they have to go looking for it. |
| **Strategic outcome** | More casual browsers pick something and stay with it. That lifts Month-1 retention and slows their slide toward watching almost nothing. It also gives them a reason to stay with us: four shows they already know are on every service, but a weekly selection they trust is only here. This protects our most valuable group, worth about $4,220 a month per 1,000 subscribers. |
| **Primary success metric** | % of casual browsers with at least one 30+ minute session per week: 11% → 14%. |
| **Guardrail metric** | Total weekly plays per casual-browser subscriber must not fall more than 5% below control. |
| **Decision window** | Six weeks for the ship decision; 90-day churn read before scaling. |

### The statement

> Based on a funnel showing only **11% of sessions reach 30+ minutes** (down from 19%) while the top of the funnel holds at 71% browsing, and on pilot cohorts with Spotlight retaining **12–15 points better at Month 1** despite only **18% adoption**, I believe that moving the curated rail into the prime slot for **casual browsers** — the 37% of subscribers who open two or three times a week with no title in mind — will result in more of them committing to a title and staying with it, as measured by a **+3 percentage point change in sessions reaching 30+ minutes** (11% → 14%) within **six weeks**. I will protect **total weekly plays per casual-browser subscriber** and make a go/no-go decision after six weeks, with a 90-day churn read before scaling.

## Success metrics

| Metric | Type | Baseline | Target | Why it matters |
|---|---|---|---|---|
| **% of casual browsers with at least one 30+ minute session per week** | Primary success | 11% (down from 19%) | 14% (+3 pts) | The case's own critical signal, and a *strategic* metric by the module's test: time-bound, and it proves the viewer's evening actually happened rather than that they clicked something. A session someone abandons never reaches it. **Measured per user, not per session** — see below. |
| **Spotlight reach** — share of casual-browser sessions that open the curated selection | Initiative signal | 18% | 35% | The number this whole initiative exists to move, and the one that moves first. The pilot shows Spotlight works for the people who find it; 82% do not. The target is roughly double today's reach, which is what a surface above the fold should deliver — and it is also the floor the primary metric needs, since 18% cannot produce a 3-point lift in 30-minute sessions arithmetically. Note the baseline measures reach of the curated *space*, since the rail does not exist yet. |
| **New-title play rate** — share of sessions ending in a play of a title new to that viewer | Discovery indicator | Control arm | Higher in arm B | Distinguishes "the rail worked" from "people re-watched for longer." A 30+ minute session spent on a known comfort title is depth without discovery. No historical baseline exists — the case data reports content *type*, never novelty — but none is needed: the control arm supplies it, and the comparison that matters is between arms. |
| **Total weekly plays per casual-browser subscriber** | Guardrail | Control arm | Not more than 5% below control; investigate at 3% | Spotlight narrows choice deliberately. Suppressing consumption rather than redirecting it is a failure, not a trade-off. |
| **Month-1 retention**, arm B vs arm A | Second guardrail | ~79% (latest Spotlight cohort) | Not more than 2 pts below control | Catches a harm the first guardrail cannot see: the rail could raise session depth while making people less likely to come back. Depth bought with retention is not a win, and retention is what the initiative is for. Equivalently, churn must not rise more than 2 points. Baselined against the Spotlight cohort, not Full Library, because Spotlight exists in both arms. Requires simultaneous enrolment so every subscriber reaches Month 1 inside the window. |
| **90-day churn**, exposed vs non-exposed | Confirming metric | Control arm | −14 pts (segment-data prior) | The business outcome the initiative is funded to move. Lands in Phase 3, after the ship decision, as the durability check — a rail that worked only through novelty shows up here. |

**Retired:** the early-abandon guardrail from the previous draft. It existed to catch starts that never became watching — which a 30-minute threshold now catches by construction.

### Why the primary metric counts users, not sessions

The experiment randomises by user. If the metric counted sessions, the two would not match: sessions belonging to the same person are correlated, and standard sample-size maths assumes independent observations. The effective sample would be smaller than the session count suggests.

Counting users removes the problem. One user, one observation, matching the unit we randomise on.

It also matches how the case reports the number. The funnel header reads "% of homepage **visitors** who reach each stage", so the 11% was already visitor-level. Reading it as a session rate was our error, not the data's.

And it asks the better question. "Did this person get a good evening this week?" is what the initiative is for. "Was the average session long?" can be satisfied by one person watching a boxset while everyone else leaves.

## Hypothesis audit — the four pitfalls

| Pitfall | Verdict |
|---|---|
| **Vague or broad** | Passes. Named persona (casual browsers, 37%), named behaviour (sessions reaching 30+ minutes), named metric with a baseline and a target. |
| **Biased framing** | Passes with a caveat. The hypothesis frames around the problem — the depth collapse — rather than around the rail. The M5 experiment brief necessarily names the solution, because an A/B test has to specify a variant; that is a different document doing a different job, not a contradiction. |
| **Not testable** | Passes. Tied to a measured baseline (11%), a specific change (+3 pts), a window (6 weeks), and a metric the product already tracks. |
| **Misaligned with goals** | Passes. 30+ minute sessions feed Month-1 retention, which feeds churn, which is the M1 business crisis. If validated, it moves the North Star. |

