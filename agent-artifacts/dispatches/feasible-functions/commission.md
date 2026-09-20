# Commission: dispatches/feasible-functions

## Request

Publish an article explaining exactly how Michael Hintermüller and Jianfeng Ning's paper, “Constrained Neural Parameterization for Optimization in Function Spaces,” works. The supplied starting document is the arXiv v1 paper at https://arxiv.org/abs/2606.00855 and its PDF at https://arxiv.org/pdf/2606.00855. The owner did not ask to read the article before publication, so a clean Article PR should publish automatically.

## Home and contract

Use the manual, open Dispatches series and the `article` template. Keep the article between the configured 800 and 2,500 words, with at least eight source entries if the research supports that floor. Do not change `press/` configuration. Use the existing date, harness, and model fields for 2026-09-20, Codex Work Mode, and GPT-5.

## Contribution

The article must reconstruct the method as an executable mental model. Its central claim is that CNP changes constrained function optimization by making the parameterization itself feasible: the network supplies unconstrained degrees of freedom, while geometry or scalar transforms supply the constraint. The piece must walk from the abstract map into the concrete polyhedral formula, then show how pointwise bounds and PDE constraints use the same move. It must end by separating exact feasibility from successful optimization and from the paper's empirical evidence.

## Question the article answers

How can a neural network optimize functions without repeatedly repairing infeasible outputs, and where does that guarantee stop?

## Evidence obligations

The record must establish, with locators:

- the map `T_M` has image in the admissible set and becomes dense as its parameter dimension grows;
- the Hilbert-space polyhedral decomposition into an orthogonal null space, convex combinations of vertices, and nonnegative combinations of extreme rays;
- the CNP formula's projection, simplex coefficients, and nonnegative ray coefficients, including why each term preserves feasibility and why softmax only approaches the simplex boundary;
- the smooth pointwise constructions `phi + N^2`, `phi_1 + sin^2(N)(phi_2 - phi_1)`, and the stick-breaking construction for multiple phases;
- the exact reduced neural method `u = G(y)`, including the Poisson state-constrained example and its regularity assumption;
- the singularity-enriched ansatz for re-entrant corners and the paper's numerical comparison;
- the empirical comparisons against penalty and KKT-based neural methods, preserving scope, synthetic setup, and reported metrics;
- the paper's open limits: no general convergence proof for gradient training, the need for a separable PDE relation and differentiable enough states, and the fact that complementarity orthogonality is still penalized in one experiment.

Use at least eight sources when possible. Classify the focal paper and the authors' code as primary. Use primary or official sources for PINNs, hard constraints, KKT/optimal-control neural solvers, singularity-enriched PINNs, and convex geometry. Do not treat a source as independent merely because it has a different URL.

## Angle and structure

Use a concrete headline and a plain one-sentence dek. The article should have this reasoning order:

1. Orientation: state the problem and the core feasible-by-construction map.
2. Polyhedral constraints: explain the geometric scaffold and the central CNP equation.
3. Pointwise constraints: show how squares, `sin^2`, and stick-breaking encode bounds and sums.
4. PDE-constrained optimization: derive the reduced objective by eliminating the control, then state the regularity requirement.
5. Limits and evidence: explain singularity enrichment, report the strongest numerical comparisons, and close on what the method guarantees versus what remains an optimization and generalization question.

Use one annotated equation for the central polyhedral CNP and one compact table for the constraint-to-parameterization mapping or the Example 5.1 comparison. Do not add an image unless the evidence record identifies an exact source visual whose argumentative value exceeds the prose. Do not copy the prior Jev article's opener, section-heading rhythm, note labels, code listing, pull quote, or closing pattern.

## Recent coverage to break

The only recent Dispatches article is `dispatches/jev-system-one`, “Jev Turns AI Judgment Into a Typed Software Primitive.” It opens with a product contract, uses a labeled note, then a table and a code listing, and closes with a qualified product verdict. Those choices are not this article's template. Keep this paper's argument centered on function-space geometry and use the equation as the main teaching object.

## Source set proposed for research

- Focal paper: https://arxiv.org/abs/2606.00855 and https://arxiv.org/pdf/2606.00855
- Authors' implementation: https://github.com/JianfengNing/CNP_Code
- Boyd and Vandenberghe, *Convex Optimization*: https://web.stanford.edu/~boyd/cvxbook/
- Raissi, Perdikaris, and Karniadakis, *Physics-informed neural networks*: https://doi.org/10.1016/j.jcp.2018.10.045
- Lu et al., *Physics-informed neural networks with hard constraints for inverse design*: https://arxiv.org/abs/2102.04626
- Dai et al., *Solving elliptic optimal control problems via neural networks and optimality system*: https://arxiv.org/abs/2308.11925
- Hu, Jin, and Zhou, *Solving Poisson Problems in Polygonal Domains with Singularity Enriched Physics Informed Neural Networks*: https://arxiv.org/abs/2308.16429
- Barry-Straume et al., *Physics-informed neural networks for PDE-constrained optimization and control*: https://arxiv.org/abs/2205.03377
- E and Yu, *The Deep Ritz method*: https://arxiv.org/abs/1710.00211

## Editorial boundary

Report the paper's theorems, constructions, implementation choices, and numbers as such. Mark any interpretation as analysis. Do not imply that universal approximation plus exact feasibility proves the optimizer finds a global optimum. Do not generalize the numerical examples beyond the tested functions, domains, widths, optimizers, sampling schemes, and reference methods. Explain why the method is a reparameterization of the feasible set, not a new loss that merely punishes violations.
