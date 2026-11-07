<!--
Revised 2026-11-07 at the author's request: broadened from "the compiler as
an API, read through Zero, BAML and MoonBit" to the general question of what
a language and toolchain should look like for coding agents. The earlier
thesis (approved at Gate 2) is in git history (commit 130183a). This version
has NOT been approved; thesis_approved is false in article.yaml.
-->

# Thesis

## Working title

Languages for Coding Agents: Where Should the Structure Live?

## Question

If AI agents write much of our software, what makes a programming language
and its toolchain good for them, and does that require new languages or
better tooling around the ones we have?

## Thesis

What makes a language work well for a coding agent is mostly the quality of
its feedback and editing loop (static checking, fast structured diagnostics,
queryable program structure, checked edits) rather than its syntax, and since
existing languages can acquire most of that loop through tooling, new
agent-oriented languages such as Zero, BAML and MoonBit should be read as
probes into which parts of it need language-level change rather than as
replacements for mainstream languages.

## Why now

Agents already write and modify real code in languages designed for humans,
through an interface of files, text diffs and compiler messages. At the same
time, projects are trying different answers: Zero makes a semantic graph the
program, BAML's canary targets a language for agents, and MoonBit's SeekMoon
adds syntax-aware search and review around conventional source.

## Argument 1

An agent's results depend heavily on its feedback loop: whether the language
catches errors statically, how fast and structured the diagnostics are, how
well it can find what to change, and how safely it can make the change. Some
agent failures come from text editing and context cost; others come from
today's harnesses. The article should separate these, because only the first
kind argues for changing the language or representation.

## Argument 2

There are three places to put structure for agents: the representation (Zero's
graph and checked patches), the language semantics (BAML's typed model calls
and errors), and the tooling around ordinary source (MoonBit's
syntax-tree search and review). Existing languages mostly sit in the third.
Naming the layer makes the trade-offs comparable: each step toward the
representation buys stronger guarantees and costs compatibility.

## Argument 3

Incumbent languages have a structural advantage that new ones must overcome:
existing code, libraries, human reviewers, and presumably more training data
for models. Compiler APIs, language servers (which already support versioned,
optionally atomic edits) and AST tooling cover part of the proposed
interface, so the practical path is likely evolution of existing languages'
tooling. Whether that captures most of the value is an empirical question the
article should frame as an experiment.

## Counterargument

Agents already do well on plain text with a good harness, so the cited failure
modes are harness problems and no new language or representation is needed.
Structure can also hurt: early edit-format results suggested complex formats
made some models write worse code. And a new language must beat TypeScript
plus mature libraries, with no independent evidence yet that any of the three
does.

## Response

Largely accepted and built into the thesis: the claim is about the feedback
and editing loop, which is why it points at tooling for existing languages and
treats the new languages as probes. What it does not accept is that text plus a
better harness is obviously enough; that is the open question the proposed
comparison is meant to test. [AUTHOR OPINION: how strongly you believe text
will stay good enough.]

## Novel contribution

Most coverage either compares languages or celebrates agents. This frames
language design for agents around the feedback and editing loop, places real
projects on a three-layer map of where structure can live, takes the
incumbency advantage seriously, and ends with a testable proposal.

## Evidence required

- What Zero, BAML and MoonBit actually implement (partly gathered; see
  research.md).
- Evidence that language properties (static typing, diagnostics quality)
  change agent success, ideally cross-language benchmarks. Not yet sourced.
- Evidence on training-data or ecosystem effects on agent performance by
  language. Not yet sourced; currently an assumption.
- Existing compiler and language-server capabilities for semantic edits
  (LSP partly gathered; TypeScript unverified).
- Research on agent edit formats and structured editing (partly gathered).
- The difference between type checking, formal verification and behavioral
  correctness.

## Author input required

- [AUTHOR EXPERIENCE] a real failure of text-based agent editing, or a real
  harness you have built.
- [AUTHOR OPINION] whether source code stops being the primary interface.
- [AUTHOR EXAMPLE] the codebase you would use for the proposed experiment,
  and whether the article proposes it or reports results.
