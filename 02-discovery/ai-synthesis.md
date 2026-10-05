# AI Synthesis, Product Health & Insights Summary (Module 2)

- **Module 2 · Lab 1** · Scenario: StreamLine Spotlight (B2C)
- Feeds the **Research & Competitive Analysis** slide, alongside [`competitive-and-journey.md`](competitive-and-journey.md)

## The exercise

Read the raw research first, unaided — 12 UXR notes and 10 open bug reports — and write down the moments of misery by hand. Then give the same material to an AI with a tight brief: thematic synthesis only, no roadmap, no recommendations, low-priority defects aggregated into a single line. Then compare the two and find where the AI's version is weaker than it looks.

The aim is to find out where the AI loses things.

## Step 1 · What I found reading the raw data myself

- **Moment of misery / red flag #1:** Loading spinner, then kicked to home screen when selecting a video
- **Moment of misery / red flag #2:** Watchlist does not sync mobile & TV (cross-device)
- **Moment of misery / red flag #3:** User is muting the TV because the autoplay trailer starts too fast

## Step 2 · What the AI produced

The full output is committed separately at [`product-health-summary.md`](product-health-summary.md), with a **severity provenance** section added afterwards in response to logic leak #1 below. Reproduced here as it was returned:

  > **Product Health & Insights Summary**
  > 22. Sept. 2026 · @Katharina
  >
  > Thematic synthesis of 12 user research sessions (UXR-01 to UXR-12) and 10 open bug reports (BUG-1042 to BUG-1121).
  >
  > **Executive Summary**
  >
  > The platform is technically sound in the aggregate but failing at the point of decision: its defects are narrow and addressable, while its experience problems are structural and are the ones users act on. Engineering issues cluster in two areas — playback reliability on older Smart TV hardware and cross-device state synchronisation — whereas research shows the dominant failure mode is behavioural: long browsing sessions that end without a play, retreat to a handful of familiar titles, and churn to competitors offering human curation. The central tension is that stability work alone will not move the outcomes users describe, because the product is already stable enough to browse and still cannot help anyone choose.
  >
  > **Technical Stability & Performance**
  >
  > Instability is concentrated on living-room hardware rather than distributed across the estate. The pattern in both bug data and interviews is that failures occur at the two moments users are least tolerant — opening the app and committing to a title — and that the response is abandonment rather than retry. Users do not report the app as broken; they report it as not worth the wait.
  >
  > - Playback drops to the home screen after roughly 60 seconds of buffering on Samsung Tizen 2021+ Smart TVs, reproducing in 7 of 10 attempts; affected users describe switching to a competing app rather than retrying — High
  > - Cold-start time averages 11 seconds on older TV devices, establishing a perception of slowness before any content is rendered — Medium
  >
  > **Cross-Platform Continuity**
  >
  > This is the most quantified and most damaging cluster in the dataset. The product is used across phone, tablet and TV as a single service, but state is not carried between them, so intent formed on one device is destroyed on another. The downstream effect is not inconvenience but lost consumption: titles saved are never found again, and titles started are never finished.
  >
  > - "My List" does not synchronise between mobile and TV; items added on one device are absent on another, generating over 340 support tickets this quarter — Critical
  > - Resume position is not preserved across devices, restarting titles at 0:00; identified as the leading driver of "couldn't finish" complaints and corroborated by multiple interviews — High
  >
  > **Discovery & Search**
  >
  > Discovery is the most frequently raised theme in research and the one least represented in the bug backlog, because it manifests as friction rather than failure. Users arrive with an intent expressed as mood, occasion or description — "quiet Sunday", "slow French drama" — and the product only accepts an exact title. Catalogue growth compounds this: volume is experienced as an obstacle rather than a benefit, with several participants describing anxiety at the scale of choice and a preference for being told what to watch.
  >
  > - Search supports exact-title matching only; natural-language and descriptive queries return unrelated results, undermining the primary escape route from failed browsing — Medium
  > - No mood-, occasion- or context-based browsing exists; the home screen privileges recency and promotion over reader intent, leaving no path for "something quiet" or "something for a group" — High
  > - Extended browsing sessions terminate without a play, with users reporting 20-minute scrolls, retreat to a fixed set of re-watched titles, or abandonment of the platform entirely — High
  >
  > **Algorithmic Curation & Content Relevance**
  >
  > The recommendation system is not perceived as inaccurate so much as reductive. It infers a genre from a single viewing and returns near-identical titles, which users read as a misunderstanding of who they are rather than a technical limitation. A distinct and more serious signal runs alongside it: users increasingly describe the algorithm's objective as retention rather than satisfaction, and rate friends, editors and competitors' hand-picked selections above it. This is a trust issue, and trust loss appears in the cancellation rationale of at least one lapsed subscriber.
  >
  > - "Because you watched" surfaces near-duplicate titles from the same franchise, producing low-diversity rows that users label repetitive — High
  > - Recommendations are perceived as optimised for continued scrolling rather than for a satisfying selection, eroding confidence in every surfaced row — High
  > - No human or editorial curation layer exists; a competitor's two hand-picked titles per week were cited directly as both a retention mechanism and a reason for churn — Medium
  >
  > **Experience Friction & Controls**
  >
  > A small number of interface behaviours are disproportionately disliked because they override user intent and cannot be turned off. Autoplay is the clearest case: it interrupts the act of reading a title, repeats many times per session, and has driven at least one user to mute their television permanently — a workaround that removes audio from the product entirely. The severity of the defect understates its effect on session quality.
  >
  > - Autoplay trailer audio plays at full volume, ignoring the last volume setting, with no option to disable autoplay in settings; reported at five occurrences in a single session — Medium
  >
  > **Minor Technical Debt**
  >
  > Subtitle timing drifting approximately 2 seconds on titles over 90 minutes, cover-art thumbnails falling back to grey placeholders on slow connections, and completed titles persisting in Continue Watching for up to 48 hours; individually cosmetic, collectively a steady erosion of perceived polish — Low

## Step 3 · The critique

**Did the AI catch the specific moments of misery I found in Step 1?**

Two of the three came back intact. The playback drop and the My List sync failure are both there, at the severity the tracker gives them.

The third survived as a defect but not as the behaviour. I recorded it as a timing problem — the trailer starts before you have finished reading the title. The output records a volume problem: "plays at full volume, ignoring the last volume setting." The prose above the bullet does say it "interrupts the act of reading a title", so the observation exists in the document. It just did not make it into the line a prioritisation meeting would actually read.

**Did it smooth over a critical frustration into a generic bullet point?**

Yes. It generalised the findings and simplified the user feedback more than I would have.

Autoplay is the clearest case. A user muted their television permanently to escape it — they removed audio from the product rather than use it as built. That is a person abandoning a core function, and it is recorded as Medium, because Medium is what the bug tracker says. The defect severity is preserved and the behavioural consequence is lost.

**Did the AI try to suggest features or a roadmap despite the constraints?**

Not in the document. The constraint held exactly where I had placed it.

It did not hold around the document. In the conversation either side of the output, the same assistant offered segment recommendations, metric designs and a persona pivot, none of which I had asked for. Setting a rule for the document did not set it for the conversation about the document — worth knowing, because the document is the part you check.

**Logic leak #1 — two sources, one voice.**

The summary does not distinguish what came from the bug tracker from what came from the interviews. Everything is rendered in the same format with the same severity labels, so a reader cannot tell which items carry a reproducible defect behind them and which are a judgement about how strongly users felt. That matters for both actionability and reliability.

Some of the High severities turned out to be assigned rather than sourced: "no mood-based browsing exists" and "extended sessions terminate without a play" have no tracker equivalent at all. **Fixed** by adding a severity provenance split to [`product-health-summary.md`](product-health-summary.md), separating the ten tracker severities from the four the AI assigned itself.

**Logic leak #2 — 12 sessions that were never 12 sessions.**

The output opens with "thematic synthesis of 12 user research sessions." There were 12 research *notes*. How many sessions produced them is not stated anywhere in the source. The number was carried over and relabelled, which reads as more primary research than the project actually has.

## What I took from it

The AI did not make anything up. Nothing in the output is invented, and for the brief it was given, it is a good document.

What it does is flatten things out. A tracked defect and a researcher's judgement end up looking the same. So do a person who was annoyed and a person who gave up. So do a note and a session. None of this shows up as a mistake. It shows up as a summary that sounds more certain and more even than the evidence behind it.

So I can use it for the first pass but not for the severity call. The moment of misery and the persona both had to come from reading the raw notes myself. This is where I started checking its claims against the source every time, and I kept doing that for the rest of the project. More on that in [`06-launch/individual-insights.md`](../06-launch/individual-insights.md).
