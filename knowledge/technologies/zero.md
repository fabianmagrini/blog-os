# Zero (programming language)

Graph-native language from Vercel Labs (vercel-labs/zerolang, Apache-2.0,
marked experimental). The semantic graph is the program ("the program
database"); `.0` text is a reviewable projection. `zero patch` applies edits
to graph nodes with an expected value and `--expect-graph-hash` stale-state
guard; invalid shape, type or stale state fails before the store is written.
Atomicity, rollback and concurrent-edit behavior are undocumented as of
2026-11-01; the docs do not say "transactional".

Sources: https://zerolang.ai/concepts/graph-architecture ,
https://github.com/vercel-labs/zerolang

Added 2026-11-07: install `curl -fsSL https://zerolang.ai/install.sh | bash`;
docs say "Experimental ... Expect breaking changes"; no version number shown.
Explicit capabilities (`world: World`), explicit errors (`raises`, `check`),
no hidden exceptions. `zero patch` also supports `--check-only` and
`--dry-run`. Patch results are narrated in the docs, not captured.
