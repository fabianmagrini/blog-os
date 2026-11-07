# Interfaces between coding agents and programs

- **Text edit formats**: whole-file, search/replace, udiff. Diff-XYZ (arXiv
  2510.12487) found search-replace best for larger models; smaller open
  models gained little from any format. Early Aider results (GPT-3.5/4 era,
  unverified here) suggested complex formats can hurt.
- **LSP 3.17**: WorkspaceEdit with optional `transactional` failure handling
  and versioned text document edits (stale-edit protection). Client-dependent.
- **Graph-native (Zero)**: checked structural patches over a semantic graph,
  stale-hash guard, text as projection. Experimental.
- **Language-level (BAML canary)**: typed model calls, typed errors, evals.
  Shipped status unconfirmed.
- **Tooling-level (MoonBit SeekMoon)**: syntax-tree search and diff review
  per vendor post; not confirmed in the linked repository.

See `posts/active/languages-for-coding-agents/sources/sources.yaml`.
