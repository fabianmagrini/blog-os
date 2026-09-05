# scripts/

Empty by design for the MVP (`docs/init-spec.md` §45): the initial system
runs on Markdown + YAML + AI agents invoked manually, no CLI required.

Phase 2 (`docs/init-spec.md` §46) adds automation here — a `blog` CLI
wrapping the commands described in `README.md` and `docs/init-spec.md` §34
(`blog scout`, `blog ideas`, `blog start`, `blog thesis`, `blog research`,
`blog draft`, `blog review`, `blog publish`), plus source validation and
article state-machine checks. Add scripts here only once a manual workflow
has proven itself and the automation would remove real repeated effort —
don't build the CLI ahead of the need.
