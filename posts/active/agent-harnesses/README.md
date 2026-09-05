# agent-harnesses (worked example)

This article workspace exists to demonstrate the full per-article layout
(`docs/init-spec.md` §30) and to give the pipeline something concrete to run
against. It is a scaffold, not a real in-progress article:

- `article.yaml` — `status: thesis`, both gates still `false`
- `thesis.md` — a draft thesis, **not yet approved** (Gate 2 has not
  happened)
- `research.md`, `outline.md`, `drafts/`, `reviews/`, `sources/sources.yaml`,
  `publish/` — intentionally not yet populated; per the state machine
  (`docs/init-spec.md` §32) those stages come after Gate 2

To actually develop this article (or replace it with a real one): follow
`workflows/develop.md` from the thesis-review step onward, or start a fresh
idea via `workflows/discover.md` and `workflows/develop.md` for
`blog start <idea>`.
