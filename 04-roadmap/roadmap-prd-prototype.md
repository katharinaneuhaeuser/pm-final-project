# Roadmap, PRD & Prototype

> **Module 4 · ★ Deliverable 4.** Repo file `04-roadmap/roadmap-prd-prototype.md` — part of your submission.
> It becomes the **Roadmap, PRD & Prototype** slide of your Module 6 final deck. (Your Module 4 · Exercise 2 PRD sprint lands in `prd-and-prototype.md`.)

## Strategic anchors

Pulled from M2 and M3. If a feature doesn't move the primary metric, its Value can't be a 5.

- **Persona (M2):** Casual browsers — "The Resigned Browser." The 37% of subscribers who open StreamLine two or three times a week with no title in mind and settle for whatever is trending.
- **Primary success metric (M3):** % of casual browsers with **at least one 30+ minute session per week**. Baseline 11%, down from 19% six months ago. Target 14%.
- **Initiative signal (M3):** Spotlight reach — share of sessions that open the curated selection. Baseline **18%**.
- **Moment of misery (M2):** Discovery costs more than the evening is worth, so they abandon the search — falling back to a title already seen, or closing the app with nothing played.
- **Guardrails (M3):** Total weekly plays per casual-browser subscriber, not more than 5% below control. Month-1 retention, not more than 2 points below control.

**What we are building, precisely.** Spotlight — the curated space — already exists, piloted from the December cohort, and it works: those cohorts retain 12–15 points better at Month 1. But only 18% of visitors ever reach it. **A1 is the rail that brings it to the home screen.** We are not building curation; we are building the surface that gets a proven thing in front of the other 82%.

**Constraints:** 2 engineers + 1 designer · 3-week sprint.

## High-level product roadmap

Interactive version: [`04-roadmap/roadmap.html`](roadmap.html) — lanes, quadrant badges, Value/Effort meters and a live quadrant filter. Screenshot that for the M6 deck slide.

Quadrant rule: Value ≥ 4 is high, Effort ≤ 2 is low.

| # | Feature | V | E | Quadrant | Lane | Rationale |
|---|---|---|---|---|---|---|
| A1 | Spotlight Curated Rail | 5 | 2 | Quick Win | **Now** | The reach mechanism — puts the already-proven curated selection in the prime slot, where the other 82% will meet it. The only item that directly moves both Spotlight reach and 30+ minute sessions. Ships with manual curation, not bespoke curator tooling. |
| A6 | Spotlight Digest Email | 4 | 2 | Quick Win | **Now** | The only feature that creates a session rather than improving one, and the only one that reaches the viewer who stopped opening the app. UXR-04 is direct competitor proof. |
| A2 | "Why You'll Love This" Label | 4 | 3 | Major Project | **Next** | Human-written curator notes ship inside A1; the AI-generated version is a separate project, worth building only once the concept is proven. |
| A7 | Curator Profiles | 4 | 3 | Major Project | **Next** | The switching-cost mechanism from the journey map's Return stage — but it needs curation worth following to exist first. |
| A3 | Hidden Gem Badge | 3 | 1 | Fill-In | **Later** | Cheap and surfaces the back catalogue, but a badge nudges rather than decides — it needs a working rail to sit on. |
| A9 | Advanced Filter Engine | 4 | 3 | Major Project | **Later** | Weak as a user-facing feature for a persona who won't assemble a query — but the normalised metadata beneath it is what curator tooling, hidden-gem detection and any future occasion browsing all sit on. Scored as an enabler, not as a filter UI. |
| A4 | Mood-Based Entry Point | 3 | 3 | Time Sinker | **Cut** | Serves the Occasion Browser persona we deliberately rejected, and puts a decision in front of the content for someone whose problem is too many decisions. |
| A5 | Personalized Spotlight Queue | 2 | 4 | Time Sinker | **Cut** | Re-introduces the personalisation loop Spotlight exists to break; a taste-profiled Spotlight is the recommendation row with a new name. |
| A8 | Watch Party (Spotlight) | 1 | 5 | Time Sinker | **Cut** | Coordination infrastructure for a group that has already agreed what to watch — downstream of the decision we're fixing. |
| A10 | Offline Download (Spotlight) | 1 | 4 | Time Sinker | **Cut** | Changes where you watch, not whether you chose; it presupposes the decision this persona never reaches. |
| **A11** | **Play Something** *(added, not on the supplied backlog)* | 4 | 2 | Quick Win | **Later** | One title, one tap, no choice — triggered when a session passes the give-up threshold. The only item that addresses the experience gap directly rather than preventing it. Held for Later on purpose: the week-6 read decides whether prevention was enough. |

### A11 · Play Something — the feature the journey map asked for

The M2 journey map exposed that **Give up is the only stage with no touchpoint at all**. At the moment the viewer needs the product most, nothing is there to meet them. Spotlight answers that by *prevention* — the short rail means the scroll never starts — but prevention is never complete, so the gap moves rather than closing.

A11 is the intercept: when a session passes the give-up threshold, offer one title, one tap, no choice. It is UXR-12's "just tell me what's good tonight" taken literally, and it is the Netflix "Play Something" archetype.

**Why it is Later and not Now**, despite scoring as a Quick Win:

- Re-serving the same curated picks in an interruption fixes nothing — the viewer already scrolled past them. A11 only earns its place if it is a *different* bet from curation, which makes it a second experiment, not a second feature in this one.
- Running it alongside A1 confounds the test. We would not know which surface moved the metric.
- The week-6 read answers whether it is needed at all. If 30-minute sessions move, prevention was sufficient. If they do not, an intercept carrying the same content would not have rescued it either.

Added using the lab's blank backlog row, which exists for a feature discovered in M2 or M3 that is not on the supplied list.

### What is deliberately not on this roadmap

The M2 synthesis rated one item **Critical**: "My List" does not sync between mobile and TV, with 340+ support tickets this quarter. It is absent here.

That is deliberate. Critical bugs get fixed because they are broken, not because they won a prioritisation exercise — this roadmap sequences the Spotlight initiative, and a sync defect of that size should be in flight already rather than waiting for a lane. The team fixes it immediately, in parallel.

Worth noting for the initiative: **Spotlight is unaffected by that bug.** The rail is editorial, not personal — every viewer sees the same weekly selection, so there is no per-user state to sync across devices. A personalised rail would have inherited the problem.

### Capacity balance — the 70 / 20 / 10 split

The roadmap is not all core work. Mapping the lanes against the module's split:

| Share | Type | Items | Why it lands here |
|---|---|---|---|
| ~70% | **Core product** | A1 Spotlight Curated Rail, A2 "Why You'll Love This" | The rail, plus the note that tells you why a title was picked. This is the bet, so it gets most of the capacity. |
| ~20% | **Adjacent growth** | A6 Spotlight Digest Email, A7 Curator Profiles, A3 Hidden Gem Badge | Each takes the same curated selection further: into email, into a following mechanic, into a badge. They widen the bet without changing it. |
| ~10% | **Exploratory** | A9 Advanced Filter Engine, A11 Play Something | A9 builds metadata other features will need later. A11 removes the choice instead of improving it, which is a different bet, and waits for the week-6 read. |

The cut list uses no capacity.

### Scores re-checked against the new success metric

Value is defined as the anticipated lift on the M3 success metric. That metric changed on 2026-10-03, from new-title play rate to **% of sessions reaching 30+ minutes**, with **Spotlight reach** as the initiative signal. All eleven scores were re-checked against the new definition and none of them moved.

They held because both metrics measure the same chain: reach the selection, commit to a title, stay with it. A feature that raised new-title plays raises 30-minute sessions for the same reason. A1 stays a 5 — it is the only item that moves reach directly. A5 stays a 2 — personalising the rail would turn it back into the recommendation row people already ignore.

Two rationales were reworded rather than rescored: A1 is now described as the reach mechanism rather than the core mechanism, and A11's trigger references 30-minute sessions.

### Why Now is two features, not three

A1 and A6 are not two bets on the same mechanism — they are **one feature per exit**. A1 addresses the viewer who opens the app and gives up inside it. A6 addresses the viewer who stopped opening it at all. The sprint therefore covers both failure modes rather than half of them.

Holding at two also keeps the six-week gate readable: 30-minute sessions is the kill-or-continue signal, and a third simultaneous change makes it harder to say what moved it.

**Scoping note behind A1's Effort 2:** the rail ships with manual curation — a CMS entry or a spreadsheet, not bespoke curator tooling. If the sprint builds the tool as well, A1 becomes an Effort 3 Major Project and stops being a quick win.

## Lab reflection

**Instinctive quick wins before touching the AI:** A1, A6, A3. A1 is the initiative itself and needs no ML. A6 is the only backlog item that *creates* a session, which matters at 2.3 sessions a week. A3 is nearly free and surfaces the back catalogue.

**Where I overrode the AI baseline:**

- **A5 · 4 → 2.** The baseline rewards "personalized" because it sounds aligned to the metric. BUG-1091 shows the personalisation loop *is* the failure. The value proposition is a point of view, not a taste profile. Moved from Major Project to Time Sinker, and cut.
- **A6 · 3 → 4.** The baseline penalised it for acting outside the app. That is backwards: at 2.3 sessions a week the binding constraint is that they do not open the app at all, and this is the only item that creates an occasion. It is also the only feature that reaches the second exit — the viewer who left with nothing played.
- **A7 · 3 → 4.** The baseline called it "retention rather than a direct lever," missing the journey map's Return stage. Following a curator is the switching-cost mechanism and the answer to why this segment swaps at all.
- **A4 · 4 → 3.** Reads as on-friction and carries an M2 UXR origin, but serves the persona we rejected and adds a decision before content. Guardrail risk too. Cut rather than deferred.
- **A9 · 2 → 4.** The baseline scored the filter UI; the value is the metadata layer beneath it, which curator tooling and hidden-gem detection both require. Scoring the enabler rather than the surface moves it from Time Sinker to Major Project — deferred, not discarded. The baseline also discounted it partly for being Engineering-originated, which is origin bias running the other way.
- **A2 · Effort 3 → folded into A1.** Human-written curator notes deliver the same benefit as AI-generated reasons; the value belongs in A1 this sprint.

**Did the AI over-value a Sales/Engineering request?** A8 and A10 are the obvious cuts, but both share a defect worth naming: they sit **downstream of the decision**. Offline Download changes where you watch, not whether you chose; Watch Party coordinates a group that has already agreed. Neither is low-value because Sales asked — they are low-value because they solve the wrong end of the journey. A9 is the reverse case: I under-scored an Engineering request because of its origin, which is the same bias running the other way. Origin tells you who is advocating, not whether they are right.

**Did it underweight something the M3 data supports?** A6, clearly. M3 Retention origin, and the 2.3-sessions-per-week figure is the entire problem statement. Every other feature improves a session that already started; a weekly digest is the only one that starts one.

**My "Now" lane:** A1 Spotlight Curated Rail with hand-written curator notes, and A6 Spotlight Digest Email — one for each exit from the failed decision.

**What I cut, and the "no" I'm protecting:** A4, A5, A8, A10. The "no" is to features that sit downstream of the decision, improving the experience after a choice is made for a persona who never gets that far. A5 is the most dangerous of the four because it *sounds* like the initiative — it is the recommendation loop that failed, rebuilt inside the surface meant to escape it.

## PRD snippets

_Module 4 · Lab 2 — lands in [`prd-and-prototype.md`](prd-and-prototype.md). Top "Now" feature to build against: **A1 Spotlight Curated Rail**._

## Wireframes / prototype

Built in Module 4 Lab 2: [`prototype-spotlight-rail.html`](prototype-spotlight-rail.html) — a clickable prototype of A1 with live analytics attribution and switches that exercise the Smart Behaviours table. The PRD it was built from is [`prd-spotlight-rail.md`](prd-spotlight-rail.md); what building it exposed about the PRD is in [`prd-and-prototype.md`](prd-and-prototype.md).

Roadmap artifact: [`roadmap.html`](roadmap.html)

