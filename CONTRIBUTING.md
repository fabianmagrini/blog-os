# Contributing to blog-os

This repo has one primary contributor (the author) and a set of AI agents
acting on the author's behalf. "Contributing" here mostly means: how do you
add to or move something through the pipeline.

## Adding a signal

Drop a new file in `signals/inbox/` named `signal-YYYY-MM-DD-NNN.yaml`
following `templates/signal.yaml`. It can be filled in by hand or by the
Scout agent (`agents/scout.md`). Once it has been used to generate an idea
or is no longer useful, move it to `signals/archive/`.

## Adding or updating an idea

Ideas live in `ideas/backlog.yaml` as a list following `templates/idea.yaml`.
Add new candidates at `status: backlog`. Use the Idea Agent
(`agents/editor.md` + `docs/init-spec.md` §11) to convert signals into
well-formed ideas — a topic ("agentic coding") is not an idea; a specific,
falsifiable claim ("the agent harness is becoming more important than the
model") is.

Score new ideas using the rubric in `docs/init-spec.md` §12. When an idea is
selected at Gate 1, move it (or a copy of its record) into
`ideas/shortlisted/`; rejected ideas move to `ideas/rejected/` with a short
note on why, so the same weak idea doesn't get re-proposed.

## Starting an article

Run `workflows/develop.md`. This creates
`posts/active/<slug>/` with `article.yaml` (from `templates/article.md`'s
sibling schema in `docs/init-spec.md` §31) and moves the article to
`status: selected`.

## Moving an article through the pipeline

Follow the workflow file for the stage you're on:

| Stage | Workflow |
|---|---|
| Signals → ideas | `workflows/discover.md` |
| Idea → thesis → research | `workflows/develop.md`, `workflows/research.md` |
| Outline → draft | `workflows/write.md` |
| Critique → fact-check → voice edit | `workflows/review.md` |
| Publication assets | `workflows/publish.md` |

Each workflow states which agent to invoke, what it reads, and what it must
produce before the article can move to the next `status`.

## Human Gates are not optional

Three points in every article's life require the author's explicit sign-off,
not an agent's judgment call:

1. Idea selection (is this worth saying)
2. Thesis approval (is this what I believe)
3. Publication approval (am I willing to put my name on this)

If you're an agent reading this: do not advance `status` past a gate
yourself. Present the artifact and stop.

## Style and voice

All drafting and editing should follow `config/voice-guide.md` and
`config/editorial-principles.md`. If you (human or agent) learn something
about what worked or didn't after a post goes out, update the voice guide via
the Retrospective Agent (`agents/retrospective.md`) rather than letting the
lesson live only in a chat transcript.
