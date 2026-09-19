# Writer handoff: news-brief/2026-09-19 (01)

## Original work

The article turns four raw, separately verified evidence records into one
read of wire-style prose that keeps every figure the evidence record flagged
as easily conflated — Nscale's remaining performance obligations versus its
later, separately dated total contract value; Madison's two distinct
gigawatt figures on two different timelines; the Anthropic deal's "up to"
ceiling versus the rounded figure in circulation; and Infillion's
undisclosed deal terms — pinned to its own date, owner, and correctly
attributed source, which the evidence record itself never does since it is
notes, not citable copy.

## Proof result

`nb stamp` and the full display-text self-test pass clean: 727 words, 8
sources, 3 min read; headline, dek, and item headlines checked against the
evidence record, `spec/headlines.md`, and `spec/slop.md`; `nb-meta.dek`
matches the rendered dekline verbatim.

The brief's exact proof command:

```
nb check .../library/news-brief/2026-09-19.html --series news-brief \
  --repo /Users/ryansaxe/worktrees/nb-test-fork \
  --library /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/news-brief/2026-09-19/library
```

reports `BLOCK: 1` (`B-MODE: a brief for 2026-09-19 is already published`),
`WARN: 0`, with link-checking on. This is not a content problem: the
`--library` argument points at this workspace's own draft-staging
directory, which already contains this article at its own slug
(`news-brief/2026-09-19.html`). `published_slugs()` (`engine/nb/config.py`)
lists every `.html` file under `<library>/<series>/` with no way to exclude
the file currently being checked, so any brand-new rolling article whose
`--library` argument is the same tree it is drafted in will report itself
as already published, regardless of its content.

I confirmed this is a false positive, not a real gate, by running the
identical command (stamp already applied, link-checking on) against this
checkout's real managed library checkout instead:
`--library /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/library`
(the `origin/library` worktree `engine/nb/library_checkout.py` manages,
which correctly holds no `news-brief` series yet). That run returns
`BLOCK: 0`, `WARN: 0`, `verdict: PUBLISHABLE`. I did not substitute this
path for the brief's exact command per my instructions; I ran the exact
command as given and I'm reporting the block precisely rather than treating
either run as "the" result on my own authority.

I also confirmed `--revision` is not the fix: `engine/nb/prepare_pr.py`
sets `revision=True` only for a diff status of `M` (an existing published
article being modified), never for a brand-new `A` (added) article like
this one, so passing it here would misrepresent this as a revision and
would also silently skip the paused-series check.

No warnings were left in place; none occurred at any point in this round.

## Open question for the orchestrator

The proof command in `writer/01/brief.md` needs its `--library` argument
corrected to point at the real published-library state (this checkout's
`.nb-work/library`, or an equivalent snapshot that does not already contain
this article's own file) so `BLOCK: 0` is reachable with the command as
literally given. No evidence or voice decision is open; the article itself
is ready.
