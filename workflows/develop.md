# Workflow: Develop

Covers turning a selected idea into an approved thesis — the first half of
Week 2 in the monthly cadence, ending at **Gate 2**.

## 1. Start the article (`blog start <idea>`)

Create `posts/active/<slug>/` (see `docs/init-spec.md` §30 for the full
per-article layout):

```text
posts/active/<slug>/
├── article.yaml       (templates/article.md schema, status: selected)
├── drafts/
├── reviews/
├── sources/
├── assets/diagrams/
├── assets/images/
└── publish/
```

Populate `article.yaml` from the idea record: `title`, `themes`, `audience`,
`created`, `target_publish_date`, `word_count_target` estimate.

## 2. Develop the thesis (`blog thesis <article>`)

Invoke the Thesis agent (`agents/thesis.md`).

- Input: the idea record, `config/audience.md`, `config/editorial-principles.md`
- Output: `posts/active/<slug>/thesis.md` (`templates/thesis.md`)
- Set `status: thesis` in `article.yaml`.

## 3. Gate 2 — Thesis approval (human)

Present the thesis to the author. The question is:

> Is this what I actually believe?

- Approved: set `thesis_approved: true`, `status: research` in
  `article.yaml`, and proceed to `workflows/research.md`.
- Not approved: revise `thesis.md` (replace, don't patch around
  disagreements) and re-present. Do not move to research on an unapproved
  thesis.

If research later (see `workflows/research.md`) undermines the thesis,
return here — re-approval is required before drafting continues.
