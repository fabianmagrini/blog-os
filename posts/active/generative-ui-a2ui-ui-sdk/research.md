# Research Dossier

## Article

What the Boundary Doesn't Check: Generative UI After A2UI 1.0

## Thesis

Revised 2026-11-21 after the critics' review and approved by the author
(earlier theses: dfc72cb, e47cbfd). Every runtime control the field currently
offers around an agent and an interface (a component catalog, a sandbox, a
permission layer) limits what the agent can show or do, not whether what it
shows is correct. In the documents read, whether the content is right is left
to offline evaluation and to checks the developer writes, so the reliability
work that matters sits outside the boundary.

> **Note:** the "Thesis impact" section at the end records why the thesis was
> revised; its proposed text is now adopted.

All figures were read on 2026-11-15. Star counts are popularity, not quality.
Several fetches were capped on quote length, so code and JSON samples must be
re-copied from the live pages before publication.

# Review log: 2026-11-21 (critics and falsification test)

- **Reclassification (technical review, critical).** MCP Apps UI is HTML the
  tool author predeclares as a `ui://` resource; the host may preload it, and
  the model only decides to call the tool. It is not agent-emitted. The
  A2UI-embeds-generated-HTML case is the model-supplied one. Web hosts
  "typically" use a sandboxed iframe; that is not a requirement for every host.
- **A2UI stability.** The 0.x SDK versions are package versions; the release
  notes mark entries as implementing v1.0, so a 0.x package does not
  contradict a stable 1.0 protocol. The 0.9 to 1.0 "cannot be used directly"
  line is a migration note. The supportable point is consumer lag (Gemini and
  Compose 0.9.1, Lynx adapting) and that v0.9 catalogs do not carry over.
- **Attribution conflict.** The critic found "can be updated directly by the
  language model during generation" on the data-binding page, not the messages
  page; an earlier fetch attributed it to messages. Resolve at fact-check.
- **UI SDK corrections (from the review's live reads, to verify at
  fact-check):** the bridge sees only UI SDK components (snapshot caps at 100);
  `data-agent-confirm` needs a person only when `allow` does not answer for them
  (docs warn that an `allow` returning true answers for the person) and without
  an `allow` the press fails; the 5-minute wait is a default that `timeout`
  changes; the skill install command is `npx skills@latest add ...`; the "55
  components" count and the "some APIs may still change" wording could not be
  confirmed, use the README's "UI SDK is in beta"; AGENTS.md describes testing
  helpers that check components against WAI-ARIA patterns, so the Write case
  does include structural accessibility checks.
- **AI SDK conflict.** The critic says the AI SDK page tells readers to
  validate output shape before rendering; the falsification read found its
  example validates tool input only and renders output directly as props. Not
  resolved; re-read the page.
- **Falsification test (content-level controls).** Result: partial. A2UI's eval
  framework (eval/, roadmap "Available today") scores model output on the
  project's own datasets in three stages: schema and structure; deterministic
  assertions (required and forbidden components, bindings, actions); and an LLM
  judge grading against a per-sample rubric. With `--no-judge` the scorer
  "returns C" for any sample that passed stages 1 and 2, so content is not
  checked in that mode. "Tool usage as a judge" is roadmap only. `@checks`,
  `regex`, `required`, `length`, `numeric` and `email` are documented for input
  components, not agent output. Agent-side functions (for example checking
  seat inventory) let a developer verify values on the server; that is a
  developer-written check, not a built-in one. json-render's docs for its
  experimental composer say "Completion is not a correctness guarantee" and
  "Registering an action does not make it safe to execute with arbitrary
  values". AG-UI lists interrupts (human in the loop) as a building block.
  No runtime content-correctness check on agent output was found.
- **Search leads (not read beyond summaries, do not cite details):** an arXiv
  paper on Macaron-A2UI (deterministic checks plus render check plus LLM
  judges), thesysdev/generative-ui-bench, OpenUI's vendor-run benchmarks (a
  competitor of A2UI, so a conflict of interest; its json-render figures
  differ between two pages), UIPersonaBench. All are offline.

---

# Update log: re-check on 2026-11-21

Re-read from live pages; "changed" is against the 2026-11-15 readings above.
Where a fetch could not read something, it says so.

- **A2UI** (re-read): stars 17.7k (was 17.4k); releases on 2026-11-17: Python
  agent SDK 0.12.0, core 0.7.0, a2a 0.4.0, Swift 0.11.0 and CLI v0.4.0 (marked
  Latest); on 2026-11-10/11 the 0.11.0 SDK, core 0.6.0 and CLI v0.3.0. No
  release is titled as a protocol or spec release; no 1.0.x or 1.1 appears,
  and the tags page was not checked. Roadmap still lists v1.0 as Current and
  the README only says v1.1 requirements are being collected. The blog post
  has no visible correction and still says Gemini supports 0.9.1, Compose is
  0.9.1 and Lynx is adapting to 1.0. Governance: CONTRIBUTING.md requires a
  Contributor License Agreement (cla.developers.google.com), says the project
  follows Google's Open Source Community Guidelines and points to a
  Google-internal link; there is no GOVERNANCE or MAINTAINERS file and no
  mention of a foundation [S15]. Data binding: still no statement that bound
  values are hidden from the model, and the messages page says the data model
  "can be updated directly by the language model during generation" [S5].
- **UI SDK**: latest is 0.1.0-beta.13 (2026-11-19; beta.12 the same day), up
  from beta.2 on 2026-11-13; still all pre-release, no 1.0 seen on the first
  releases page. Stars 6.3k (was 4.6k), 688 commits (was 454). The docs
  changelog has one entry, "Introducing UI SDK", dated 2026-11-12, so the
  launch was the 12th and beta.2 the 13th [S16]. Permissions and WebMCP pages
  read again; same content as summarized (no earlier copies to diff word for
  word). Still no mention of A2UI, AG-UI, json-render, MCP Apps or
  "generative UI".
- **json-render**: latest release v0.23.2 (2026-11-19), after v0.23.1
  (11-16), v0.23.0 (11-15, adds a Swift/SwiftUI renderer) and v0.22.0 (11-04);
  stars 19.8k. The CHANGELOG could not be read (503 twice). README Quick Start
  unchanged (`defineCatalog(schema, ...)`, undefined `format()`); the homepage
  still shows a different (`defineSchema`) example. An automated GitHub digest
  found in search called it "in maintenance mode", which the release cadence
  contradicts; that digest is low credibility and not used [S18].
- **AG-UI**: new. The repo now says "AG-UI 1.0 is here", with "a stable,
  frozen specification backed by a JSON Schema" that is backwards compatible
  with 0.x; stars 20.8k (was 17.4k). Its docs still say "AG-UI is not a
  generative UI specification". The release tag and date were not readable.
  Its docs list A2UI, MCP-UI and Open-JSON-UI as generative UI specs while the
  README lists A2UI, MCP Apps and Open-JSON-UI.
- **Tambo**: banner unchanged, still in the future tense ("keeps running until
  October 31, 2026") although that date has passed; the shutdown post is dated
  2026-10-01 and the team is pivoting to Charming. Whether the hosted API
  actually stopped is still unverified [S17].
- **Vercel AI SDK**: the RSC overview now reads "currently experimental. We
  recommend using AI SDK UI for production" with a migration link. The
  stronger phrase quoted earlier ("unsuitable for stable production use") is
  on the migration guide, which was not re-read, so it is not re-confirmed. The
  "major version 7" claim came from the 7.0 migration guide and was not
  re-confirmed on the pages read today.
- **MCP Apps**: spec still Stable 2026-01-26; hosts on the docs page
  unchanged; ChatGPT is claimed only in the repo README, and the client matrix
  page was not read. Sandbox question (previously unresolved): the spec's MUST
  (`allow-scripts` and `allow-same-origin`, on a different origin from the
  host) applies to the outer sandbox proxy, while A2UI's guide states
  `sandbox="allow-scripts"` without same-origin for the inner View frame, whose
  attribute values the spec text read does not specify. They are not a direct
  contradiction, but it is unverified that A2UI's guide meets the spec for the
  outer proxy. Part of the spec's security section was read only via a
  summary.
- **Search for new developments**: no new primary announcements found. The
  results were secondary blogs and automated digests; one says A2UI's releases
  show no tag named 1.0, which the re-check corroborates (see above). Not used
  as evidence.
- **Effect on the thesis**: none. The changes strengthen the "young and
  fast-moving" point (SDK versions moved a minor version in a week) and add
  AG-UI 1.0 as a stabilizing transport layer.

---

# Claim 1

A2UI is a declarative-data protocol: agents send JSON describing a UI, never
code, and the app renders it from a catalog it controls. (factual)

## Supporting evidence

README: "A2UI (Agent-to-User Interface) is an open-source generative UI
framework" [S6]. The homepage says it "Streams declarative JSON data with
two-way bindings — never executable code", and the catalogs page says agents
send only known component types, "never raw HTML, CSS, or executable scripts"
[S5]. Every wire message is a JSON object with a `version` field; agent-to-
renderer messages are `createSurface`, `updateComponents`, `updateDataModel`,
`deleteSurface`, `callRendererFunction` and `agentFunctionResponse`, and
renderer-to-agent messages are `action`, `callAgentFunction` and
`rendererFunctionResponse` [S5]. Components are a flat adjacency list with
ID references and one `root`; data binding uses `{"@path": "/reservation/
destination"}` in 1.0 [S5]. A catalog is "a collection of components and
functions that acts as a contract between an agent and a renderer", with JSON
Schema per component; the basic catalog has 18 components and 14 functions
[S5]. Renderers: React, Lit, Angular, Flutter, SwiftUI, Jetpack Compose, with
community renderers for Lynx, Svelte, Vue and a Go TUI [S5, S6]. Apache-2.0,
GitHub org `a2ui-project`, 17.7k stars on 2026-11-21 [S6].

## Contrary evidence

The acronym is not expanded on the announcement, homepage or quickstart; only
the README expands it [S1, S5, S6]. Ownership: the repo is under a separate GitHub
organization, but CONTRIBUTING.md requires a Google CLA, follows Google's Open
Source Community Guidelines and links Google-internal information; no
GOVERNANCE or MAINTAINERS file or foundation is mentioned [S6, S15]. That
points to a Google-run project, which is an inference, not a stated fact.

## Assessment

Solid for the design. The article can say "data, not code" with the project's
own wording. Avoid claiming Google owns it beyond "announced on Google's
developer blog".

## Confidence

High (design as documented), Low (governance)

---

# Claim 2

A2UI's server-side data binding keeps sensitive values from the model, as the
announcement says. (factual)

## Supporting evidence

The announcement: "A2UI reliably binds to your data and child components on
the server, so sensitive values never reach the model" [S1]. The data-binding
docs say deterministic agent code can inject data "directly into the surface
without passing them through the model" [S5]. The README says the agent must
not handle data such as credit card or account numbers, PII or financial data
[S6].

## Contrary evidence

The docs do not say bound values are hidden from the model, and do not state a
mechanism for the README's rule. Button actions send resolved context values
back to the agent, `sendDataModel: true` attaches the full surface data model
to every outbound message to the creating agent (metadata key
`a2uiRendererDataModel` in 1.0), and the messages page says the data model "can
be updated directly by the language model during generation" [S5]. Whether
data sent to the agent's server then reaches the model is not stated. Data an agent injects deterministically from server code need
not pass through the model, but values that reach the agent via actions or
`sendDataModel` can.

## Assessment

Only partly backed. The honest statement is that A2UI lets server code bind
data without routing it through the model, and that whether a value reaches
the model depends on how actions and `sendDataModel` are used. Do not repeat
"sensitive values never reach the model" as a guarantee.

## Confidence

High (that it is only partly supported by the docs read), Low (actual behavior)

---

# Claim 3

A2UI 1.0 is stable. (factual)

## Supporting evidence

The announcement calls it "the first stable version" and "a stable protocol"
[S1]. The roadmap page lists v1.0 as Current, v0.9.1 and v0.9 as Previous, and
v0.8 as Deprecated [S5].

## Contrary evidence

The announcement itself says Gemini supports 0.9.1 "today", the Compose
renderer is at 0.9.1 with 1.0 "coming soon", and Lynx supports 0.9 and is
adapting [S1]. The evolution guide lists breaking changes from 0.9 (renamed
`@path`/`@call`, a new MIME type, `callFunction` replaced, `theme` and
`primaryColor` removed, `updateDataModel` `value` now required) and says
"Catalogs authored for v0.9 cannot be used directly with v1.0 protocol
runtimes" [S6]. The released packages are all 0.x, and moved quickly: on
2026-11-17 the Python agent SDK was 0.12.0 (0.11.0 a week earlier), core 0.7.0,
a2a 0.4.0, Swift 0.11.0 and the CLI v0.4.0; no release is titled as a protocol
release and none is tagged 1.0 on the releases page (the tags page was not
checked) [S6]. The README says protocol v1.1 requirements are being collected [S6].

## Assessment

"Stable" describes the protocol version, not the ecosystem. The article should
say what 1.0 covers and note that SDKs are 0.x and key consumers lag.

## Confidence

High

---

# Claim 4

A2UI's trust boundary is the catalog plus function permissions, and it limits
what a misbehaving agent can do. (factual)

## Supporting evidence

README: "The app developer controls what the agent can and cannot do in the
app" [S6]. Homepage: "Agents place only components you registered" [S5]. The
agent SDKs validate output against live surface state and return errors to the
model [S5]. Functions carry `allowedCallers` (`rendererOnly` by default,
`agentOnly`, `rendererOrAgent`) and `requiresUserActivation`, which stops
navigation without user intent and is paired with `openUrl` [S5]. Per the
pages, an agent cannot emit raw HTML, CSS or scripts, place components outside
the catalog, call `rendererOnly` functions remotely, or trigger
`requiresUserActivation` functions without a user gesture [S5].

## Contrary evidence

An agent can still choose any registered component, send any values in
`updateDataModel` or action context, call `agentOnly` functions and choose any
supported catalog; the pages describe no semantic check on content, and no
threat model beyond these principles [S5]. The announcement describes none
[S1]. Whether a renderer implements these checks correctly is not evidenced.

## Assessment

A real, specific boundary, with the catalog at its center. It limits form
(what can appear), not content (what it says). Say so.

## Confidence

High (as documented), Low (renderer implementations)

---

# Claim 5

UI SDK is a build-time library for agents authoring components, and the thesis
can treat it as the build-time counterpart to A2UI. (factual; tests thesis
Argument 1)

## Supporting evidence

"A library of behaviors for agents to build the next generation of user
interfaces": focus, selection, dismissal, popups, drag and drop and ARIA in
`@ui-sdk/core`, with adapters for React, Vue, Svelte, Solid and Web
Components, and 55 unstyled React components [S2]. The `ui-sdk` skill
(`npx skills add vercel-labs/ui --skill ui-sdk`) is a workflow for choosing
behaviors, defining a primitive, rendering and testing it, with rules such as
per-component imports, "Name every control", never generate ids, key lists by
value or id, and not hand-rolling `role=` attributes [S4]. AGENTS.md says
agents "can now generate those interfaces", meaning code written for
developers [S4]. Apache-2.0, vercel-labs, 6.3k stars on 2026-11-21; every
release is a pre-release (0.1.0-beta.13 on 2026-11-19, up from beta.2 on the
13th) and the docs say "UI SDK is in beta, so some APIs
may still change" [S2, S16].

## Contrary evidence

UI SDK is not only build-time. Its "Connect an Agent" feature lets an agent
operate the live page: `createAgent` returns `snapshot()` (the components with
refs, labels, values and actions), `act()` (for example `setValue`) and
`query()`, and `registerTools` exposes the same three tools to "the agent
built into a browser" through `document.modelContext` (WebMCP) [S3]. The docs
do not describe an agent generating new UI for end users at runtime [S3]. The
pages read never mention A2UI, AG-UI, json-render, MCP Apps or "generative UI"
[S2, S3, S4].

## Assessment

Build-time authoring is accurate. But the larger point is a different job:
an agent acting on UI that already exists. That is a third role next to
"emit" and "write" (see Thesis impact).

## Confidence

High (as documented)

---

# Claim 6

UI SDK's runtime bridge has its own trust boundary, in the form of a
permission layer. (factual)

## Supporting evidence

`createAgent({ allow })` runs a callback before each step; returning false
refuses it and `act` returns `ok: false`. `allow` can return a Promise to ask
the person, with a 5-minute default timeout. `data-agent-confirm="..."` marks a
control that always needs a person; `data-agent-hidden` hides components from
`snapshot` and `query`; `data-agent-secret` shows "[redacted]"; password, card
and one-time-code fields are treated as secret without a mark [S3]. WebMCP
tools carry `readOnlyHint` (snapshot, query), `untrustedContentHint` (all
three) and `consequentialHint` (act) [S3]. The docs warn that "An allow that
returns true without reading step.confirm answers yes for the person" and that
checks in keyboard or pointer handlers do not run for `setValue` because it
calls the component API directly [S3].

## Contrary evidence

The docs say `allow` checks actions only: components stay visible in
`snapshot()`, `query()` can still read choices, and finding a component can
open a section or popup before the action is checked [S3]. With no `allow`
callback, the bridge accepts supported actions [S3]. Registration works only
in a browser that provides `document.modelContext`, which the pages do not
name; WebMCP is not defined or linked to a spec [S3]. The docs' own agent
benchmark (16 vs 5 tool calls, 39.8k vs 6.8k characters read, 41 s vs 16 s,
$0.073 vs $0.032, medians of three runs on one task with Sonnet via Claude
Code) is vendor-reported and the baseline is not clear from the report [S3].

## Assessment

A third kind of boundary, specific and unusually candid about its limits.
Quote the limits; they are evidence about where boundaries leak.

## Confidence

High (as documented), Low (effectiveness)

---

# Claim 7

The field has at least three families, and the projects sort into them.
(factual, with the taxonomy as interpretation)

## Supporting evidence

**Constrained emitters (model picks from a catalog)**:
- json-render (Vercel Labs, Apache-2.0, 19.8k stars): "AI generates interfaces
  from natural language prompts, constrained to components you define", a
  Zod-typed catalog, a flat `{ root, elements }` spec, many renderers (React,
  Vue, Svelte, Solid, React Native, PDF, email, terminal, Chat SDK and more),
  an MCP Apps integration, latest release v0.23.2
(2026-11-19; v0.23.0 added a SwiftUI renderer), no project-wide beta label
found [S9, S18].
- assistant-ui (MIT, 13.2k stars): the model emits a flat JSON tree through a
  `present` tool, with 35 default components and Zod-schema custom components;
  `@assistant-ui/generative-ui` is pinned at `^0.0.11` [S11].
- Tambo (MIT, 11.2k stars): components registered with Zod `propsSchema` [S12].
- Vercel AI SDK: "Generative UI is the process of connecting the results of a
  tool call to a React component", rendered client-side with `useChat` [S10].
- A2UI (Claim 1).

**Unconstrained emitters (model or tool supplies HTML)**: MCP Apps, an
official MCP extension whose spec is "Stable (2026-01-26)": a tool declares a
`ui://` resource with MIME type `text/html;profile=mcp-app`, rendered in a
sandboxed iframe with JSON-RPC over `postMessage`, a restrictive default CSP
(`default-src 'none'`, `connect-src 'none'`), hosts including Claude, VS Code
GitHub Copilot and Microsoft 365 Copilot [S8]. It unifies the approaches of
MCP-UI and the OpenAI Apps SDK [S8].

**Transport, not a UI format**: AG-UI says "AG-UI is not a generative UI
specification"; it is an event-based interaction protocol that "natively
supports" A2UI, Open-JSON-UI and MCP-UI (MIT, 20.8k stars on 2026-11-21, origin in
CopilotKit's partnership with LangChain and CrewAI; its repo now says "AG-UI 1.0 is
here" with a stable, frozen specification) [S7].

**Agent writes or operates UI**: UI SDK (Claims 5-6).

## Contrary evidence

Boundaries are not clean: A2UI says generated HTML and JS "can run as an MCP
App inside an A2UI surface" [S5]; json-render lists MCP Apps integration [S9];
AG-UI carries both [S7]. The categories come from vendor pages, some with
internal inconsistencies [S13, S14]. Only the awesome-list's table separates
dev-time ("Static UI (generation happens in dev)") from runtime generation,
and does not name specific tools beyond calling v0 a "Component Generator" and
Bolt.new and Lovable "App Builders" [S14].

## Assessment

A usable map for the article, with overlaps stated. It is my synthesis.

## Confidence

Medium

---

# Claim 8

Existing taxonomies already describe this field, so the article's axis needs
to be placed against them. (factual)

## Supporting evidence

CopilotKit's "Generative UI Spectrum" (a vendor page) names Controlled
("developers make pre-defined components available for the agent to render"),
Declarative ("catalogs of lego-like building blocks that the agent assembles
on demand at runtime") and Open-Ended, with MCP Apps as its own band [S13].
AG-UI's docs name static and declarative generative UI [S7]. The awesome-list
splits constrained from unconstrained [S14].

## Contrary evidence

The CopilotKit page says "three pillars" while showing four bands, uses
"Open-Ended" and "Fully Open" for the same band, and claims AG-UI is "in
production at the majority of Fortune 500 and Fortune 1000 companies", which
is unverified [S13]. The three taxonomies disagree on the category count and
on names. None is independent.

## Assessment

The expressiveness axis (constrained to unconstrained) is orthogonal to the
article's axis (who does what: emit, write, operate). The article should say
so, instead of pretending to be the only map.

## Confidence

Medium

---

# Claim 9

The field is young and unstable, and vendor-reported. (factual)

## Supporting evidence

A2UI SDKs at 0.x [S6, S15]; UI SDK 0.1.0-beta.13 [S2, S16];
assistant-ui's generative UI package at 0.0.11 [S11]; json-render at v0.23.2
with a README catalog API that differs from its homepage example and a Metric
component that calls an undefined `format()` [S9, S18]. Vercel AI SDK RSC
(`streamUI`) is "currently experimental" with a recommendation to use AI SDK UI
for production (the stronger "unsuitable for stable production use" wording is
on the migration guide, not re-read; "major version 7" was not re-confirmed)
[S10]. Tambo's README says "Tambo Cloud is shutting down": new signups closed,
the hosted API stops after October 31, 2026 and user data is deleted November
30, 2026; the banner is still in the future tense and the hosted API was not
checked; the project stays open source and self-hostable [S12, S17]. AG-UI,
by contrast, now claims a stable frozen 1.0 specification [S7].
No independent evaluation of reliability or accessibility of generated UI was
found.

## Contrary evidence

Adoption claims exist: Atlassian (Jira), Alation, ByteDance (Lynx), Bloomberg
and Google's own Gemini products for A2UI [S1], with 17.4k to 19.6k stars on
the larger projects. These are early-adopter signals, not evidence of
reliability.

## Assessment

Supports "verify before depending". Tambo's change is a concrete example of
why a catalog-based approach does not remove vendor risk for the surrounding
stack.

## Confidence

High (state of the projects), Low (outcomes)

---

# Useful examples

All must be re-copied from the live pages; some were relayed through a fetch
tool that capped quote length.

- A2UI: `createSurface` with `components` and `dataModel`, a `Button`
  `action.event` with data-bound `context`, and a catalog definition
  (https://a2ui.org/concepts/messages/, /catalogs/, /data-binding/).
- UI SDK: `createAgent`, `agent.snapshot()` output, `agent.act()`, `allow` and
  `data-agent-confirm` (https://ui-sdk.dev/docs/agents/connect-an-agent and
  /permissions).
- json-render: `defineCatalog` with Zod components and actions, then
  `defineRegistry` and `<Renderer spec registry />` (README Quick Start [S9]).
- AI SDK: `part.type === 'tool-displayWeather'` rendering `<Weather ...>` [S10].
- MCP Apps: a tool's `_meta.ui.resourceUri` pointing at a `ui://` resource [S8].

# Useful quotes

- "Streams declarative JSON data with two-way bindings — never executable
  code." (a2ui.org) [S5]
- "AG-UI is not a generative UI specification" (docs.ag-ui.com) [S7]
- "An allow that returns true without reading step.confirm answers yes for the
  person." (ui-sdk.dev) [S3]
- "Catalogs authored for v0.9 cannot be used directly with v1.0 protocol
  runtimes." (A2UI evolution guide) [S6]

# Open questions

- (Partly resolved 2026-11-21) A2UI governance: CLA, Google guidelines and an
  internal link point to a Google-run project; no foundation or GOVERNANCE
  file. The A2UI A2A extension spec
  (https://a2ui.org/specification/v1.0-a2ui-extension-specification/) was not
  read.
- What mechanism, if any, keeps bound values off the model in A2UI?
- How does json-render constrain the model (structured output, constrained
  decoding, or prompt and validation)? The pages do not say.
- Did Tambo's hosted API actually stop on 2026-10-31? Not checked.
- OpenUI (Thesys), Open-JSON-UI (OpenAI), Hashbrown, mdocUI and others appear
  in an awesome-list but were not verified; leave them out unless checked.
- (Narrowed 2026-11-21) MCP Apps sandbox: the spec's MUST for the outer proxy
  (`allow-scripts`, `allow-same-origin`, different origin) and A2UI's inner-frame
  `sandbox="allow-scripts"` apply to different frames; whether A2UI's guide
  meets the spec for the outer proxy is unverified, and part of the spec's
  security section was only seen via a summary.
- Still unverified: A2UI protocol tags, AG-UI 1.0 release tag, MCP Apps client
  matrix (ChatGPT, Gemini, Cursor), json-render CHANGELOG, the AI SDK
  migration guide wording and major version.
- No independent evidence on reliability, accessibility or security of
  generated UI. None located.
- No first-hand trial of any of these.

# Claims requiring author judgment

- Whether to revise the thesis (see below).
- Which of the verified projects to include; the article cannot cover them all.
- Whether to take a position on "constrained is enough".

---

# Thesis impact (for the author's decision)

The thesis was approved on 2026-11-15. Research suggests three changes. Per
AGENTS.md this needs re-approval, so none has been made.

1. **"Two kinds" is too few.** UI SDK is not only build-time authoring; its
   `createAgent` and WebMCP features let an agent *operate* an existing UI
   under a permission layer (Claims 5-6). That is a third job next to "emit"
   (A2UI, json-render, assistant-ui, Tambo, AI SDK tool UIs, MCP Apps) and
   "write" (UI SDK's skill, v0-style generators).
2. **"The catalog is the control point" holds only for constrained emitters.**
   For MCP Apps it is the sandbox and CSP; for an agent operating a live page it
   is the permission layer (`allow`, `data-agent-confirm`, secrets). The shared
   idea is a boundary the developer owns, whatever shape it takes.
3. **Blog-level safety claims overstate the docs.** A2UI's "sensitive values
   never reach the model" is only partly supported (Claim 2), which supports
   a "verify the boundary" message.

Proposed revision, for approval:

> "Generative UI" now names at least three jobs (an agent emitting an interface,
> writing one, or operating one), and in each the thing worth designing is the
> boundary the developer owns, a component catalog for constrained emitters, a
> sandbox for unconstrained ones and a permission layer for agents acting on a
> live page, because that boundary, not the model, is where reliability,
> accessibility and brand safety are settled.
