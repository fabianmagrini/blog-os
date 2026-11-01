# Thesis

## Working title

The Compiler as an API: What Zero, BAML and MoonBit Say About Languages for
Coding Agents

## Question

If AI coding agents become the primary authors of software, does the
interface between agent and compiler matter more than language syntax, and
should source text remain the source of truth?

## Thesis

The next gain for coding agents is likely to come from a structured, queryable
and checked interface to the program rather than from new syntax, and because
much of that interface can be built over existing languages, Zero, BAML and
MoonBit are best read as three experiments in where to put that structure
(the representation, the language semantics, or the tooling) rather than as
replacements for mainstream languages.

## Why now

Three projects document different answers: Zero makes a semantic graph the
program and text a projection; BAML's canary positions a language for agents;
MoonBit's SeekMoon keeps source text and adds syntax-tree search and review
tooling. Meanwhile most agents still edit text files through an interface
built for human programmers.

## Argument 1

Several agent failure modes come from the interface, not the model: fragile
text edits, context spent on search, wrong dependency assumptions, repeated
compile-and-repair loops, and merge conflicts between agents. Some of these
are limits of text; others are limits of today's harnesses, and the article
should separate the two.

## Argument 2

The three projects place structure in different layers. Zero changes the
authoritative representation (graph plus checked patches with a stale-state
hash guard); BAML changes language semantics (typed model calls, typed errors,
built-in evals); MoonBit changes tooling around conventional source
(syntax-tree search, diff review). Comparing where each puts structure is more
informative than comparing features.

## Argument 3

Compiler APIs, language servers and AST tooling already offer pieces of this
(semantic search, refactoring, impact analysis), so a transactional semantic
editing layer over an existing language such as TypeScript could capture much
of the value without a new language. Whether it does is an empirical question
the article should frame as an experiment, not answer by assertion.

## Counterargument

Agents already work well enough on text with a good harness, so the cited
failure modes are harness problems and a new representation solves a problem
that does not need a new language. A new language also has to beat TypeScript
plus mature AI libraries, and none of the three has independent evidence of
doing so.

## Response

Largely accepted, and it is part of the thesis: the claim is about the
interface, which is why it points at existing languages and why the article
treats the three projects as experiments. What it does not accept is that
text plus a better harness is obviously sufficient; that is the open
question the proposed comparison is meant to test. [AUTHOR OPINION: how
strongly you believe text will stay good enough.]

## Novel contribution

Most coverage compares languages or hypes agents. This frames the
agent-compiler interface (search, mutation, verification, policy) as the
design variable, locates three real projects on it, and ends with a testable
proposal.

## Evidence required

- Zero: documentation and repository for what is implemented, what a patch
  guarantees (atomicity, rollback, concurrency), license, maintainers.
- BAML: which canary language features are shipped versus planned, and the
  production status of the general-purpose direction.
- MoonBit/SeekMoon: what structural search and edit operations exist, and any
  independent measurement of compiler speed or agent productivity.
- Existing compiler APIs (TypeScript compiler API, LSP) and what they can and
  cannot do transactionally.
- Any published research on agent edit formats or structured editing.
- The difference between type checking, formal verification and behavioral
  correctness.

## Author input required

- [AUTHOR EXPERIENCE] a real failure of text-based agent editing, or a real
  harness you have built.
- [AUTHOR OPINION] whether source code stops being the primary interface.
- [AUTHOR EXAMPLE] the TypeScript codebase you would use for the proposed
  experiment, and whether the article proposes it or reports results.
