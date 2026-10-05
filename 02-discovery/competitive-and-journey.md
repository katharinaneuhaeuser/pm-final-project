# Competitive Analysis & Journey Map

> **Module 2 · Lab 2 — ★ Deliverable 2.** Repo file `02-discovery/competitive-and-journey.md` — part of your submission.
> It becomes the **Competitive Analysis & Journey Map** slide of your Module 6 final deck. Builds on your `ai-synthesis.md` and your Module 1 `problem-hook.md`.

## Step 1 · Persona

Chosen persona: **The Resigned Browser**.

### Two behavioural personas, one chosen

The research surfaced two distinct behaviours, not one segment with an average. They need different product decisions, so picking one was a trade-off rather than a summary.

| | **The Resigned Browser** *(chosen)* | **The Occasion Browser** |
|---|---|---|
| Behaviour | Has stopped expecting to find anything new; defaults to trending or a known title | Arrives knowing the kind of evening they want, but not which title delivers it |
| Evidence | UXR-01, UXR-03, UXR-08 — all **observed behaviour** | UXR-09, UXR-12 — both **stated preference** |
| Product decision | A short, pre-decided selection. Remove the choice. | Mood or occasion entry. Let them *describe* the choice. |
| Why chosen / not | Larger share of the segment, and the behaviour is evidenced rather than reported as a wish | Evidence comes only from older participants, and from the kind of question the module flags as unreliable — see below |

The need the Occasion Browser describes does not disappear. It becomes something Spotlight answers through curation, rather than the persona Spotlight is designed around. A4 Mood-Based Entry Point was cut for the same reason: it adds a decision in front of the content for someone whose problem is too many decisions.

### The three categories of insight

**Behaviours** — what they actually do. Open two or three times a week with no title in mind; scroll trending rows; take 44% of consumption from trending and 31% from curated; re-watch a shortlist of four; or close the app with nothing played.

**Need** — the job being hired. *Let my evening start without me having to work for it.* Not "help me find the perfect film" and not "show me more" — the job is to remove the labour from the decision, so that choosing stops competing with watching.

**Pain points** — the friction. Choosing costs more than the evening is worth; the one surface built to help returns near-duplicates of what they just watched; there is no way to express the kind of evening they want.

Stating the need separately matters, because the value proposition argues from pain alone otherwise — and pain tells you what to remove, while the need tells you what to put in its place.

- **Role, who are you solving for? (the specific user segment or profile):** Casual browsers — a regular subscriber who opens StreamLine two or three times a week and has quietly stopped expecting to find anything new. 37% of the base, $11.40 monthly LTV, 2.3 sessions per week, 31% curated against 44% trending consumption.

- **Goal, what is this user ultimately trying to achieve?:** To start watching something decent within a couple of minutes, without the choosing becoming the evening's main activity.

- **Friction, the main barrier (moment of misery) stopping them from succeeding:** Discovery costs more than the evening is worth, so they abandon the search — and there are two exits, not one. Some fall back to a title already seen: UXR-03, "I just re-watch the same four comfort shows. Discovering anything new feels like a chore, so I don't." Others leave entirely: UXR-01 scrolls twenty minutes, closes the app without pressing play and goes back to a DVD; UXR-08 "gave up and opened YouTube." BUG-1091 keeps the loop closed, answering a single viewing with near-duplicate franchise titles, so the one surface meant to help confirms there is nothing new worth finding. The second exit is the more expensive one — leaving with nothing played is how a casual browser becomes a wanderer.

## Step 2 · The current workaround

The headline finding, because it inverts the usual framing: this persona's workaround is not a messy spreadsheet or a manual hack. It is **abandoning discovery entirely** — and it works beautifully for them.

The pain is real. These viewers want to watch something new and do not find it — twenty minutes of scrolling for nothing, and discovery that "feels like a chore."

What makes this hard is that the pain has a cheap escape. Giving up and re-watching a known show removes it immediately, at no cost. Closing the app is cheaper still. So the pain never builds into a complaint or a demand for something better. It gets relieved rather than solved, and the viewer quietly lowers what they expect.

That is why nobody asks us to fix it, and why there is no point at which the problem becomes urgent enough to force a change. Each failed search resets to zero.

- **External tools, the outside platforms or tools the user is forced to use:** A friend or partner's recommendation, trusted over the product's own (UXR-10). A second app opened the moment StreamLine costs them patience — UXR-08 gave up on a loading spinner and "opened YouTube." Physical media: UXR-01 went back to a DVD rather than keep scrolling. Their own memory — a mental shortlist of four already-watched titles that never fails. A competitor's curation email, for those who have already left (UXR-04).

- **The process, the 3 to 5 manual steps the user takes to get the job done:**
  1. Open StreamLine with no title in mind, intending to find something new.
  2. Scroll trending and "Because you watched" — which return more of what they have already seen.
  3. Effort passes the point they were willing to spend; abandon the search for anything new.
  4. Take one of two exits — fall back to a known-good title from the mental shortlist, or close the app with nothing played and do something else entirely.
  5. Begin the next session expecting less, and give it less time.

- **Core frustration, the exact moment the process feels most "broken":** The **experience gap** is the moment the effort tips — they have now spent longer choosing than the evening was worth, and the only guaranteed-good option is something they have already seen, or nothing at all. The surface built to prevent this, "Because you watched," is what confirms it, by answering their last viewing with three more of the same. Whichever exit they take from here, the product has lost: one ends in a re-watch that earns nothing from the catalogue, the other in a closed app.

- **The evidence, a specific quote or behavior from the research that proves this:** UXR-03: "Honestly I just re-watch the same four comfort shows. Discovering anything new feels like a chore, so I don't." Supported by UXR-01: "I scroll for like twenty minutes, and close it without watching anything... I ended up going back to a DVD."

### How strong is this evidence, honestly

The module's standard is that behaviour beats attitude. Measured against it, our evidence splits unevenly — and the split explains our biggest risk.

**Strong, because it is behavioural.** Everything describing the *problem*: twenty-minute scrolls ending in nothing (UXR-01), re-watching four titles (UXR-03), giving up and opening YouTube (UXR-08), 2.3 sessions a week, 44% trending consumption, and the bug reports. These are reported or observed actions.

**Weak, because it is attitudinal.** Everything suggesting the *solution* — that casual browsers want curation. UXR-09 ("I want 'quiet Sunday'") is a stated preference. UXR-12 is a focus group, attitudinal by the module's own classification, reporting what participants would *rather* have. Both are close to "what would your dream product look like?", which the module lists among the questions that invite social-desirability bias.

Nobody has been observed using a curated surface, because none exists. That is not a flaw in the research; it is a limit of what discovery can establish before anything is built.

**What follows from it.** Our confidence in the problem should be high, and our confidence in the solution should be lower than a reader might assume. It is also the methodological reason **avoidance is not appetite** sits at the top of the risk list: UXR-03's "discovering feels like a chore, so I don't" is observed opting-out, while the evidence that they would opt back *in* is entirely what people said they would like. The experiment exists to convert that attitudinal claim into a behavioural one.

### The breaking point — there isn't one

The framework says to find the moment where the cost of inaction finally outweighs the pain of switching. For this persona that moment never arrives, and the reason is the escape described above: re-watching clears the pain every time, so it never accumulates. The cost of doing nothing stays flat, and no threshold is ever crossed.

That changes the strategy. We cannot wait for the current experience to become unbearable, because it won't. Spotlight has to be faster than giving up — a decided pick in under two minutes — because that is what it is actually competing with.

### The competitive field, and why the status quo still wins

Named rivals do exist. Specialist services compete on curated, high-quality catalogues; one sends two hand-picked films a week by email, and UXR-04 cancelled StreamLine and now watches both.

Neither is the primary threat to *this* persona. A casual browser who stops discovering does not switch to a specialist service — they re-watch, or they close the app. They stay subscribed, which is why the loss is invisible in acquisition numbers and only appears as churn months later. Rivals take the high-intent viewers. The status quo takes everyone else, and it takes more of them.

### Why this workaround feeds the business crisis

1. **It hollows out the asset.** 44% trending and 31% curated consumption, for a segment that is 37% of the base, means the library's marginal title generates no value for our largest revenue pool — and the sessions that end with nothing played do not show up in that mix at all, so the real figure is worse than the one we can see.
2. **It trains the system to get worse.** Re-watch behaviour feeds "Because you watched," which returns near-duplicates (BUG-1091), which confirms there is nothing new — a closed loop that tightens every cycle.
3. **It removes all switching cost.** A subscriber whose viewing is four known shows can get those anywhere; nothing about their consumption is specific to us. That is the mechanism behind the 14-point churn gap, and why this segment swaps where power users do not.

## Step 3 · Future-state journey map

- **Your journey map, a shareable link, or the map file you committed:** [`02-discovery/journey-map.html`](journey-map.html) — four-stage future-state map with the current-state loop shown above it for contrast, built on the Scenario A strategy block ("Restore & curate"). A plain-text twin is committed alongside it at [`journey-map.md`](journey-map.md).

