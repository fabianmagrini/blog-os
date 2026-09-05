# Workflow: Write

Covers the start of Week 3: outline → first draft.

## 1. Outline (part of `blog draft <article>`)

Invoke the Outliner agent (`agents/outliner.md`).

- Input: `thesis.md`, `research.md`, `config/audience.md`
- Output: `posts/active/<slug>/outline.md` (`templates/outline.md`),
  including explicit `[AUTHOR EXPERIENCE]` / `[AUTHOR OPINION]` /
  `[AUTHOR EXAMPLE]` markers
- Set `status: draft` once the outline is in place.

## 2. First draft (`blog draft <article>`)

Invoke the Writer agent (`agents/writer.md`).

- Input (minimum context, `docs/init-spec.md` §36): `config/audience.md`,
  `config/voice-guide.md`, `thesis.md`, `research.md`, `outline.md`
- Output: `posts/active/<slug>/drafts/v1.md`
- The Writer must not resolve `[AUTHOR ...]` markers itself — leave them as
  placeholders if the author hasn't supplied that content.

## 3. Author fills in author-only content

Before critique, the author should fill in any `[AUTHOR EXPERIENCE]`,
`[AUTHOR OPINION]`, or `[AUTHOR EXAMPLE]` markers directly in the draft
(or explicitly defer specific ones, noting that they'll remain gaps into
critique).

## Next

Proceed to `workflows/review.md` once a complete `v1.md` (or later
revision) exists with the argument fully drafted, even if some author
markers are still open.
