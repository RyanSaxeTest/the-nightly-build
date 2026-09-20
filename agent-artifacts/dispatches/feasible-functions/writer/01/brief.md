# writer brief: dispatches/feasible-functions (01)

## Inputs

- Commission: `.nb-work/dispatches/feasible-functions/agent-artifacts/dispatches/feasible-functions/commission.md`
- Editorial direction: `.nb-work/dispatches/feasible-functions/agent-artifacts/dispatches/feasible-functions/editorial-direction.md`
- Voice guide: `.nb-work/dispatches/feasible-functions/agent-artifacts/dispatches/feasible-functions/writing-coach/01/voice-guide.md`
- Evidence record: `.nb-work/dispatches/feasible-functions/agent-artifacts/dispatches/feasible-functions/researcher/01/evidence.md`
- Template contract: `.nb-work/dispatches/feasible-functions/.nb-context/template-contract.yaml`
- Furniture and runtime contract: `.nb-work/dispatches/feasible-functions/.nb-context/furniture/engine.md`, `.nb-work/dispatches/feasible-functions/.nb-context/runtime-assets.yaml`
- Draft target: `.nb-work/dispatches/feasible-functions/library/dispatches/feasible-functions.html`

## Assignment

Write and proof a 1,800–2,300 word Dispatches article titled “This Neural Method Searches Only Feasible Functions.” Explain the focal paper as an executable mental model, in this order:

1. Start with the failure mode of an unconstrained neural output and the paper's abstract map `T_M` into the admissible set.
2. Explain the Hilbert-space polyhedral decomposition and decode the central CNP equation term by term. Use one annotated equation as the main teaching object.
3. Show the square, `sin^2`, and recursive stick-breaking maps for pointwise bounds and simplex constraints. Use one compact mapping table.
4. Derive the exact-reduced PDE method from `u = G(y)`, work through the Poisson state-bound example, and state the `H^2` regularity requirement and its limitation.
5. Close with the singularity-enriched ansatz, the strongest scoped numerical comparisons, and the difference between exact feasibility, density, and successful optimization. Include the complementarity penalty caveat.

Use 9 source entries in first-citation order: the focal paper, Raissi et al. PINNs, Boyd and Vandenberghe, the authors' code, Lu et al. hPINN, Dai et al. KKT/optimality-system solver, Hu et al. singularity-enriched PINNs, Barry-Straume et al. Control PINNs, and E/Yu Deep Ritz. Cite each section beside the claims it uses. Use `data-nb-kind="primary"` for papers, code, and the official book reference.

Do not say that the method is globally optimal, universally superior, or a generic PDE solver. Do not say that all constraints are penalty-free: Example 5.4 still penalizes complementarity orthogonality. Preserve the exact numbers in the evidence record, with the example and metric attached. Keep the prose reportorial and explanatory, with no code listing, pull quote, copied image, or Jev article structure. Use plain HTML compatible with KaTeX and the existing `nb-*` classes.

## Proof handoff

After writing, run exactly:

`/workspace/scratch/8a1899acd8af/nightly-build/nb check /workspace/scratch/8a1899acd8af/nightly-build/.nb-work/dispatches/feasible-functions/library/dispatches/feasible-functions.html --series dispatches --repo /workspace/scratch/8a1899acd8af/nightly-build`

Then run `nb stamp` on the article and repeat the proof. Report the final word count and any warnings in `draft-handoff.md` for the editor.
