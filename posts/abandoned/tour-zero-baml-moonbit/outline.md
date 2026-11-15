# Outline

## Article

Three Languages Built for Coding Agents: A Tour of Zero, BAML and MoonBit

Target: about 3,500 words. Built from documentation only; nothing has been
run first-hand (see Author contributions). Section references point to
research.md claims; code samples come from "Useful examples" there.

## Structure

### Hook / Problem  (~250 words)

Coding agents mostly work through an interface built for human programmers:
files, text diffs, terminal commands and compiler messages. Ask whether that
is a compatibility layer or the long-term design, and note that three young
projects answer differently. Do not open with the projects.

- [AUTHOR EXPERIENCE] one concrete moment where the human-shaped interface
  got in an agent's way, if you have one. Otherwise open on the observation
  alone; do not invent an anecdote.

### Observation  (~200 words)

These are different bets, not three versions of one idea. Say that up front,
so the reader does not expect a feature matrix. (Argument 1; brief's
instruction not to imply they solve the same problem.)

### Thesis  (~100 words)

State the thesis plainly: Zero bets on the representation, BAML on typed agent
behavior in the language, MoonBit on the toolchain around ordinary code, and
each is best judged by what it ships today, what it assumes and what it
costs to adopt.

### How to read the tour  (~150 words)

Introduce the four questions used for each project: where does the structure
live, what does it ship today, what does it assume, what does it cost to
adopt. Also state the convention: every claim is labelled as documented,
vendor-reported, or unconfirmed, and every code sample is copied from the
project's own docs with its source and the date read. (Argument 2)

### Evidence: Tour 1 - Zero  (~600 words)

What it is: the graph is the program; `.0` text is a projection (Claim 10).
Show the hello projection, the `zero patch` form, and the hash-guarded edit,
then the `zero query` graph dump. Explain what changes for an agent: it
queries and patches nodes instead of editing lines. Explicit capabilities
(`world: World`) and explicit errors. Status: experimental, no version
shown, results of patch are narrated in the docs not captured. State what is
not claimed: the docs never say "transactional" (Claim 2).

### Evidence: Tour 2 - BAML  (~700 words)

What it is: a language where calling a model is a typed function (Claim 11).
Show the classify function, then typed errors with exhaustive `catch_all`,
`spawn`/`await`, and the TypeScript call. Explain what is language and what
would otherwise be library. Status: canary only, no stable release, v0.25.2;
testing and evals chapters unpublished; older BAML (v0) and its relationship
are unexplained (Claim 3). Label all samples canary.

### Evidence: Tour 3 - MoonBit  (~700 words)

What it is: a conventional language with a fast, integrated toolchain
(Claim 12). Show the enum and match, the test block, and the `.mbtx` script.
Cover `moon ide` as semantic navigation for agents and the skills repo. Cover
SeekMoon honestly: token/AST diff corroborated by release notes, structural
search not located, `moon prove` in a blog post but not the docs (Claim 4).
Status: v0.10.19, pre-1.0, syntax moving (derive change), docs and README
disagree on "beta-preview" versus "experimental".

### Framework or Architecture: side by side  (~250 words)

A compact table: where the structure lives, status, license/org, what is
verified versus claimed. No ranking. (Argument 3)

### Concrete Examples: could you get this today?  (~350 words)

Existing tooling already offers pieces: LSP versioned and optionally atomic
edits, ts-morph rename and find-references, the TypeScript compiler API (and
its coming TS 7.1 API change) (Claims 5, 9). Edit formats matter by model and
structured formats can hurt (Claim 6). Benchmarks do not isolate language
effects (Claim 7). Keep this short; it is context, not the point of the
article.

- [AUTHOR EXAMPLE] a small task to carry through all three, if you want a
  common thread. Without it, keep examples separate.

### Trade-offs  (~200 words)

What each bet costs: Zero asks you to give up text as the source of truth;
BAML asks you to adopt a new language and a canary toolchain; MoonBit asks
you to adopt a fast-moving language. What each buys. Be concrete and sourced.

### Counterargument  (~200 words)

The skeptic: young projects, self-reported claims, and the three are too
different for one article; a reader choosing a tool would rather compare
mature options. Give it in full, then the Response: the tour labels claimed
versus confirmed and presents case studies, not recommendations.

### Recommendation  (~150 words)

Not a winner. A reader's checklist: the four questions, plus what to verify
before trusting any language built for agents (maturity, who maintains it,
independent measurements, whether the benefit could come from tooling around
an existing language).

- [AUTHOR OPINION] either a closing verdict on which bet looks most
  promising, or a deliberately neutral ending. Decide before drafting.

### Conclusion  (~100 words)

Return to the opening observation: the interface between agents and programs
is being redesigned in at least three places at once. End on what to watch,
not a prediction.

---

## Author contributions required

- [AUTHOR EXPERIENCE] any first-hand run of Zero, BAML or MoonBit; and a
  concrete moment for the hook. Without it the tour describes documentation,
  and the draft will say so.
- [AUTHOR OPINION] verdict or neutral ending.
- [AUTHOR EXAMPLE] an optional common task to run through all three.

## Verify before publication

- Re-copy every code sample from the live page; the fetch tool dropped
  whitespace in some blocks.
- Re-check versions and dates: Zero (no version shown), BAML v0.25.2 canary
  (2026-11-06), MoonBit v0.10.19 (2026-11-05), TypeScript 7.1 API note.
- Re-check whether BAML has a stable release, whether `moon prove` appears in
  the docs, and where SeekMoon's structural search lives.
- Fact-check S2 (Zero repo) stats (stars, forks) at publication time, or drop
  them.

## Deviations from default structure

The default argument-shaped structure is mapped onto a tour: the Evidence
section holds three per-language tours, "Framework or Architecture" holds the
side-by-side comparison, and "Concrete Examples" holds the existing-tooling
comparison instead of code. Reason: this is an explainer, so the examples are
the evidence.
