# Commission: news-brief/2026-09-19

## Assignment

Cover what moved in technology since yesterday, 2026-09-18, against the
series' own test in `press/series/news-brief/prompt.md`: an item qualifies
when it changes what can be built, what it costs, who sells it, or what a
government, court, or standards body does about it. Sit at the low end of the
template's item band (4 items, not 6), because the day's real, qualifying
developments are covered by the three leads below. Do not add a fourth or
fifth item to hit a count; if the researcher verifies a fourth genuinely
qualifying, distinct item from 2026-09-18 or 2026-09-19, include it, but three
solid items beat a padded fourth.

## Leads

These are candidate items, not settled copy. Verify each against its own
primary source and find the required independent secondary account before the
writer uses it; drop any that does not hold up or does not clear the series'
qualifying test.

1. NASA awarded SpaceX a contract modification (reported near $946-950
   million) for three more crewed ISS flights (Crew-15/16/17), extending the
   Commercial Crew Transportation Capability contract's period of performance
   through 2030 and raising its total value. Primary: NASA's own award
   announcement or contract record. This is a government contract decision.
2. Nscale, an Nvidia-backed AI cloud/GPU-rental provider, filed to go public
   on the NYSE (ticker NSCL), disclosing steep revenue growth alongside a
   widening net loss and a large remaining-performance-obligations backlog.
   Primary: Nscale's own S-1/prospectus filing. This changes who sells AI
   compute capacity and on what terms.
3. Anthropic and OpenAI are reported pursuing smaller (roughly 20-30 MW) AI
   data center deals, including in the UK and Nordics, alongside their
   existing gigawatt-scale commitments, favoring faster time-to-usable
   capacity for inference over training-scale buildouts. Primary: the labs'
   own statements if available; otherwise the original reporting that first
   surfaced this, corroborated independently. This changes what can be built
   and how AI compute capacity gets deployed.

## Boundaries

Do not cover the Google Gemini/Irregular security-test incident or OpenAI's
frontier-safety misalignment disclosure this week. Both are covered in this
run's `feature/gemini-safety-test-breakout` article; repeating either here
would cover the same ground twice in one day's paper. If a lead above turns
out to be unverifiable or thin, replace it with a different qualifying,
distinct item rather than reaching into AI safety-testing news to fill the
gap.

## Reader and angle

Write for the press's declared reader: a professional who reads widely and
has already seen today's headlines. Each item adds the number or the caveat
the headline dropped, per `templates/brief/identity.md`. An item stands alone;
none should require the reader to already know the story.

## Article shape

Use the `brief` template with 4 items (the series' item band is `[4, 6]`
per its manifest). Meet the series' per-item source floor of at least one
primary and one secondary source per item
(`press/series/news-brief/series.yaml`), and the template's overall six-source
floor, without exceeding what that floor requires.

## Production record

Harness: Claude Code, unattended scheduled orchestrator run.

Model: Configured paper policy is `economy`. Per
`nb production-policy --series news-brief`: writing-coach uses efficient/low
(Claude Haiku), researcher uses capable/medium (Claude Sonnet), writer uses
capable/medium (Claude Sonnet), editor uses capable/high (Claude Sonnet).

## Continuity

Published library history (`nb history`) has one article as of this run:
`dispatches/jev-system-one`. It does not overlap with any of the three leads
above. This run also commissions `feature/gemini-safety-test-breakout`, which
owns this week's AI safety-testing story; see Boundaries above. There is no
news-brief back-catalog yet, so no series-specific habits to avoid.
