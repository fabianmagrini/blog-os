<!--
Approved at Gate 2 on 2026-11-15 WITH A SCOPE CHANGE requested by the author:
widen from A2UI 1.0 and UI SDK to a wider field of generative-UI libraries and
protocols. The thesis claim is unchanged; A2UI and UI SDK stay the two anchor
cases and other projects are placed on the same runtime / build-time map only
if verified from primary sources. Libraries to be chosen during research.
-->

# Thesis

## Working title

Two Kinds of Generative UI: What A2UI 1.0 and Vercel's UI SDK Tell Us About
Trusting Agents With Interfaces

## Question

As A2UI 1.0 and libraries such as Vercel Labs' UI SDK arrive, what does
"generative UI" mean, and where should the trust boundary sit between an agent
and the interface it produces?

## Thesis

"Generative UI" now covers two different jobs, an agent emitting an interface
at runtime from components the app has registered (A2UI) and an agent
authoring components at build time from tested behaviors (UI SDK), and in both
the decision that matters most is the design of the catalog the developer owns,
because that is where reliability, accessibility and brand safety are settled,
not the model.

## Why now

Google announced A2UI 1.0 on 2026-11-11 and called it stable; Vercel Labs
published UI SDK 0.1.0-beta.2 on 2026-11-13. They arrived in the same week
with different ideas of what an agent contributes to an interface, and
readers are being asked to adopt both vocabularies at once.

## Argument 1

The two projects do different jobs. A2UI is a protocol in which "the agent
describes what to show and every app draws the UI with its own native
components", with an agent that places and configures "only the components you
register". UI SDK is "a library of behaviors for agents to build the next
generation of user interfaces", where the agent puts behaviors such as focus,
selection and popups together into components. Calling both "generative UI"
hides that one is about what appears on screen at runtime and the other about
how an interface gets written.

## Argument 2

Both put the safety boundary in a catalog the developer owns. In A2UI that is
the registered component set plus server-side data binding, so "sensitive
values never reach the model". In UI SDK it is the tested behaviors and the
ARIA they carry. In each case the agent's freedom is bounded by what the
catalog exposes, so teams should spend their design effort there: what the
catalog contains, what it forbids, and how accessibility and brand rules are
enforced.

## Argument 3

Both are early, and most claims are the vendors' own. A2UI 1.0 is called
stable, yet Gemini supports 0.9.1, the Compose renderer is at 0.9.1 and Lynx
at 0.9; the announcement gives no code, wire format or threat model. UI SDK is
a beta whose releases are all pre-release. The practical advice is a checklist
of what to verify before depending on either, not a verdict on which wins.

## Counterargument

The two-kinds split may be a taxonomy more than an insight. UI SDK also
documents connecting an agent to components and WebMCP, which lets agents read
and act on components at runtime, so the line blurs. MCP Apps, which A2UI's
renderers can run inside, may make the distinction moot. And a declarative
catalog caps what an agent can express, so "generative UI" may amount to chat
with widgets.

## Response

The blur is real and the article should say so rather than hide it: the claim
is that the two jobs differ in emphasis and that the catalog is the common
control point, not that the projects never overlap. Expressiveness limits are
the cost of the trust boundary, which is the trade-off the article examines.
[AUTHOR OPINION: how strongly you think the catalog, rather than the model, is
the decision that matters.]

## Novel contribution

Most coverage summarizes A2UI or lists libraries. This separates runtime from
build-time generative UI, places A2UI and UI SDK as anchor cases and other
verified libraries and protocols on the same map, names the catalog as the
control point, and ends with a verification checklist.

## Evidence required

- A2UI: the specification and evolution guide, message format, security model,
  license and governance, and how it relates to MCP Apps (partly gathered;
  the announcement has none of these).
- UI SDK: the agent docs (Build with an Agent, Skills, Connect an Agent,
  WebMCP), and what is runtime versus build-time (partly gathered).
- Other libraries and protocols named in the brief ("such as"): json-render,
  AG-UI, Vercel AI SDK generative UI, MCP Apps, assistant-ui and others. Not yet
  researched; the article should cover only those that are verified.
- Independent evidence on reliability or accessibility of generated UI.
  None located yet.
- Real code samples must come from official docs and be attributed.

## Author input required

- [AUTHOR EXPERIENCE] whether you have built an agent frontend or used A2UI or
  UI SDK; a first-hand try would strengthen it, and I will not write as if I
  had.
- [AUTHOR OPINION] how strongly the catalog is the deciding factor.
- [AUTHOR EXAMPLE] a product or feature you would build with each approach.
