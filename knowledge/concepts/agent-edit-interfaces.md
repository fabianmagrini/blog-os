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

## Added 2026-11-07

- **Typing in the loop**: type-constrained decoding cut compilation errors by
  more than half on HumanEval/MBPP (arXiv 2504.09246); function-level, not
  agentic.
- **Language effects on agents**: SWE-bench Multilingual (one model, ~43
  tasks per group) had Rust 58%, Java 53%, JS/TS 35%, Go 31%, C/C++ 29%;
  Multi-SWE-bench (verified from its Table 4) says TS/JS lowest, but JS is
  lowest and TS's best rate (11.61) exceeds Go's (7.48) and C's (8.59), with
  large swings by agent method; TS has only 3 source repos. Benchmarks
  disagree and are confounded; do not cite as a typing effect.
- **Low-resource gap**: R and Racket lag high-resource languages
  (arXiv 2501.19085); qualitative, not about agents.
- **TypeScript**: compiler API (TS 6.0 and earlier; 7.1 will have a
  completely different API) and ts-morph provide AST edits and code fixes;
  no documented transactional semantic edits found. ts-morph has `rename`
  (across files), `findReferences`, `getDefinitions`; its docs say
  "Manipulation support is lacking" for parts of the language. tsserver's
  refactor commands remain unverified (protocol file not read).
- **SeekMoon**: the openseek `desktop` client is named SeekMoon; its
  structural search and Diff Review remain unlocated in the repo.
