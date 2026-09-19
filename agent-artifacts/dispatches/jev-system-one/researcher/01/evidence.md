# Evidence: dispatches/jev-system-one (researcher/01)

The public record supports a narrow but consequential description of Jev. It is
TypeSafe AI's first System One model: a hosted model that evaluates a textual
state against developer-defined typed questions and returns constrained answers,
probability distributions, and, for Choice and Score, a confidence statistic.
The design moves control flow and side effects into code while reserving the
model for judgments over unstructured or semi-structured input. TypeSafe also
documents a post-training objective called Reinforcement Learning for Calibrated
Decisions, parallel evaluation of independent questions, and early-access price
and latency claims.

The evidence is thin where the question becomes architectural. TypeSafe names a
new model architecture and a parallel sampler, but the public release does not
specify the model family, parameter count, pretraining corpus, training compute,
or weights. Its workflow evaluations are vendor-designed harnesses measured
against reference-model judgments, not independently reproduced accuracy tests.
The strongest article should therefore explain the observable contract and its
software consequences without treating the contract as proof of general model
quality.

## Sources

### 1. TypeSafe AI launch post

URL: https://typesafe.ai/blog/introducing-system-one-models-and-jev

Kind: primary. TypeSafe's founder and company announcement owns the claims
about the product's release, design goals, training method, benchmarks, price,
latency, and open questions.

Establishes: TypeSafe calls System One a new class of frontier models for fast,
structured software decisions. It identifies Jev as the first public model in
early access and names a new model architecture, a parallel sampler, and RLCD.
It describes the output as typed probabilistic decisions rather than strings.

Paraphrase: TypeSafe's comparison table sets the intended contract. Existing
LLMs are described as sequential string generators optimized through RLHF or
RLVR. Jev is described as accepting unstructured state, returning predefined
typed values plus probabilities, and evaluating outputs in parallel. The post
lists $0.042 per million input tokens, free output, and 70–500 ms TypeSafe
latency. It says the 193.6x faster and 444.6x cheaper claims come from the
company's workflow evaluations. The author discloses that the side-by-side
state is short and favorable, that one recorded comparison disagreed on one
ambiguous item, that the workflows were made by the company's capabilities team,
and that the reference average favors OpenAI and Anthropic models. The FAQ
leaves architecture, training data, and public benchmark questions unanswered.

Locators: introduction and comparison table; Evidence / Technical Results;
workflow evals; Hallucination and Type-safety; FAQ.

### 2. TypeSafe AI, “System One”

URL: https://docs.typesafe.ai/concepts/system-one

Kind: primary. Official product documentation owns the public definition of the
System One model class and its current input and output contract.

Establishes: A System One model evaluates a state and returns typed answers and
probabilities. Jev currently accepts strings, JSON objects, and arrays of text;
images, audio, and video are not supported. The docs distinguish Choice, Score,
and Noul questions. They state that calibration is measured across groups and
does not guarantee an individual answer.

Paraphrase: The product's practical unit is an evaluation of one state against
one or more developer-defined questions. Its output is a typed decision rather
than generated prose. The documentation's refund example shows the model
providing signals that code can combine with deterministic checks before routing
or escalating a case.

Locators: “System One”; “How it differs from an LLM”; “Fast judgments inside a
larger workflow”.

### 3. TypeSafe AI, “Introduction”

URL: https://docs.typesafe.ai/introduction

Kind: primary. Official introductory documentation owns the product's API-level
explanation and primitive summary.

Establishes: TypeSafe frames the problem as a mismatch between text generation
and decisions consumed by code. It lists the three primitives and says that
questions in one call are evaluated independently and in parallel.

Paraphrase: The company's proposed abstraction is a set of small, composable AI
primitives. A Choice returns a choice, probabilities, and confidence. A Score
returns a score, probabilities, and confidence. A Noul returns the probability
that a statement is true. The docs recommend decomposing broad judgments into
separate questions and composing their answers in code.

Locators: “TypeSafe primitives”; “Atomic questions, composed in code”.

### 4. TypeSafe AI, “Primitives (Questions)”

URL: https://docs.typesafe.ai/primitives

Kind: primary. Official reference documentation owns the question schema and
response semantics.

Establishes: Each question has an ID, type, and instructions. Choice and Score
also take criteria. Choice selects from an unordered set, Score places a state
along ordered levels, and Noul expresses the probability of a yes answer. The
returned fields and the independence rule are specified in detail.

Paraphrase: The model is not being asked to write a decision in prose. The
developer defines the answer space first. Jev returns values that remain inside
that space. Choice returns a selected option and a distribution across options;
Score returns a position, legend, distribution, and confidence; Noul returns a
0-to-1 probability. Questions over one state are independent, so code can ask
many at once and decide which answers matter on a given path.

Locators: “Ask for one snap judgment per question”; “Choose a question type”; “What
comes back”; “Ask multiple questions together”; “Split a complex judgment into
several questions”.

### 5. TypeSafe AI, “State”

URL: https://docs.typesafe.ai/concepts/state

Kind: primary. Official documentation owns the supported state shapes and input
limitations.

Establishes: State is the content evaluated by a System One model. It may be a
string, a JSON object, or an array of text values. Jev currently accepts text
only, and English is the primary training language. The docs show a state that
combines a conversation, order records, and a refund policy.

Paraphrase: State is best understood as the material presented to a panel before
asking for a judgment. Questions are separate from that material. This matters
for the article because Jev's generality comes from the state and question
definitions supplied at request time, not from a customer-specific fine-tuned
model.

Locators: “State can be as simple as a string”; “A support conversation as state”;
“Separate content from questions”.

### 6. TypeSafe AI, “How to build with TypeSafe”

URL: https://docs.typesafe.ai/concepts/how-to-build-with-system-one

Kind: primary. Official implementation guidance owns TypeSafe's intended system
architecture and recommended composition patterns.

Establishes: TypeSafe positions System One as a way to build AI-powered software,
not an agent. Code owns control flow, deterministic rules, and side effects.
The model handles narrow judgments, questions run in parallel, and code uses
probabilities and confidence to act or escalate. The page reports that most
queries complete in about 100 ms and describes the model as structured,
parallel, comparable, fast, and calibrated.

Paraphrase: The engineering consequence is a division of labor. Keep date
arithmetic, database operations, and side effects in code. Put the uncertain
interpretation of text into atomic model questions. Combine returned signals
with explicit thresholds or a downstream learned model. The model does not
choose its own next action, so the architecture has a bounded control loop.

Locators: opening summary; “Three software architectures”; “What makes System
One composable”; “Design a System One workflow”; “Route on uncertainty”.

### 7. TypeSafe AI, “AI primer”

URL: https://docs.typesafe.ai/introduction/machine-learning-primer

Kind: primary. Official foundations documentation owns TypeSafe's account of
RLHF, RLVR, RLCD, and calibration.

Establishes: TypeSafe calls its post-training path Reinforcement Learning for
Calibrated Decisions. It says RLCD trains models to return decisions and
calibrated probabilities rather than generated text. It defines calibration in
aggregate: predictions assigned probability 0.2 should occur about 20% of the
time across many predictions, with no guarantee for one prediction.

Paraphrase: RLCD is an objective claim, not a published description of every
training stage. The material explains what output behavior the objective is
intended to reward. It also argues that human-preference optimization can make a
model sound confident without making its uncertainty useful to software. The
article should report this as TypeSafe's rationale and avoid treating it as an
independent causal proof.

Locators: “Three post-training approaches”; “RLCD and calibrated decisions”; “The
problems with RLHF”.

### 8. TypeSafe AI, “Confidence”

URL: https://docs.typesafe.ai/confidence

Kind: primary. Official documentation owns the definition of returned confidence
and the recommended action thresholds.

Establishes: Choice and Score return probability distributions and a confidence
statistic derived from those distributions; Noul has no separate confidence.
TypeSafe recommends different behavior for high, medium, and low confidence and
says thresholds must be tuned to domain risk and observed accuracy.

Paraphrase: Confidence is not a proof token. It compresses a distribution for
convenience, while the full distribution remains available. A high threshold may
be appropriate for approving a transfer and a lower threshold for showing a
read-only screen. This is the clearest official evidence that schema safety and
calibrated uncertainty do not remove the need for application-specific testing.

Locators: “Confidence is derived from the probabilities”; “I don’t know is a
useful signal”; “Thresholds scale with risk”.

### 9. TypeSafe AI, “Models”

URL: https://docs.typesafe.ai/models

Kind: primary. Official current model reference owns the version, pricing,
limits, aliases, customization, language, and data-handling details.

Establishes: The current documented model is Jev 1.13, identified as
`jev-1.13.0`. The page lists $42 per billion input tokens, or $0.042 per
million, with free output. It lists a 64k-token budget per request and a 32k
budget for state plus the longest question, text-only input, and current rate
limits of 250,000 tokens per second and 1,200 requests per minute. The page says
the aliases can move and that customer data does not produce per-account weights.

Paraphrase: A production team shapes Jev through state, instructions, criteria,
and code rather than through fine-tuning or LoRA. The alias `jev-latest` can
move, so a team that tunes thresholds against a specific version should pin the
version and log the response's model field. The same page warns that limits are
dynamic.

Locators: “Current models”; “Aliases”; “Customizing Jev”; “Language support”; “Data
handling”.

### 10. TypeSafe AI, “Workflow evals”

URL: https://evals.typesafe.ai/

Kind: primary. TypeSafe's evaluation site owns the workflow definitions,
comparison method, and reported aggregate results.

Establishes: The site compares structured workflows with standalone prompts over
four example tasks. It decomposes tasks into code rules plus Noul, Choice, and
Score questions. It assumes the harness is correct and uses the average of
GPT-6 Astra and Claude Fable 5.1 as reference labels. It says each model is
evaluated on the same workflow and reports mean accuracy against consensus labels.

Paraphrase: The result measures a complete harness, not Jev in isolation. The
workflow contains decisions, schemas, and code that determine how model outputs
become actions. The evaluation is useful evidence for the proposed software
pattern, but it cannot establish how Jev performs on arbitrary tasks or whether
the reference models are the right standard for a given deployment.

Locators: “How we evaluate”; “Assume the harness is correct”; example workflows.

### 11. LangChain, “Building a Harness with Jev”

URL: https://www.langchain.com/blog/building-a-harness-with-jev

Kind: secondary. LangChain documents a third-party integration and repeats
TypeSafe's reported speed and cost claims; it does not own Jev's model behavior
or provide an independent benchmark in the article.

Establishes: LangChain describes Jev as a System One model that takes a state and
questions and returns typed answers. It explains the three primitives, shows
that multiple questions can be sent together, and frames Jev as a complement to
the LLM in an agent loop rather than a drop-in replacement for generation.

Paraphrase: The outside integration makes the interface legible to developers:
an agent can keep an LLM for open-ended reasoning and use Jev for routing or
classification. The article's “up to 200x faster” and “400x lower cost” wording
is attributed to TypeSafe's reports, so it is not independent evidence of those
figures.

Locators: “All about Jev”; “How to Use Jev with LangChain”; “Use Cases”.

### 12. Cloudflare Workers AI, “Jev”

URL: https://developers.cloudflare.com/ai/models/typesafe/jev/

Kind: secondary. Cloudflare documents a third-party hosted integration of the
TypeSafe model and supplies an API example; Cloudflare is not the model author.

Establishes: The integration exposes Jev under `typesafe/jev` and shows the same
Noul, Choice, and Score question shapes. The example response contains typed
answers, distributions, and confidence for Choice and Score.

Paraphrase: The model's interface is portable beyond TypeSafe's own endpoint.
That supports the claim that Jev is being offered as a software primitive, but
the example is documentation, not a quality test. Cloudflare's page lists a
32,000-token context window, while TypeSafe's current model page describes a
64k request budget with a 32k state-plus-longest-question limit. The article
should avoid flattening those integration-specific limits into one universal
number.

Locators: model overview; Usage; response body; model information table.

## Contradictions

- TypeSafe's launch post describes 70–500 ms latency and a 40x–200x speed range
  for comparable System One-shaped queries. The same post attributes 193.6x
  speed and 444.6x cost claims to its own workflow evaluations. LangChain
  repeats up-to-200x/up-to-400x figures. These are different scopes and
  baselines, not one stable Jev multiplier. Report the ranges with their owner
  and context, not as a general speed guarantee.
- TypeSafe claims that Jev cannot hallucinate in the sense of generating
  malformed or unconstrained strings. Its own docs say calibration does not
  guarantee an individual answer and recommend domain-specific threshold tests.
  The article must preserve the difference between type safety and semantic
  correctness.
- TypeSafe's current model page lists a 64k request budget with a 32k state plus
  longest-question limit. Cloudflare lists 32k in its integration page. The
  discrepancy may reflect an integration limit or documentation timing; it is
  not material to the mechanism and should not be presented as settled product
  capacity.
- The launch post says Jev uses a new model architecture and parallel sampler,
  but the public documentation explains behavior and serving rather than the
  architecture itself. No source supports an inference about transformer,
  diffusion, parameter count, or pretraining recipe.

## Numbers

Figure: $0.042 per million input tokens; output tokens free
Owner: TypeSafe AI launch post and current model reference
Scope: listed TypeSafe pricing for Jev; output is described as too cheap to meter

Figure: 70–500 milliseconds end-to-end response time
Owner: TypeSafe AI launch post
Scope: TypeSafe's stated service range, with the post noting published evals were
generally run from company laptops on the West Coast

Figure: 193.6x faster and 444.6x cheaper
Owner: TypeSafe AI launch post
Scope: TypeSafe's workflow-evaluation claims, not a general benchmark; the post
notes company-team workflows and reference-model bias

Figure: 64k tokens per request and 32k for state plus the longest question
Owner: TypeSafe AI current model reference
Scope: current documented Jev 1.13 model limits; rate limits are dynamic

Figure: 250,000 tokens per second and 1,200 requests per minute
Owner: TypeSafe AI current model reference
Scope: current listed rate limits, explicitly subject to change

Figure: calibration example of 0.2 probabilities occurring about 20% of the time
Owner: TypeSafe AI AI primer
Scope: aggregate calibration explanation, not an individual-answer guarantee

## Source assets

Asset: TypeSafe's workflow-evaluation Pareto chart and the companion workflow
diagram appear in the launch post.
Shows: the company's own performance framing and the decomposition of a workflow
into questions and code.
Crop: if used, retain axes, legend, comparison labels, and caption context; do
not crop away the reference-model or workflow caveats.
Decision: not used in this article. An authored comparison table and a worked
request/response explanation make the interface clearer and avoid presenting a
vendor chart as independent evidence.

Asset: the AI primer includes a diagram contrasting RLHF, RLVR, and RLCD.
Shows: TypeSafe's description of its claimed post-training objective.
Crop: retain the labels and the distinction between the training paths.
Decision: not used. The article states the distinction in prose because the
diagram is a company explanation, not an independent result.

## Discarded

URL: https://www.reddit.com/r/singularity/comments/1wiq7vn/jev_from_typesafeai_is_getting_hyped_quite_a_bit/
Reason: user discussion and enthusiasm provide no source-owned evidence for the
article's mechanism or performance.

URL: https://every.to/also-true-for-humans/mini-vibe-check-typesafe-s-jev-judged-everything-i-ve-written-in-0-7-seconds
Reason: useful anecdotal context, but the article's demonstration is not needed
to establish the API contract and its performance details are not necessary
once the official and independent integration sources are read.

URL: https://www.uol.com.br/tilt/colunas/iagora/2026/09/17/sem-chat-e-quase-sem-custos-como-e-nova-ia-feita-pelo-cocriador-do-chatgpt.ghtm
Reason: secondary reporting in Portuguese largely repeats TypeSafe's launch
claims; it adds no evidence that changes the article's interpretation.
