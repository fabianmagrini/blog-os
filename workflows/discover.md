# Workflow: Discover

Covers Week 1 of the monthly cadence: signals → ideas → ranked backlog,
ending at **Gate 1**.

## 1. Collect signals (`blog scout`)

Invoke the Scout agent (`agents/scout.md`).

- Input: `config/themes.md`
- Output: one new file per signal in `signals/inbox/`, following
  `templates/signal.yaml`
- Target: enough fresh signals that the backlog stays healthy — the system
  should aim for 50+ captured signals across the first three months
  (`docs/init-spec.md` §49), not a one-off burst.

## 2. Generate and rank ideas (`blog ideas`)

Invoke the Editor / Idea Agent (`agents/editor.md`).

- Input: unprocessed files in `signals/inbox/`, `ideas/backlog.yaml`
- Output: new entries appended to `ideas/backlog.yaml` (`templates/idea.yaml`),
  each scored per `docs/init-spec.md` §12
- Move signals that produced an idea into `signals/archive/`, keeping a
  `related_signals`/`supporting_signals` link intact.
- Target: 5–10 serious article candidates ready for human review.

## 3. Gate 1 — Idea selection (human)

Present the ranked backlog to the author. The question is:

> Is this worth saying?

- Selected idea(s): move the record to `ideas/shortlisted/`, set
  `status: selected`, and proceed to `workflows/develop.md` to create the
  article workspace.
- Rejected ideas: move to `ideas/rejected/` with a short rejection note.
- Ideas neither selected nor rejected stay in `ideas/backlog.yaml` at
  `status: backlog` for a future cycle.

Do not proceed past this gate without an explicit human decision recorded
(who chose what, and when — a short note in the moved file is enough).
