# Workflow: Review

Covers the rest of Week 3: independent critique, revision, and fact-check
(`blog review <article>`), moving the article to `status: revision` then
toward `ready`.

## 1. Independent critique (run in parallel, not sequentially derived)

Invoke both:

- Technical Critic (`agents/technical-critic.md`) →
  `posts/active/<slug>/reviews/technical.md`
- Argument Critic (`agents/argument-critic.md`) →
  `posts/active/<slug>/reviews/argument.md`

Neither critic should read the other's output before writing its own — the
point is independent reasoning paths (`docs/init-spec.md` §6.4).

Optional additional critics if useful: Fact Checker (can also run standalone,
see step 3), Editorial Critic, Skeptical Reader.

## 2. Revise

The Writer (or the author) revises the draft addressing:

- every "Critical issues" item from the technical review
- every item from the argument review, especially "Weakest part" and
  "Missing counterargument"

Save as the next `drafts/vN.md`. Set `status: revision`.

## 3. Fact check

Invoke the Fact Checker (`agents/fact-checker.md`) against the revised
draft.

- Output: `posts/active/<slug>/reviews/fact-check.md`
- Any high-impact claim left `UNVERIFIED` must be surfaced explicitly to the
  author — this is not resolved by the agent alone.

## 4. Re-revise if needed

If the fact check finds unsupportable claims, route back to step 2 (or to
`agents/researcher.md` if new research is needed) rather than rewording to
obscure the gap.

## Exit condition

Proceed to `workflows/publish.md` (Voice Edit → Gate 3) only once:

```text
✓ technical review has no open Critical issues
✓ argument review's Weakest part / Missing counterargument addressed
✓ fact check has no unaccepted UNVERIFIED high-impact claims
```

(Full quality gate list: `docs/init-spec.md` §42.)
