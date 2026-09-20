## How this piece should sound

Write for a technically literate reader who can follow calculus, finite-dimensional convexity, and neural-network notation but should not have to reverse-engineer the paper's construction. Lead with the operational problem: an unconstrained network can produce a plausible-looking function that is unusable because it violates a bound, boundary condition, integral constraint, or PDE. Then make each abstraction earn its place. Introduce a symbol before using it, translate every displayed equation into an operation, and distinguish three claims that are easy to blur: the parameterization is feasible by construction; its family can be dense under stated assumptions; and an optimizer will find a good parameter choice. Use a scalar identity before the function-space construction, and use the Poisson example to show exactly where the PDE residual goes. Keep theorem, implementation detail, experiment, and caveat visibly separate. The ending should report what the numerical evidence establishes and stop short of promising global optimization or universal applicability.

The prose should be reportorial and calm: short paragraphs, concrete verbs, one conceptual turn per section, and equations used as working machinery rather than decoration. Prefer “the network can only return…” to “this elegantly guarantees…”. Name regularity and geometry assumptions at the point where they matter. Use one compact comparison table for the pointwise maps and one result table for the paper's measured errors. Do not reproduce the prior Jev article's opening, heading rhythm, pull-quote device, or conclusion pattern.

## Exemplar 1 — Chris Olah, “Understanding LSTM Networks”

Source: https://colah.github.io/posts/2015-08-Understanding-LSTMs/

Verified passages:

> “Humans don’t start their thinking from scratch every second.”

> “We’ll walk through the LSTM diagram step by step later.”

What to borrow: begin with an intuitive failure mode before introducing notation, then promise a deliberate diagram/equation walk-through. Olah repeatedly gives the reader a local reason to care about the next symbol. For this article, the analogous move is to show why penalty-after-the-fact constraints are awkward before naming the feasible set K, and to decode the CNP equation term by term rather than presenting it as a theorem-shaped block.

## Exemplar 2 — Andrej Karpathy, “A Recipe for Training Neural Networks”

Source: https://karpathy.github.io/2019/04/25/recipe/

Verified passages:

> “Don’t be a hero.”

> “complexify only one at a time”

What to borrow: use imperative checkpoints and isolate variables when explaining an experimental result. The article should tell the reader what the implementation actually changes—network output, constraint map, optimizer, or loss—before comparing numbers. It should also resist turning a small benchmark into a claim about every function-space problem. The focal paper's penalty comparison, exact-reduction examples, and singularity enrichment should be reported with their problem class and metric attached.

## Exemplar 3 — Chris Olah et al., Distill, “Attention and Augmented Recurrent Neural Networks”

Source: https://distill.pub/2016/augmented-rnns/

Verified passages:

> “The basic RNN design struggles with longer sequences”

> “the same underlying trick”

What to borrow: establish the baseline limitation, then expose the reusable mechanism behind several variants. That structure fits the CNP paper: first identify why residual penalties, multiplier networks, and post-hoc projection complicate constrained optimization; then show that one compositional pattern—projection onto the unconstrained directions plus nonnegative combinations of feasible generators—reappears across integral, pointwise, PDE, and singularity-enriched examples. Keep the common mechanism visible while marking where the assumptions change.

## Editorial checks before handoff

- Every variable in the main CNP equation is defined in the preceding sentence or its legend.
- The article says “feasible for every parameter value” only for the constraints the construction actually encodes.
- Density is stated conditionally; it is not converted into a claim that Adam finds the global optimum.
- The exact-reduction section names the regularity required to evaluate the eliminated PDE operator.
- The complementarity example is reported as a mixed result because orthogonality still uses a penalty.
- Citations sit beside the claim they support, and the sources list includes the focal paper, its code, and primary comparison papers.
