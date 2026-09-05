# Workflow: Publish

Covers Week 4: voice edit → human review → publish → repurpose
(`blog publish <article>`).

## 1. Voice edit

Invoke the Voice Editor (`agents/voice-editor.md`) on the fact-checked
draft.

- Output: `posts/active/<slug>/drafts/final.md`
- Changes phrasing/structure/pacing only — factual meaning, thesis,
  technical conclusions, evidence, and citations must be unchanged from the
  fact-checked version.

## 2. Confirm quality gates

Before presenting to the author, confirm all of (`docs/init-spec.md` §42):

```text
✓ thesis exists and is approved
✓ research dossier exists
✓ important factual claims have sources
✓ counterargument considered
✓ technical review complete
✓ argument review complete
✓ fact check complete
✓ voice edit complete
```

If any are unmet, do not present the article as ready — say which gate is
open.

## 3. Gate 3 — Publication approval (human)

Present `drafts/final.md` to the author. The question is:

> Am I prepared to put my name on this?

- Approved: set `publication_approved: true`, `status: ready` →
  `published` in `article.yaml`.
- Not approved: capture what's blocking it and route back to the
  appropriate stage (revision, re-research, or even back to Gate 2 if the
  thesis itself is the issue).

**No publishing workflow bypasses this gate.**

## 4. Publish

Invoke the Publisher agent (`agents/publisher.md`) only after
`publication_approved: true`.

- Output into `posts/active/<slug>/publish/`: `article.md`, `article.html`,
  `metadata.yaml`, `linkedin.md`, `short-post.md`, `x-thread.md`,
  `diagram-prompts.md`, `follow-ups.md`
- Move the whole workspace from `posts/active/<slug>/` to
  `posts/published/<slug>/`.

## 5. Repurpose

The Publisher's derivative outputs (LinkedIn post, thread, diagram prompts,
follow-up ideas) are the repurposing step (`docs/init-spec.md` §25). Route
any `follow-ups.md` ideas back into `ideas/backlog.yaml` as new candidates.

## 6. Learn

Once real engagement data exists, invoke the Retrospective agent
(`agents/retrospective.md`) — see its file for inputs/outputs. This is not
required to close out publication, but should not be skipped indefinitely;
it's how `config/voice-guide.md` and the process itself improve.
