# article.yaml schema

<!--
This isn't a prose template — it documents the article.yaml metadata schema
(docs/init-spec.md §31) that every posts/active/<slug>/article.yaml should
follow. Copy the YAML block below when creating a new article workspace.
-->

```yaml
id: <slug>

title:

status: idea | selected | thesis | research | outline | draft | review |
        revision | ready | published | abandoned | deferred | merged

created: YYYY-MM-DD

target_publish_date: YYYY-MM-DD

themes: []

audience: []

word_count_target:

thesis_approved: false

publication_approved: false
```

## Notes

- `status` must always be explicit and current (docs/init-spec.md §32) —
  update it as the article moves through the pipeline, and never skip a
  state without an explicit human instruction to do so.
- `thesis_approved` flips to `true` only at Gate 2.
- `publication_approved` flips to `true` only at Gate 3, and is the only
  thing that authorizes the Publisher agent to move the workspace to
  `posts/published/`.
