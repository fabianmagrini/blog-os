<!--
Worked example, not yet reviewed by the author. This exists so the
blog-os pipeline has something concrete to run end-to-end (Gate 2 has NOT
happened — thesis_approved: false in article.yaml). Treat every claim below
as a draft position to be tested, not as settled fact.
-->

# Thesis

## Working title

The Agent Harness Is Becoming More Important Than the Model

## Question

As frontier model capability converges across vendors, what determines
whether an AI coding agent is actually reliable in production use?

## Thesis

Harness design — context management, tool scoping, permission gating, and
workflow structure — is becoming a bigger driver of agent reliability than
which underlying model powers it.

## Why now

Multiple frontier models now perform comparably on public coding
benchmarks, yet real-world reliability of agent products built on top of
them still varies widely — a gap that model capability alone does not
explain.

## Argument 1

Most production agent failures observed in practice trace to context and
tool-scoping problems (irrelevant files pulled into context, overly broad
permissions, ambiguous task boundaries) rather than to the model failing to
reason correctly given the context it was actually given.

## Argument 2

Harness features that constrain and structure agent behavior — explicit
state machines, human approval gates, narrow per-agent context, file-based
communication instead of hidden conversational state — measurably reduce
the blast radius and frequency of agent errors, independent of model choice.

## Argument 3

As switching the underlying model becomes cheaper and more common (multiple
vendors, comparable capability, similar APIs), the harness is the thing that
persists and compounds in value across model generations — it is the
long-lived investment, while the model is increasingly a replaceable
component.

## Counterargument

Model capability gaps are still large enough on specific hard tasks —
long-horizon planning, novel algorithm design, deep codebase reasoning —
that no amount of harness quality compensates for a meaningfully weaker
underlying model. Harness-centric arguments may be true for routine tasks
but false for the tasks that matter most.

## Response

This is likely true at the tails, which is exactly why the thesis is scoped
to reliability of routine, repeated engineering work rather than to
frontier reasoning tasks. The claim is not "the model doesn't matter" — it
is that for the workloads most engineering teams actually automate today,
harness quality is the more common bottleneck. [AUTHOR OPINION: state how
strongly you hold this scoping, and whether it should be sharpened or
softened.]

## Novel contribution

Most public commentary treats "agent reliability" as primarily a model
benchmark question. This article argues the more actionable lever for
practitioners today is harness design, and proposes what "good harness
design" concretely looks like.

## Evidence required

- Documented cases (public postmortems, engineering blog posts) attributing
  agent failures to context/tooling/permission issues rather than model
  reasoning failures
- Comparable benchmark data showing capability convergence across current
  frontier models on coding tasks
- Documentation from agent harness vendors/projects describing the specific
  design patterns claimed here (state machines, scoped context, human
  gates)

## Author input required

- [AUTHOR EXPERIENCE] a concrete case from the author's own work where
  harness design (not model choice) determined an agent's reliability
- [AUTHOR OPINION] how far the "harness > model" claim should be pushed for
  this audience
- [AUTHOR EXAMPLE] a specific architecture or workflow the author has built
  or used that demonstrates the argument
