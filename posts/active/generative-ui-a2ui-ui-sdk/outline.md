# Outline

## Article

Three Jobs Called "Generative UI": Where to Draw the Boundary Between Agents
and Interfaces

Target: about 2,500 words. Built from documentation only; nothing has been run
first-hand. Section references point to research.md claims. Code samples must
come from official docs, attributed, and be re-copied from live pages.

## Structure

### Hook / Problem  (~200 words)

In one week, 11 to 13 November 2026, Google called A2UI stable and Vercel Labs
shipped a beta of UI SDK. Both put an agent in front of an interface, and they
do different things. Open on that, not on definitions.

- [AUTHOR EXPERIENCE] a real moment where an agent in front of an interface
  went wrong or went well, if you have one. Otherwise open on the week alone;
  do not invent an anecdote.

### Observation  (~200 words)

"Generative UI" is being used for at least three jobs: an agent emitting a UI,
writing one, or operating one. The vocabulary overlaps (A2UI, json-render,
assistant-ui, Tambo, the AI SDK, MCP Apps, AG-UI), which is why the pieces get
confused. (Claim 7)

### Thesis  (~100 words)

State it plainly: in each job the thing worth designing is the boundary the
developer owns, not the model.

### Evidence: Emit  (~450 words)

Constrained emitters: A2UI (data, not code; flat components; catalog as a
contract; function permissions), with json-render, assistant-ui, Tambo and the
AI SDK's tool UIs as variants. Unconstrained: MCP Apps (`ui://` HTML in a
sandboxed iframe). AG-UI as transport, "not a generative UI specification".
(Claims 1, 4, 7)

### Evidence: Write  (~200 words)

UI SDK's behaviors library and skill: agents compose tested behaviors with
rules about naming controls and ARIA. Build-time, reviewed in code. (Claim 5)

### Evidence: Operate  (~300 words)

UI SDK's `createAgent` and WebMCP: an agent reads `snapshot()` and calls
`act()` on a live page, under `allow`, `data-agent-confirm` and secrets.
Include the docs' own admissions of what `allow` does not cover. (Claim 6)

### Framework or Architecture: the boundary map  (~250 words)

A table: job, example projects, where the boundary sits, what it limits, and
where it leaks (form not content; actions not visibility; sandbox not
semantics). Place it against vendor taxonomies, which describe expressiveness
(constrained to unconstrained), a different axis. (Claims 7, 8)

### Concrete Examples  (~350 words)

Four short attributed samples: an A2UI message with a bound action; a
json-render catalog; UI SDK `allow` plus `data-agent-confirm`; an MCP Apps
tool declaring a `ui://` resource. Say which are verbatim and from where.
(Useful examples in research.md)

- [AUTHOR EXAMPLE] a product feature to carry through the three jobs, if you
  want a common thread. Otherwise keep the samples separate.

### Trade-offs  (~250 words)

Constrained emitters give predictability and cost expressiveness; unconstrained
give expressiveness and move trust to the sandbox; operating a page is cheap to
add and relies on a permission layer whose docs say what it does not cover.
Boundaries limit form or action, not content. (Claims 4, 6)

### Where claims outrun the docs  (~250 words)

Three checks the reader can copy: "stable" (A2UI protocol 1.0 versus 0.x SDKs
and 0.9.x consumers); "never reaches the model" (data binding versus actions and
`sendDataModel`); "production" (Tambo Cloud shutting down, AI SDK RSC
experimental). No independent evaluation of reliability, accessibility or
security was found. (Claims 2, 3, 9)

### Counterargument  (~200 words)

The split is taxonomy; the lines blur (A2UI inside MCP Apps, json-render's MCP
integration); MCP Apps may make it moot; a thin boundary can be a false
comfort. Give it in full, then the Response: the claim is about what is at
risk, and the boundary has to be tested.

### Recommendation  (~200 words)

A checklist, not a winner: which job; where the boundary is; what is verified
versus claimed; what is 0.x or beta; what vendor risk exists; how
accessibility will be tested for generated UI.

- [AUTHOR OPINION] how strongly to say the boundary, not the model, decides
  reliability, and whether to name a preferred approach.

### Conclusion  (~100 words)

Back to the week: two launches, different jobs. End on what to watch, not a
prediction.

---

## Author contributions required

- [AUTHOR EXPERIENCE] any first-hand use, or a real moment for the hook.
  Without it the article describes documentation and says so.
- [AUTHOR OPINION] strength of the boundary claim and any preferred approach.
- [AUTHOR EXAMPLE] an optional feature to carry through all three jobs.

## Verify before publication

- Re-copy every code sample from the live pages; A2UI samples came through a
  quote-capped fetch.
- Re-check versions and dates: A2UI protocol 1.0 and SDK versions, Gemini
  support, UI SDK 0.1.0-beta.2, json-render 0.22.0, MCP Apps spec date, Tambo's
  hosted API.
- Resolve open items: A2UI governance and bound-value behavior, json-render's
  constraint mechanism, and the MCP Apps sandbox permission difference.
- Re-check star counts at publication time or drop them.
- Keep the A2UI "never reach the model" claim attributed and qualified.

## Deviations from default structure

The Evidence section holds one block per job (emit, write, operate) and
"Framework" holds the boundary table. A "Where claims outrun the docs" section
is added between Trade-offs and Counterargument because verification is part of
the thesis.
