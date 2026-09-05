# Workflow: Research

Covers the second half of Week 2: building the research dossier for an
approved thesis.

## Precondition

`article.yaml` has `thesis_approved: true`. If not, stop and return to
`workflows/develop.md` — do not research an unapproved thesis as if it were
final.

## 1. Build the research dossier (`blog research <article>`)

Invoke the Research agent (`agents/researcher.md`).

- Input: `posts/active/<slug>/thesis.md`, `config/source-policy.md`,
  existing `knowledge/`
- Output:
  - `posts/active/<slug>/research.md` (`templates/research.md`)
  - `posts/active/<slug>/sources/sources.yaml`, one entry per source
    (`docs/init-spec.md` §15)
  - any durable findings promoted into `knowledge/concepts/`,
    `knowledge/technologies/`, or `knowledge/sources/` for reuse by future
    articles
- Set `status: outline` in `article.yaml` once the dossier covers every
  argument in the thesis, or `status: research` (unchanged) with an explicit
  note if gaps remain and more research is needed before outlining.

## Checks before moving on

- Every `factual` claim in the thesis's arguments has at least one
  supporting source, or is explicitly flagged as unsupported.
- Contrary evidence has been actively sought, not just accepted if it
  happened to surface.
- "Claims requiring author judgment" is populated, not empty by default.

## If the thesis doesn't survive research

Return to Gate 2 (`workflows/develop.md`) rather than quietly weakening the
thesis to match what the evidence actually supports.
