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
incomplete, the features live elsewhere, or the post overstates. A further
search of the desktop docs (UX guidelines, design notes), the desktop and
editor directory listings, and the 2026-10-10 MoonBit post "Building Agents,
MoonBit is all you need" found no mention of syntax-tree search, Token Diff,
Syntax Tree Diff or Diff Review [S21]. The only lead is an unopened
`editor/syntax` directory and a "DiffEditor" facade, both unconfirmed. Do not
describe the structural search as available until verified in the code.

Update 2026-11-07: a second look found that `moonbitlang/openseek/desktop`
is itself titled "SeekMoon" ("a Proton + Rabbita desktop client for the
OpenSeek agent, written in MoonBit"), so SeekMoon is the desktop client over
the OpenSeek agent. Its README still does not mention syntax-tree search,
Token/Syntax Tree Diff or Diff Review, and the post names no package or
command for them [S7, S19]. The `editor/` README mentions a "DiffEditor"
facade, an unconfirmed lead. Docs/ files and the 2026-10-10 MoonBit blog post
were not read.

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

# Claim 7

A language's properties (static typing, diagnostics) change coding-agent
success, so the feedback loop matters more than syntax. (interpretive; load-
bearing for the broadened thesis, Argument 1)

## Supporting evidence

Type-constrained decoding (Mündler, He, Wang, Sen, Song, Vechev; arXiv
2504.09246, submitted 2025-04-12) uses a language's type system to steer
generation and, per its abstract, "reduces compilation errors by more than
half and significantly increases functional correctness in code synthesis,
translation, and repair tasks across LLMs of various sizes and model
families", formalized on a simply-typed language and extended to TypeScript
[S12]. This is direct evidence that putting static checking in the loop
helps model output.

## Contrary evidence

The paper evaluates on HumanEval and MBPP (function-level tasks), not
repository-level agent work, and the abstract gives no exact figures or
whether the TypeScript experiments used those benchmarks [S12].
Multilingual agent benchmarks do not show a clean typing effect. In SWE-bench
Multilingual (300 tasks, 42 repos, one model, SWE-agent with Claude 3.7
Sonnet, ~42-44 tasks per language group), resolution rates were: Rust 58.14%,
Java 53.49%, PHP 48.84%, Ruby 43.18%, JS/TS 34.88%, Go 30.95%, C/C++ 28.57%
[S13]. A different benchmark, Multi-SWE-bench (ByteDance Seed, arXiv
2504.02605; 1,632 instances from 39 repositories, 7 languages; 9 models x 3
agent methods), was read from the paper's HTML (Table 4). The authors write
that "TS and JS consistently yield the lowest resolved rates", attributing it
to "dynamic typing, asynchronous execution, and diverse runtime behaviors"
and, for C, C++, Rust and Go, to manual memory management, "complex build
systems, and intricate type systems" [S14]. The best resolved rates in the
table are Python 52.20, Java 23.44, Rust 15.90, C++ 14.73, TS 11.61, C 8.59,
Go 7.48 and JS 5.06 [S14].

Reading the table against that statement (my observation, not the authors'):
JS is lowest, but TypeScript's best rate (11.61, and 11.16 for another
method) is higher than Go's and C's best, and TS swings widely for the same
model: Claude 3.7 Sonnet scores 11.16 under one agent method and 2.23 under
another [S14]. Instance counts per language are uneven and come from few
repositories: TypeScript 224 instances from 3 repositories, Go 428 from 3,
JavaScript 356 from 6, Rust 239 from 10, Java 128 from 9 [S14]. TypeScript is
statically typed, so the authors' "dynamic typing" explanation fits JS better
than TS. The authors also list "intricate type systems" as a source of
difficulty for other languages, which is not what a simple "static typing
helps agents" story predicts.

## Assessment

Static checking in the generation loop helps in the one controlled study
found. Cross-language benchmark results are confounded by repository, task
mix and model, rely on small per-language counts, and the two benchmarks
disagree on which languages are hard. They do not isolate language
properties. The article may claim a plausible link and cite the decoding
result, but must not say benchmarks show typed languages do better.

## Confidence

Medium (type checking helps generation), Low (language properties explain
cross-language agent differences; the two benchmarks disagree, results are
repo-confounded, and even the authors' own table only partly matches their
"TS and JS lowest" statement)

---

# Claim 8

Training-data and ecosystem scarcity lowers model performance for a
language, which favors incumbents. (factual, for low-resource languages)

## Supporting evidence

Giagnorio, Martin-Lopez and Bavota (ICPC 2025, arXiv 2501.19085) studied R
and Racket with six LLMs and report poorer code generation than for high-
resource languages, with the best remedy depending on model size: fine-
tuning usually best for smaller models, in-context learning increasingly
effective for larger ones, and fine-tuning very large models can hurt [S15].

## Contrary evidence

The abstract describes the gap only qualitatively, with no numbers or model
names on the page [S15]. It concerns two low-resource languages and
code-generation tasks, not coding agents, and not languages as new as Zero,
BAML or MoonBit. Larger models and in-context learning narrow the gap.

## Assessment

Supports the direction of the incumbency argument for low-resource
languages in general. It does not measure how a brand-new language fares with
current frontier models or agents, so keep that part of Argument 3 as an
inference.

## Confidence

Medium (low-resource gap exists), Low (applies to new agent-oriented languages)

---

# Claim 9

TypeScript's compiler and tooling already provide a transactional semantic
editing layer. (factual; tests thesis Argument 3)

## Supporting evidence

The compiler API exposes program creation, diagnostics, a type checker
(`getSymbolAtLocation`, `getTypeAtLocation`), AST construction through
`ts.factory`, a printer, and a language service with semantic diagnostics
and per-file `version` tracking [S16]. ts-morph adds node manipulation
(`replaceWithText`, `addStatements`, `removeStatement`), code fixes
(`organizeImports`, `fixMissingImports`, `fixUnusedIdentifiers`), and
batches file-system changes until `project.save()`, noting that on a
mid-run error "the files won't be in a halfway state" [S17].

## Contrary evidence

The compiler API page covers TypeScript 6.0 and earlier and says "TypeScript
7.1 will have a completely different API" [S16], a stability risk for any
layer built on it. Neither source documents atomic or versioned multi-file
semantic edits; the ts-morph save batching is advice, not a documented
transaction guarantee [S17]. Follow-up reading found that ts-morph does provide
`rename` ("rename all usages ... across all files", with `renameInComments`
and `renameInStrings` options), `findReferences()` and `getDefinitions()`
[S20]. But its docs describe no refactor or code-action API beyond the code
fixes noted above, expose the language service only as `compilerObject`
("Generally you won't need to use the language service"), call AST transforms
"not a typical scenario", and say "Manipulation support is lacking" for parts
of the language [S20]. The tsserver wiki page names only `open`, `quickinfo`,
`completions` and `geterr` [S18]; the protocol file that would list the edit
commands could not be read (the URL tried returned 404), so tsserver's
refactor and code-action commands, and any version or batching semantics,
remain unverified.

## Assessment

Parts of the interface clearly exist (types, diagnostics, AST edits, rename
and find-references through ts-morph, code fixes), but a transactional, versioned semantic edit layer for TypeScript is
not established by these sources, and the compiler API is about to change.
Argument 3 should say "partly available, with gaps", and the experiment's
purpose is to find the gaps.

## Confidence

Medium (pieces exist), Low (that they compose into a checked transaction)

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
- What do tsserver and the language service expose for rename, references
  and refactor edits? (Partly answered in Claim 9: not found on the pages read.)
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
