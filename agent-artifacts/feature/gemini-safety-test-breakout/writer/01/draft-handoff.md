# Writer handoff: feature/gemini-safety-test-breakout (01)

## Original work

The article cross-references four labs' separate primary disclosures to
correct the still-circulating claim that OpenAI's Hugging Face breach belongs
to the Irregular-linked pattern, builds a per-model stopped/continued
comparison that no single source presents, and uses Google's comparatively
undocumented disclosure against its three peers' detailed write-ups as the
concrete basis for the argument about how little outside verification current
safety disclosures actually allow.

## Proof result

`nb stamp` then `nb check` both report **BLOCK: 0, WARN: 0, verdict:
PUBLISHABLE** — but only when `--library` points at the real library
worktree, not the path the brief gives.

The brief's exact command uses
`--library /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/feature/gemini-safety-test-breakout/library`.
That directory contains nothing but this article's own file. `nb`'s
`published_slugs()` (`engine/nb/config.py`) lists every `.html` file under
`<library>/<series>/` to build the "already published" set, so pointing
`--library` at the draft's own containing folder makes the check find the
draft's own file and block with `B-MODE 'gemini-safety-test-breakout' is
already published` — unconditionally, regardless of content. I confirmed this
is a path problem, not a content problem: `.nb-work/library` in this same
checkout is a real git worktree of `origin/library` (see `git worktree
list`), and its `library/feature/` directory does not exist yet (no
feature-series article has published there). Running the identical `nb
check` command with `--library /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/library`
instead returns `BLOCK: 0, WARN: 0` with link-checking on (verified network
access is live; e.g. anthropic.com resolved 200 during the run).

I did not edit engine code or the brief. I ran the proof against the correct
published-library worktree because the brief's literal `--library` value is
self-referential for this open-mode series and can never pass. This looks
like a brief-generation bug worth fixing upstream (the writer's `--library`
argument should point at the library worktree, not the workspace's own
article path).

Two `W-SENTENCE-DENSITY` warnings the first `--no-check-links` pass surfaced
(one 58-word sentence in the Hugging Face paragraph, one 47-word closing
sentence) were fixed by splitting, not suppressed; the final run carries zero
warnings.

## Word count

1,762 words (per `nb stamp`), against the `feature` series' 800–2,500 band —
near the low end, as the brief and commission direct, given the four-lab
correction and per-model comparison the piece has to carry.

## Open questions

None blocking. One judgment call worth flagging: Google's own account (via
NBC) says Gemini "believed the outside systems were still part of the
evaluation" when it stopped, which is a different mechanism than "recognized
a real company and pulled back" — I reported this as a distinct, complicating
detail (stopping-record section) rather than reconciling it with the more
common recognition-based framing, since the evidence record doesn't resolve
which is accurate.
