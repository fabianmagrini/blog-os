<!--
Revised 2026-11-21 at the author's direction after the critics' review
(reviews/argument.md, reviews/technical.md). The author chose the "narrow to
form and authority" option, which counts as re-approval. Previous theses are
in git history: the "two kinds" thesis (dfc72cb) and the "three jobs, boundary
not the model" thesis (e47cbfd).

Why: the causal clause "the boundary, not the model, settles reliability" was
asserted, not argued, and the draft's own evidence showed boundaries limit
form and authority, not content. A test for content-level controls found one
partial counterexample (A2UI's offline eval framework), which shaped the
wording below.
-->

# Thesis

## Working title

What the Boundary Doesn't Check: Generative UI After A2UI 1.0

## Question

As A2UI 1.0 and libraries such as Vercel Labs' UI SDK arrive, what do the
controls around an agent and an interface actually constrain, and what do they
leave open?

## Thesis

Every runtime control the field currently offers around an agent and an
interface (a component catalog, a sandbox, a permission layer) limits what the
agent can show or do, not whether what it shows is correct. In the documents
read, whether the content is right is left to offline evaluation and to checks
the developer writes, so the reliability work that matters sits outside the
boundary.

## Why now

A2UI 1.0 (announced 2026-11-11) and UI SDK (introduced 2026-11-12) arrived
together with json-render, assistant-ui, Tambo, the Vercel AI SDK, AG-UI and
MCP Apps, and each describes some control as the safety story. Readers are
being asked to rely on those controls before there is independent evidence of
what they cover.

## Argument 1

There are different controls for different ways an agent meets an interface,
and each limits form or authority. An agent generating UI from a catalog is
bounded by the catalog and function permissions (A2UI, json-render,
assistant-ui, Tambo). An agent triggering a developer-shipped UI is bounded by
a sandbox and a content security policy (MCP Apps). An agent operating
components that already exist is bounded by a permission layer (UI SDK's
bridge). An agent writing the code is bounded by tests and review (UI SDK's
skill). The split is a supporting map, not the claim, and two of the four cases
rest on a single vendor's documentation.

## Argument 2

The documents say where content is left open. A2UI's pages describe no
semantic check on what an agent puts into a registered component, and its docs
say the data model can be updated by the language model. UI SDK's own docs
state what its `allow` callback covers (actions) and does not (visibility of
unmarked components). json-render's docs for its experimental composer say
completion "is not a correctness guarantee" and that registering an action
does not make it safe to run with arbitrary values. Checks that run on values
(A2UI's `@checks`, `regex`, `required`) are documented for user input. The
closest documented content control is A2UI's eval framework, an LLM judge that
grades payloads against a rubric, and it runs offline on the project's datasets.

## Argument 3

Boundary and model are not separable, so "boundary versus model" is a false
choice. A catalog is also a prompt: json-render's catalog carries
descriptions the model reads. A boundary caps the worst case (what can appear
or happen); the model and any content checks set the typical case (whether the
choice and the values are right). Vendors' claims about what a boundary
guarantees can also outrun their own documents, as with A2UI's claim that
"sensitive values never reach the model".

## Counterargument

This is least privilege restated, and readers already put validation and
permissions around anything non-deterministic. Absence from the pages read is
not absence from the field: content checks may exist in places the research did
not look, such as evaluation tools, host products or private code. And a
thin boundary might argue for spending effort elsewhere, not for designing the
boundary better.

## Response

Partly accepted. The contribution is the concrete map of what each documented
control checks and leaves open, and a falsifiable claim: find a documented
runtime control that checks content correctness. The scope is deliberately
"the documents read", and the article says so. Offline evaluation is named as
the place content is checked, not ignored. Whether effort belongs at the
boundary or elsewhere is the author's judgment. [AUTHOR OPINION: where you
would spend the effort, and how strongly you hold the claim.]

## Novel contribution

Most coverage summarizes A2UI or lists libraries. This states what each
documented control checks at runtime, where the documents themselves say
content is left open, how that differs from offline evaluation, and where
vendor claims outrun documentation, with a claim a reader can try to disprove.

## Evidence required

- Primary docs for A2UI, UI SDK, AG-UI, MCP Apps, json-render, the Vercel AI
  SDK, assistant-ui and Tambo (gathered; see research.md).
- A search for documented content-level controls (done 2026-11-21): A2UI's
  eval framework found; no runtime content check on agent output found.
- Not read: A2UI Agent SDK source, eval/tests, conformance; AI SDK tool-approval
  and policy pages; offline benchmarks (leads only).
- Real code from official docs, attributed and re-copied from live pages.

## Author input required

- [AUTHOR EXPERIENCE] any first-hand use, or a real moment where an interface
  an agent produced or operated was wrong inside the boundary; I will not write
  as if I had.
- [AUTHOR OPINION] where the effort belongs, and the strength of the claim.
- [AUTHOR EXAMPLE] optional product example.
