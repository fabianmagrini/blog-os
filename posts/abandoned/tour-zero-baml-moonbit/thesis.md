<!--
Revised 2026-11-07 at the author's request, second time: from an argument
about languages for coding agents in general (approved at Gate 2, commit
3d66210) to an explainer and tour of Zero, BAML and MoonBit. Earlier
versions are in git history (130183a, 3d66210). This version has NOT been
approved; thesis_approved is false in article.yaml.
-->

# Thesis

## Working title

Three Languages Built for Coding Agents: A Tour of Zero, BAML and MoonBit

## Question

What are Zero, BAML and MoonBit, how does each one work, and what should a
reader make of them?

## Thesis

Zero, BAML and MoonBit are not three competitors but three different bets on
how a language should serve coding agents (Zero on the program
representation, BAML on typed agent behavior inside the language, MoonBit on
the toolchain around ordinary source code), and each is easiest to judge by
what it ships today, what it assumes, and what it costs to adopt.

## Why now

All three have recently documented what they offer to agents: Zero's graph
architecture and checked patches, BAML's canary "language for agents", and
MoonBit's SeekMoon agent environment. They are new, claims are mostly the
projects' own, and readers are being asked whether any of it matters before
independent evidence exists.

## Argument 1

Each project puts structure in a different place. Zero makes a semantic graph
the program and text a projection; BAML puts typed model calls, typed errors
and evals into the language; MoonBit keeps conventional source and builds the
tooling, tests and agent environment around it. A tour should show what a
developer or an agent actually does in each, with real examples, because the
difference is easier to see than to describe.

## Argument 2

They sit at very different maturity levels, and the tour must say so for each:
Zero describes itself as experimental; BAML's general-purpose direction is
claimed in a canary README whose shipped status is unconfirmed; MoonBit is the
most conventional but its agent-environment features (syntax-tree search, diff
review) are described in a vendor post that I could not match to the
repository. Readers need the claimed-versus-confirmed line drawn for each.

## Argument 3

The useful takeaway is a set of questions rather than a ranking: where does
the structure live, what does it guarantee, what does it cost to adopt, and
could the same benefit come from tooling around an existing language? The
article closes with those questions and a note on what existing languages
already offer, rather than declaring a winner or a new paradigm.

## Counterargument

These are young projects with mostly self-reported claims, so a tour risks
promoting hype, and the three are too different to sit in one article. A
reader who wants to choose a tool for agents is better served by a comparison
of mature options.

## Response

The tour is explicit about what is claimed versus confirmed, treats them as
case studies and not recommendations, and says plainly that they solve
different problems. The thesis itself is that they are different bets, which
is why they are toured together. [AUTHOR OPINION: whether you want a closing
view on which bet looks most promising, or a deliberately neutral ending.]

## Novel contribution

A grounded walk through three newly documented projects with real examples
and an honest maturity assessment for each, plus a transferable set of
questions, instead of marketing summaries or a feature table.

## Evidence required

- Zero: real command and `.0` projection examples, install and status,
  licensing (partly gathered; examples not yet captured).
- BAML: real function, type, error and test examples from the docs, and what
  is stable versus canary (partly gathered; examples not yet captured).
- MoonBit: the language itself (syntax, type system, tooling, version,
  governance), none of which has been researched yet; only SeekMoon has.
- SeekMoon: where structural search and diff review are implemented, or
  confirmation they are not shipped.
- Do not invent code. Every code sample must come from official docs or
  repositories and be attributed.
- Background already gathered on edit formats, LSP, TypeScript tooling and
  benchmarks (research.md Claims 5-9).

## Author input required

- [AUTHOR EXPERIENCE] whether you have actually run any of the three; a
  first-hand try of each would make the tour much stronger, and I will not
  write as if I had.
- [AUTHOR OPINION] a closing verdict or a neutral ending.
- [AUTHOR EXAMPLE] a small task to use as the common walk-through across all
  three, if you want one.
