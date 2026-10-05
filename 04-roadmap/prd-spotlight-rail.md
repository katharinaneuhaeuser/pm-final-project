# Simplified PRD — Spotlight Curated Rail

**Author:** Katharina Neuhäuser · **Status:** Draft · **Target:** High-Fidelity Prototype

---

## 1. The Big Picture

### Vision — the core value

A short, hand-picked rail at the top of the home screen that lets a casual browser start something they have not seen within two minutes, without the choosing becoming the evening.

**The single outcome this MVP delivers:** a decided pick, reached without searching.

### Press release

StreamLine today introduced Spotlight, a curated rail on the home screen carrying five to seven titles chosen by people rather than by the recommendation engine. It replaces the first thing subscribers currently meet — an endless grid ranked by what is trending — with a short list somebody stands behind.

It is built for the 37% of subscribers who open StreamLine two or three times a week with no title in mind. Today those viewers scroll, find the same rows they scrolled last week, and take one of two exits: they re-watch one of a handful of titles they have already seen, or they close the app with nothing played. Both exits cost us the same thing. Spotlight removes the scroll from the decision entirely: a small number of options, visible without scrolling, any of which can be playing within two taps.

### Success metrics

- **Primary:** % of casual browsers with at least one 30+ minute session per week. Baseline 11%, down from 19% six months ago; target 14%. Attributable to the rail via the `played_from_rail` flag.
- **Initiative signal:** Spotlight reach — share of sessions that open the curated selection. Baseline 18%, target 35%. This is what the rail exists to move, and it moves first.
- **Guardrails:** Total weekly plays per casual-browser subscriber, not more than 5% below control — Spotlight narrows choice deliberately, and suppressing consumption rather than redirecting it is a failure. Month-1 retention, not more than 2 points below control, so depth is not bought with churn.

---

## 2. The Details

### User stories

**1. As a casual browser opening the app with no title in mind, I want a short list of picks at the top of the home screen, so that I do not have to scroll in order to decide.**
- Acceptance: the Spotlight rail is the first row on the home screen, above any algorithmic row.
- Acceptance: the rail renders between 5 and 7 titles — never fewer, never more.
- Acceptance: the rail is fully visible without scrolling at 390pt phone width and at 1080p.

**2. As a casual browser, I want to see what each pick actually is at a glance, so that I can judge it without opening anything.**
- Acceptance: every card shows a thumbnail and the complete title.
- Acceptance: no card renders with a missing title or a broken image placeholder.
- Acceptance: titles are legible at rail size without truncation beyond two lines.

**3. As the PM running the experiment, I want every play that starts from the rail to be identifiable, so that I can tell whether the rail caused the change in 30-minute sessions.**
- Acceptance: every play event carries `played_from_rail` as a boolean.
- Acceptance: the flag is `false` when the same title is reached by search or by any other row.
- Acceptance: every play event also carries whether the title was new to that viewer.

### Screens to build — the happy path

Three screens, which is the whole path from opening the app to watching. Anything that is not on this path is not in the MVP.

**Screen 1 · Entry point — Home**
Spotlight rail as the first row, with section heading and a persistent attribution subline ("Chosen weekly by our editors"); 5–7 cards each showing thumbnail and title; two or three placeholder algorithmic rows beneath it, so the rail's position is visible in context. On a viewer's first exposure the subline is emphasised and the cards animate in in sequence — once, never repeating, never blocking a tap. After that the subline stays, in its resting state.

**Screen 2 · Feature core — Title detail**
Hero thumbnail; title; one-line synopsis; a single primary Play action; a back control returning to Home with the rail's order unchanged.

**Screen 3 · Success — Now playing**
Playback-started confirmation; title being played; an indicator showing whether the play was attributed to the rail (prototype stand-in for the analytics event); a return-to-Home control.

### Functional requirements

1. The Spotlight rail renders above the fold on the home screen, positioned before any algorithmic row.
2. The rail displays no fewer than 5 and no more than 7 titles.
3. Every card renders a thumbnail and the complete title; neither is optional.
4. Rail contents are read from a single editable data source — a JSON array in the prototype, standing in for the CMS or spreadsheet. Changing that source changes the rail with no code change.
5. Selecting a card navigates to the title detail screen for that title.
6. The title detail screen exposes exactly one primary Play action, which starts playback.
7. Every play event records `played_from_rail` — true only when the journey began at a rail card. Every play event also records `is_new_to_viewer` **where watch history is available**; where it is not, the field is written as `unavailable`, never inferred or defaulted.
8. The rail does not paginate, scroll horizontally beyond its items, or offer a "see all" affordance.
9. The title detail screen renders a one-line synopsis from the catalogue record.
10. **Eligible**, for the purposes of the minimum-count rule, means: present in the curation source, currently available in the catalogue, and — only where watch history is available — not already watched by this viewer.
11. **First-run introduction.** The first time a viewer sees the rail, a one-time introduction plays: the rail header reveals its attribution — who chose these titles and how often they change — and the cards animate in in sequence. It never blocks interaction, and it never repeats for that viewer.
12. Where the viewer's system requests reduced motion, the introduction renders as the same static attribution label, shown once, with no animation.
13. **Persistent attribution subline.** A short line sits under the rail heading on every render: "Chosen weekly by our editors." It does not depend on the first-run introduction and does not disappear once that has played. Without it, a viewer who misses or forgets the introduction sees a rail indistinguishable from any algorithmic row.
14. **Editorial selection rule.** The weekly selection does not lean on titles most of the base has already watched. Where the per-viewer check in FR10 is unavailable, this rule is the only thing stopping the rail from showing someone what they have already seen. It is a curation guideline, not a build dependency, which is why the watch-history integration could be demoted to Should without putting the MVP at risk.

### Smart behaviors

| Situation | Outcome |
|---|---|
| Curation source returns fewer than 5 eligible titles | Hide the rail entirely rather than render it short; the home screen displays normally |
| Curation source is empty or unreachable | Hide the rail; show no error to the viewer; log the failure |
| A card's thumbnail fails to load | Render a title-only card; never show a broken-image placeholder |
| Viewer opens a card, then returns to Home | The rail keeps its original order; it does not reshuffle mid-session |
| Viewer returns to Home after starting playback | The rail is unchanged, and the played title remains in it. Removing it mid-week would make the rail shrink below its minimum and contradict the fixed-selection promise |
| Watch history is unavailable at play time | Record `played_from_rail` as normal and `is_new_to_viewer` as `unavailable`. Never default it to true — a defaulted value would inflate the primary metric |
| Play starts from a rail card | `played_from_rail = true` |
| Play starts on the same title via search or another row | `played_from_rail = false` |
| A curator note field is empty | Render title and thumbnail only; never substitute generated or placeholder copy |
| Viewer taps a card while the first-run introduction is playing | The introduction ends immediately and navigation proceeds; it is never a gate |
| Viewer's first session falls on a day the rail is hidden (fewer than 5 eligible) | The introduction is not consumed. It plays on the first session where the rail actually renders |
| Viewer has already seen the introduction | Rail renders normally, with the attribution line in its resting state |

### Technical constraints — what not to build

No external APIs. No login or account state. No backend; `useState` only. No recommendation logic, ranking, or personalisation of any kind — the rail order is exactly the curation source's order. No real video playback; the Now Playing screen is a confirmation state. No routing library beyond simple view switching.

---

## 3. The Logistics

### Features out (from Won't Have)

Multiple themed rails · expandable curator notes · personalisation of the rail per taste profile · curator profiles and following · AI-generated "why you'll love this" copy · mood or occasion entry points · filters or sort controls on the rail · offline download · social and watch-party features.

### Edge cases

- **Fewer than 5 eligible titles:** rail hidden, not shortened. A three-item rail reads as a bug and undermines the "somebody chose this" claim.
- **Title removed from the catalogue after curation:** drop it from the rail; if the count falls below 5, hide the rail.
- **Thumbnail unavailable:** title-only card, never a broken image.
- **Viewer has already seen every pick:** the rail still renders in this version. Per-viewer exclusion is a Should, not a Must — the curator approximates it at selection time. Accepted limitation, recorded in the decision log.
- **Safety / hallucination guard:** all curator-facing copy in this version is human-written. The prototype must never generate, paraphrase or invent a title description, synopsis or reason-to-watch. An empty copy field renders as absent, not as filler. This guard exists because AI-generated reasons are a deferred feature (A2) and must not leak into a build meant to test human curation.

### Decision log

**1. Reuse the existing title detail screen rather than build an in-rail play path.** Costs one extra tap against the ideal flow, but avoids building a second playback surface inside a three-week sprint. If the tap proves to be where viewers drop, that is a finding worth having before investing in a bespoke path.

**2. Ship without curator notes; test the surface alone.** The note is a Should, not a Must. This isolates a single variable: sprint 1 answers whether the prime slot raises reach and depth, before adding the explanation layer. The six-week read is therefore a verdict on placement, not on curation — the pilot already settled whether the curation itself retains people.

**3. Attribution ships as a first-run introduction, not as a per-card byline.** The curator byline is a Could-have, so without this the rail carries nothing indicating a human chose it — and a hand-picked rail that looks identical to a well-tuned algorithmic row is not testing what it claims to test. The introduction says it once, at the only moment it matters, for the cost of a one-time animation rather than a permanent surface element. It is deliberately part of the product and not a launch communication: a comms treatment could not be targeted to one experiment arm, and would have had to wait until after the read.

### The alignment handshake

The PRD and the prototype go to each stakeholder together. The PRD gives the rules, the prototype shows the flow.

**Manager — strategic green light.** Lead with the prototype, then the numbers. The ask is agreement on the problem and the metric before anyone else is pulled in: Spotlight retains the people who reach it, 82% never do, and the rail is the cheapest way to change that. The decision to confirm is that the six-week read on 30-minute sessions is what we will be judged on.

**Engineering lead — feasibility and simpler paths.** Stress-test the Smart Behaviours, which is where the real cost sits. Three scoping choices are already made in their favour and should be checked rather than assumed: the rail reuses the existing title detail page instead of a new play path; curation ships as a CMS entry or spreadsheet rather than bespoke tooling; and `is_new_to_viewer` is written as `unavailable` when watch history is absent rather than being inferred. Each was chosen to keep A1 at Effort 2. If any of them is wrong, A1 becomes a Major Project and leaves the Now lane.

**Design lead — a validated logic map, not a finished product.** The three screens are the happy path, not a design. The handover is the logic: what the rail does when there are too few eligible titles, what a card shows when a thumbnail fails, how the first-run introduction behaves, and what it falls back to under reduced motion. One design question is still open — the curator byline is a Could-have, so attribution currently lives only in a one-time animation.

### Evals

1. **Time on task:** median time from home-screen load to playback start, via the rail, under **120 seconds** — the persona's own standard is "a couple of minutes."
2. **Attribution accuracy:** **100%** of plays begun at a rail card carry `played_from_rail = true`, and **0%** of plays reached by search or another row carry it. The metric read is worthless if attribution leaks.
3. **Safety trigger:** **zero** rendered cards containing generated, paraphrased or placeholder copy, and **zero** broken-image cards, across the full three-screen flow.

### Eval status against the prototype

These are acceptance criteria for the real build. Only one of them can be meaningfully tested in a click-through prototype, and the honest report is:

| Eval | Prototype result |
|---|---|
| **1 · Time on task under 120s** | Not meaningfully testable. Three clicks will always beat 120 seconds when there is no real catalogue and no real decision. Carries to the build. |
| **2 · Attribution accuracy** | **Passes, and genuinely tested.** This one is logic, not behaviour. Every play from a rail card flags `played_from_rail` true; every play reached by search or another row flags false. Verifiable in the prototype's event panel. |
| **3 · Zero generated copy** | Passes, but trivially — all synopses are hand-written, so nothing could have been generated. The guard matters once AI-generated reasons (A2) ship, which is why it is written down now. |

What the prototype did validate was the logic: the rail hides below 5 eligible titles rather than rendering short, a failed thumbnail degrades to a title-only card, the first-run introduction is not consumed on a hidden-rail day, and the reduced-motion fallback renders. Plus the finding that mattered more than any of them — FR7 could not be satisfied as originally written.
