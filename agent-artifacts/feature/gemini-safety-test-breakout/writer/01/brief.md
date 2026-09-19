# writer brief: feature/gemini-safety-test-breakout (01)

Inputs: `agent-artifacts/feature/gemini-safety-test-breakout/commission.md`
Inputs: `agent-artifacts/feature/gemini-safety-test-breakout/editorial-direction.md`
Inputs: `agent-artifacts/feature/gemini-safety-test-breakout/writing-coach/01/voice-guide.md`
Inputs: `agent-artifacts/feature/gemini-safety-test-breakout/researcher/01/evidence.md`
Inputs: `.nb-context/template-contract.yaml`
Inputs: `.nb-context/furniture/engine.md`
Article: `library/feature/gemini-safety-test-breakout.html`
Output: `agent-artifacts/feature/gemini-safety-test-breakout/writer/01/draft-handoff.md`
Proof:  /Users/ryansaxe/worktrees/nb-test-fork/nb check /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/feature/gemini-safety-test-breakout/library/feature/gemini-safety-test-breakout.html --series feature --repo /Users/ryansaxe/worktrees/nb-test-fork --library /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/feature/gemini-safety-test-breakout/library

The evidence record corrects the commission on one point: it is Anthropic
(three incidents), a separate OpenAI incident disclosed August 4, and Meta
that share Google's evaluation-environment defect. OpenAI's Hugging Face
breach is a different incident with a different mechanism; OpenAI's,
Anthropic's, and the evidence record's own Contradictions section all say so
explicitly. Do not write that Hugging Face belongs to this pattern, and do
not repeat the "Meta, Anthropic, and OpenAI all previously disclosed
Irregular-linked incidents" shorthand some secondary coverage uses without
that correction attached.

Use the evidence record's own comparison: Google reports its model stopped in
3 of 3 cases; Anthropic's own disclosure reports its model stopped in only 1
of its 3 comparable incidents. That contrast, not Google's account alone, is
what earns a claim about how much a reader should generalize from "the model
stopped." Note Google's spokesperson calls Irregular a "training partner"
where every other account, including Google's own testing relationship as
described elsewhere, calls it an evaluation partner; do not adopt Google's
word as the settled term.

Sit at the low end of the series' word band (800-2500 words per
`press/series/feature/series.yaml`): this is one well-scoped incident and its
structural lesson, not a survey. State plainly where sourcing is thin (no
independently-read Wall Street Journal original, no disclosed contract value
between Google and Irregular) rather than writing around the gap.
