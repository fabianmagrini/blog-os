<!--
Revised 2026-11-15 at the author's direction after research. The original
Gate 2 thesis ("two kinds": emit at runtime vs write at build time, with the
catalog as the common control point) is in git history (commit dfc72cb). The
author chose the revised thesis below and counted that as re-approval.
Reasons for the revision are in research.md ("Thesis impact"): UI SDK also
lets agents operate a live UI, the catalog is the boundary only for
constrained emitters, and A2UI's "values never reach the model" claim is only
partly backed by its docs.
-->

# Thesis

## Working title

Three Jobs Called "Generative UI": Where to Draw the Boundary Between Agents
and Interfaces

## Question

As A2UI 1.0 and libraries such as Vercel Labs' UI SDK arrive, what does
"generative UI" mean, and where should the developer draw the boundary between
an agent and the interface?

## Thesis

"Generative UI" now names at least three jobs (an agent emitting an interface,
writing one, or operating one), and in each the thing worth designing is the
boundary the developer owns, a component catalog for constrained emitters, a
sandbox for unconstrained ones and a permission layer for agents acting on a
live page, because that boundary, not the model, is where reliability,
accessibility and brand safety are settled.

## Why now

Google announced A2UI 1.0 on 2026-11-11 and called it stable; Vercel Labs
published UI SDK 0.1.0-beta.2 on 2026-11-13. They landed in the same week and
do different jobs, alongside json-render, assistant-ui, Tambo, the Vercel AI
SDK, AG-UI and MCP Apps, all described with overlapping vocabulary.

## Argument 1

The word covers different jobs. In A2UI the agent "describes what to show" and
the app draws it from "only the components you register"; json-render,
assistant-ui, Tambo and the AI SDK's tool UIs are variants of that. MCP Apps
lets a tool ship HTML into a sandboxed iframe. UI SDK is a library of behaviors
for agents to write components, and also a bridge (`createAgent`, WebMCP) that
lets an agent read and act on components already on the page. Emit, write and
operate are different jobs with different risks.

## Argument 2

Each job has its own boundary, and the design effort belongs there. For
constrained emitters it is the catalog and function permissions (A2UI's
`allowedCallers`, `requiresUserActivation`; json-render's and Tambo's Zod
schemas). For unconstrained emitters it is the sandbox, CSP and auditable
messages (MCP Apps). For an agent operating a live page it is a permission
layer (UI SDK's `allow`, `data-agent-confirm`, secrets). Each limits form or
action, not content, and each has documented gaps, so a boundary is something
to test, not assume.

## Argument 3

The field is young and mostly vendor-reported, so claims need checking before
they are relied on. A2UI 1.0 is a stable protocol while its SDKs are 0.x and
Gemini, Compose and Lynx are on 0.9.x; its "sensitive values never reach the
model" is only partly supported by its own docs; UI SDK is a beta; and Tambo's
hosted cloud is shutting down. The practical output is a checklist for choosing
and verifying, not a verdict on which project wins.

## Counterargument

The three-jobs split may be taxonomy for its own sake. The lines blur: A2UI can
run inside MCP Apps and carry generated HTML, json-render has an MCP Apps
integration, and AG-UI transports several of them. Several vendors already
publish their own categories. MCP Apps, now a stable MCP extension, may make
most of this moot. And a catalog or permission layer may be a thin safeguard if
the boundary is misconfigured.

## Response

The overlap is real and the article should say so; the claim is that the jobs
differ in what is at risk, not that the projects are disjoint. The axis is
orthogonal to vendor categories (which describe expressiveness), and the
article places itself against them. The thin-safeguard point is part of the
thesis: the boundary has to be designed and tested, which is why the article
ends with what to verify. [AUTHOR OPINION: how strongly you think a boundary,
not the model, decides reliability.]

## Novel contribution

Most coverage summarizes A2UI or lists libraries. This separates what the agent
is doing (emit, write, operate), names the boundary in each, places verified
projects on that map, shows where claims outrun the docs, and ends with a
verification checklist.

## Evidence required

- A2UI, UI SDK, AG-UI, MCP Apps, json-render, Vercel AI SDK, assistant-ui and
  Tambo from primary docs (gathered; see research.md).
- Real code from official docs, attributed and re-copied from live pages.
- Independent evidence on reliability, accessibility or security of generated
  UI: none located; the article must say so.
- Open items: A2UI governance and bound-value behavior, how json-render
  constrains the model, whether Tambo's hosted API stopped.

## Author input required

- [AUTHOR EXPERIENCE] any first-hand use of these, or a real moment where an
  agent in front of an interface went wrong; I will not write as if I had.
- [AUTHOR OPINION] how strongly the boundary, not the model, decides
  reliability.
- [AUTHOR EXAMPLE] a product feature you would build with each job, if you
  want one.
