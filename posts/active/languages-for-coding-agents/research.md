# Research Dossier

> **Revision note (2026-11-07):** the thesis was broadened to the general
> question of languages for coding agents and is awaiting re-approval. The
> claims below remain valid as evidence about three case studies and the
> surrounding tooling. New evidence needed for the broader frame is listed
> under "Open questions" (language-level effects on agent performance;
> training-data and ecosystem effects).


## Article

Languages for Coding Agents: Where Should the Structure Live?

## Thesis

The next gain for coding agents is likely to come from a structured, queryable
and checked interface to the program rather than from new syntax, and because
much of that interface can be built over existing languages, Zero, BAML and
MoonBit are best read as three experiments in where to put that structure
(the representation, the language semantics, or the tooling) rather than as
replacements for mainstream languages.

---

# Claim 1

Zero makes a semantic graph the authoritative program representation, with
text as a reviewable projection, and ships checked structural patches.
(factual)

## Supporting evidence

The docs state "the graph is the program database"; `.0` text files are
review views that `zero import` can rebuild from [S1]. The README's "What
Exists Today" lists `zero.graph` as compiler input, `.0` projections, `zero
patch`, `zero query/inspect/check/test/run`, and `zero import/export` [S2].
Patches name a node, an expected value and a new value, and carry an
`--expect-graph-hash` stale-state guard; shape, edge, type-fact and hash
checks run before the package becomes compiler input [S1].

## Contrary evidence

The README labels the project a "Vercel Labs Experiment" and warns that it
is "experimental", with breaking changes and security issues expected [S2].
No version number is shown [S2].

## Assessment

Implemented as described, but experimental. Apache-2.0, owned by Vercel Labs
(5.4k stars, 1,188 commits at time of reading); individual maintainers are
not named on the page [S2].

## Confidence

High (design and existence), Low (production readiness)

---

# Claim 2

Zero's patch operations are "transactional" in the sense the brief assumes
(atomic, rollback-safe, safe under concurrent edits). (factual)

## Supporting evidence

The README says stale hashes, unexpected field values, invalid shapes and
type errors "fail before the store is written" [S2], which implies
validate-then-write.

## Contrary evidence

Neither source describes atomicity, rollback or concurrent-edit behavior,
and the docs do not use the word "transactional" [S1, S2]. A stale-hash
check detects a concurrent change; it does not by itself say what happens to
two agents editing at once.

## Assessment

Not supported. The article may say Zero validates a patch before writing and
rejects stale state; it must not say transactional or imply multi-agent
safety without reading the implementation.

## Confidence

High (that it is unsupported by these sources), Low (about the actual behavior)

---

# Claim 3

BAML is moving from a DSL for typed model calls to a general programming
language for agents, and the new language is shipped. (factual)

## Supporting evidence

The main docs describe typed functions that call models, plus general
computation, errors and concurrency, run via CLI or generated SDKs
(TypeScript listed) [S3]. The canary README calls BAML "the programming
language for agents" with TypeScript-like syntax, Rust-like types, typed
errors, green threads, a built-in test/eval framework, an agent standard
library, and incremental adoption from TypeScript, Python, Go, C# and Java
[S4]. The repo has a `baml_language` directory [S5].

## Contrary evidence

The docs make no general-purpose claim and give no stability labels beyond
"Install Canary" [S3]. The README gives no stability caveats and states
features in the present tense; its compile-speed-versus-Go claim has no
benchmark [S4]. The repo page shows no releases and does not say whether
canary or `baml_language` is released [S5].

## Assessment

The direction is claimed, but "shipped" is unproven. Describe the canary as
the project's stated goal. Apache-2.0; BoundaryML; 9.5k stars [S5].

## Confidence

High (what is claimed), Low (that it is implemented and stable)

---

# Claim 4

MoonBit's SeekMoon provides syntax-tree search and syntax-aware diff review
for agent-written code. (factual)

## Supporting evidence

The 2026-09-01 post describes syntax-tree search with placeholders (an
example found 43 matches in the `core` project), results added to agent
context, and Diff Review with line, token and syntax-tree views plus
go-to-definition and find-references. It states a task is complete only when
the developer understands and accepts the code [S6]. The post links to
`moonbitlang/openseek` as the place to explore and build it [S6].

## Contrary evidence

That repository's README describes a "DeepSeek-backed MoonBit coding agent"
with a headless CLI, TUI, MCP server, skills and a compiler-grounded review
engine, and never mentions SeekMoon, structural search or diff review. No
release or version is listed [S7].

## Assessment

Unresolved. The shipped features are reported by the vendor's post but not
confirmed by the linked repository's README. Either the README is
incomplete, the features live elsewhere, or the post overstates. Do not
describe the structural search as available until verified in the code.

## Confidence

Medium (post describes it), Low (that it matches the repository)

---

# Claim 5

Much of the proposed interface already exists in standard tooling. LSP
provides versioned and optionally atomic workspace edits. (factual)

## Supporting evidence

LSP 3.17: a `WorkspaceEdit` can carry text edits and file operations; with
`failureHandling: transactional` the operations "either all succeed or no
changes at all are applied"; text document edits can carry a document version
that clients check before applying; servers can advertise code actions and
`referencesProvider`; rename and call hierarchy requests are listed [S8].

## Contrary evidence

Atomicity depends on the client's `failureHandling` setting; `abort` and
`undo` are weaker [S8]. I could not verify what the TypeScript language
service or compiler API expose: the wiki page fetched covers diagnostics and
incremental snapshots only, not rename, refactors or edit objects [S11].

## Assessment

LSP supports the stale-edit and transactional ideas on paper, which backs
Argument 3. Whether TypeScript's tooling can serve as the semantic editing
layer is unverified and needs the TypeScript API reference.

## Confidence

High (LSP), Low (TypeScript specifically)

---

# Claim 6

Agent edit failures depend heavily on edit format and model, so some are
harness limits rather than limits of text. (interpretive)

## Supporting evidence

Aider documents several edit formats (whole-file, search/replace diff,
fenced, udiff) and says different models work better with different ones
[S9]. The Diff-XYZ benchmark (arXiv 2510.12487, v2 2025-11-17) found the
best format depends on use case and model size: search-replace performed best
for larger models across most tasks, structured udiff variants were similar
but slightly worse, and smaller open models gained little from any format
[S10].

## Contrary evidence

Aider's early GPT-3.5/GPT-4 benchmark, via a search summary I did not read on
the page, found whole-file output most reliable, function-call-based edits
worse, and said complex edit formats can make models write worse code and
fail at formatting [S9]. That cuts against the idea that more structured
interfaces help, at least for those models. Those results are old and may not
transfer to current models.

## Assessment

Supports separating "text is the problem" from "the harness is the problem",
and warns that structure is not automatically better. The article must
acknowledge this as the strongest evidence against the thesis's direction.

## Confidence

Medium

---

# Useful examples

- Zero's patch example: node reference, `expect` value, new value, graph
  hash; rejected if any no longer match [S1].
- SeekMoon's 43-match structural search in `core` [S6], pending the
  verification in Claim 4.
- LSP `TextDocumentEdit` version checking as the existing analogue of Zero's
  stale-hash guard [S8].

# Useful quotes

- "the graph is the program database" (Zero docs) [S1]
- "fail before the store is written" (Zero README) [S2]

# Open questions

- (Added with the broader thesis) Is there evidence that language properties
  such as static typing or diagnostic quality change agent success rates?
- (Added) Is there evidence that training-data volume or ecosystem size
  affects agent performance by language? Currently an assumption.
- What does Zero's patch guarantee under concurrent edits, and is it atomic?
  Read the implementation or ask the maintainers.
- Is the BAML canary language released, and which features are implemented?
- Where do SeekMoon's structural search and diff review actually live?
- What do the TypeScript compiler API and tsserver expose for semantic edits?
- No independent measurement of compiler speed or agent productivity for any
  of the three. This is the main evidence gap.
- The distinction between type checking, formal verification and behavioral
  correctness was not researched yet.
- No research found on graph-native or structure-editing representations for
  agents.
- Maintainer identity and governance for BAML and MoonBit were not checked.

# Claims requiring author judgment

- How strongly text stays "good enough" (thesis Response).
- Whether the article proposes the TypeScript experiment or reports results.
- How much weight to give the Aider evidence that structure can hurt.
