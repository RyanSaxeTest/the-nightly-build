# How this piece should sound

Explain Jev as a software and model contract. The opening should give the
reader a concrete request and response before naming the larger category. Move
from the returned value to the workflow that consumes it, then to the training
and evaluation claims behind that workflow. Keep the boundary between a
documented mechanism and an inference visible in the sentence that makes it.

Use the plain, curious explanation in Julia Evans's Kubernetes piece as a
check on abstraction. A short example should expose the moving part, and a
qualification should arrive where the example stops carrying the argument. The
article can be confident about what the API constrains while staying cautious
about the weights behind it.

Use Simon Willison's habit of turning a black box into a sequence of inspectable
steps. When the article explains parallel questions or calibration, name the
state, the question, the returned distribution, and the code that acts on it.
Do not use a metaphor where a small request/response example would make the
same mechanism clearer.

Use Dan Luu's measurement discipline when discussing speed, cost, or evals.
Attach every number to its owner, denominator, and measurement context. The
article should make the reader notice what TypeSafe measured, what the
comparison model was, and what the experiment did not test.

The prose should read as a technical investigation rather than a launch recap.
Prefer concrete nouns and short paragraphs. Let the final section answer the
engineering question raised by the first one: which software decisions Jev can
make easier, and which claims still require a team's own data and thresholds.

## Julia Evans, "Reasons Kubernetes is cool"

Source: https://jvns.ca/blog/2017/10/05/reasons-kubernetes-is-cool/

> "There kind of is a trap"

The sentence gives a concrete qualification immediately after a tempting
benefit. Evans's voice is visible in the small turn from excitement to the
operational detail that a production system demands.

> "I love learning new things"

The first-person aside makes the explanation warmer without replacing the
technical point. The surrounding section still names the systems work that made
the claim true.

## Simon Willison, "Interactive explanations"

Source: https://simonwillison.net/guides/agentic-engineering-patterns/interactive-explanations/

> "When we lose track of how code written by our agents works we take on cognitive debt."

The opening names a practical failure and gives it a precise label. The phrase
earns its abstraction by immediately tying it to understanding code and making
changes safely.

> "But how does it actually work?"

The short question is useful because the next paragraphs answer it with a
walkthrough and a visible algorithm. It is not a generic invitation to keep
reading.

## Dan Luu, "Computer latency: 1977-2017"

Source: https://danluu.com/input-lag/

> "I've had this nagging feeling that the computers I use today feel slower than the computers I used as a kid."

Luu starts with a falsifiable observation and immediately treats his own
intuition as suspect. The sentence creates a reason to measure without claiming
that the feeling is already a result.

> "Here are the results:"

The plain handoff works because the page has done the measurement. It does not
announce an insight before showing the table that supports it.
