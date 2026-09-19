# writer brief: news-brief/2026-09-19 (01)

Inputs: `agent-artifacts/news-brief/2026-09-19/commission.md`
Inputs: `agent-artifacts/news-brief/2026-09-19/editorial-direction.md`
Inputs: `agent-artifacts/news-brief/2026-09-19/writing-coach/01/voice-guide.md`
Inputs: `agent-artifacts/news-brief/2026-09-19/researcher/01/evidence.md`
Inputs: `agent-artifacts/news-brief/2026-09-19/researcher/02/evidence.md` (the
        complete, current evidence record: carries forward round 01's two
        verified items and adds two more, for four total)
Inputs: `.nb-context/template-contract.yaml`
Inputs: `.nb-context/furniture/engine.md`
Article: `library/news-brief/2026-09-19.html`
Output: `agent-artifacts/news-brief/2026-09-19/writer/01/draft-handoff.md`
Proof:  /Users/ryansaxe/worktrees/nb-test-fork/nb check /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/news-brief/2026-09-19/library/news-brief/2026-09-19.html --series news-brief --repo /Users/ryansaxe/worktrees/nb-test-fork --library /Users/ryansaxe/worktrees/nb-test-fork/.nb-work/news-brief/2026-09-19/library

Write exactly 4 items, in this order: the NASA/SpaceX contract modification,
the Nscale IPO filing, the Infillion/Foursquare acquisition, and the
EQT/Madison Energy Infrastructure battery initiative. The evidence record's
own Contradictions section flags several figures that recur incorrectly in
secondary coverage; use the corrected figure in each case:

- SpaceX: $946 million (not CNBC's own headline figure of $950 million,
  which its own body contradicts).
- Nscale: the $56.4 billion remaining-performance-obligations figure is
  dated June 30, 2026; the $103.4 billion active-and-contracted total
  contract value is a separate, later-dated (August 31, 2026) figure. Do not
  merge them into one number. The Anthropic deal ceiling is "up to
  approximately $44.6 billion," not the "~$45 billion" some coverage rounds
  to.
- Infillion/Foursquare: no purchase price or closing date exists on the
  record; do not imply one. Attribute the 150/650 employee counts and the
  20-25% revenue/headcount projection to Axios's reporting specifically, not
  to Infillion's own release, since that release does not contain them.
- EQT/Madison: the release states two distinct "1 gigawatt" figures on two
  different timelines (an existing portfolio nearing 1 GW by fall 2026, and
  a separate new target of 1 additional GW by 2028 backed by up to $2
  billion). Keep them distinct. The $2 billion is a phased target through
  2028, not a committed spend.

Each item stands alone per `templates/brief/identity.md`: give the
development and the number or caveat the headline dropped, cite a primary
source over any coverage, and do not close an item on a line handing the
point back to the reader.
