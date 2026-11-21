# Fact Check

Draft checked: `drafts/v2.md` (2026-11-21). Read live on 2026-11-21 against the pages named below; three agents checked the claims independently of the Writer. Statuses follow `agents/fact-checker.md`. Where a page was only partly readable that is noted (the A2UI releases page, the MCP Apps spec tail and one AI SDK page were partly model-summarised; nothing was relied on from a summary where verbatim text conflicted).

## Summary

| Status | Count |
|---|---:|
| VERIFIED | 28 |
| PARTIALLY VERIFIED | 19 |
| UNVERIFIED | 3 |
| CONTESTED | 0 |
| OPINION | 3 |

Total claims checked: 53. None is CONTESTED after reading; the conflicts between earlier readings are resolved below.

## High-impact claims that are not VERIFIED (author must accept or change at Gate 3)

1. **Claim 49** (UNVERIFIED): "in the documents read, no runtime control checks whether content is correct." It is an absence claim and the thesis rests on it. One partial counterexample was found (A2UI's development-time evals).
2. **Claim 33** (UNVERIFIED): no A2UI page says whether data sent back to the agent reaches the model. Absence claim over the pages read.
3. **Claim 50** (UNVERIFIED): no independent evaluation found. Absence claim.
4. **Claim 38** (PARTIALLY VERIFIED): the evals are dev-time and the datasets are encrypted; the draft's "offline" wording is wrong.
5. **Claim 11** (PARTIALLY VERIFIED): "the model does not write the interface" for MCP Apps is an inference.

## Conflicts from earlier readings, now resolved

- The sentence "the data model can be updated directly by the language model during generation" is on **a2ui.org/concepts/data-binding**, not the messages page (Claim 32).
- The AI SDK page does **not** advise validating tool output; its example renders `part.output` directly as props and validates only tool input (Claim 10). Neither earlier reading was fully right.
- The Python agent SDK was 0.12.0 on 17 Nov; the 0.11.0 date and the "a week after" gap are not verified (Claim 43).

## Corrections to apply to the draft (action_required, in priority order)

1. **Claim 2** (Opening): Attribute the tagline to the GitHub README, not the docs. The date claim stands as 'per its docs changelog'.
2. **Claim 4** (Generate from a catalog): Reword: "a flat list in which parent components reference child components by ID, with one component marked root."
3. **Claim 6** (Generate from a catalog): Reword: "allowedCallers defaults to rendererOnly; requiresUserActivation is opt-in and, when set, stops incoming agent messages from triggering navigation without user intent."
4. **Claim 8** (Generate from a catalog): Mark it as an excerpt (add an ellipsis after the last line) and re-copy from the raw README.
5. **Claim 11** (Trigger a shipped UI): Reword: "A tool points to a predeclared `ui://` resource the server supplies; the host fetches it when the model calls the tool." Mark 'the model does not write it' as my reading.
6. **Claim 13** (Trigger a shipped UI): Optional: add that the spec makes the sandbox mandatory for web-page hosts.
7. **Claim 15** (Trigger a shipped UI): Say 'its docs list A2UI, MCP-UI and Open-JSON-UI (its README names MCP Apps)', or drop the list.
8. **Claim 16** (Operate): Use the multi-line form from the page.
9. **Claim 17** (Operate): Reword to "UI SDK components on the page" and add the 100-component snapshot limit if the cap matters.
10. **Claim 18** (Operate): Reword: "runs before a step changes anything and can refuse it."
11. **Claim 22** (Operate (map)): Drop the quotation marks around 'unmarked' or reword to 'components not marked hidden remain visible'.
12. **Claim 23** (Operate): Attribute the two statements to their pages in the source list.
13. **Claim 25** (Write): Reword: "AGENTS.md says `@ui-sdk/core/testing` checks the result against its WAI-ARIA pattern."
14. **Claim 26** (Costs): Say 'the @ui-sdk packages' rather than 'UI SDK 0.1.0-beta.13'.
15. **Claim 27** (What the controls leave open): State that it is the experimental composer's page (the draft does).
16. **Claim 28** (What the controls leave open): Reword: "documented for validating inputs; the agent attaches the rules and the renderer runs them on what a person enters." Drop 'not content an agent authored'.
17. **Claim 30** (What the controls leave open): Replace 'server code' with 'deterministic agent-side code'.
18. **Claim 31** (What the controls leave open): Optional: note the `userMessage` detail, which is explicitly for the LLM.
19. **Claim 32** (What the controls leave open): The draft does not name the page; keep it that way or cite data-binding.
20. **Claim 33** (What the controls leave open): Keep scoped as 'the pages read'. It is a core part of the argument, so the author should accept it explicitly at Gate 3.
21. **Claim 35** (Where content is checked): Reword to 'a rubric attached to each sample'.
22. **Claim 38** (Where content is checked): Replace 'offline' with 'at development time, not at runtime', and add that the datasets are encrypted and the default judge is Gemini. Avoid 'offline' where the project uses it for a different profile.
23. **Claim 40** (Where content is checked): Add 'or escalate'.
24. **Claim 41** (Where content is checked): Keep as stated (no figures cited). If a benchmark is cited later, name Thesys and its pinned versions.
25. **Claim 43** (Costs): Delete 'a week after 0.11.0' or confirm the 0.11.0 release date.
26. **Claim 44** (Costs): State Lynx as 0.9.
27. **Claim 47** (Costs): Say it 'was scheduled to stop on October 31, 2026'; do not claim it has stopped.
28. **Claim 48** (Map): Say 'CopilotKit's spectrum runs from full developer control to full agent autonomy; AG-UI and a community list draw similar lines' and mark it as my reading.
29. **Claim 49** (Opening / Map): Keep the scope 'in the documents read'. The author should accept this at Gate 3, as the thesis rests on it.
30. **Claim 50** (Costs): Keep the scope 'in the sources read'.
31. **Claim 53** (What the controls leave open): Mark the last clause as my reading or cut it.

## Claims

### Claim 1: Opening

```yaml
claim: "Google called A2UI 1.0 \"the first stable version\" of its open protocol for generative UI on 11 November 2026."
status: VERIFIED
sources:
  - "developers.googleblog.com A2UI 1.0 post"
notes: "Blog dateline NOV. 11, 2026; \"Today, we're releasing A2UI 1.0, the first stable version of our open protocol for generative UI.\""
action_required: "None."
```

### Claim 2: Opening

```yaml
claim: "Vercel Labs introduced UI SDK the next day (12 Nov), per its docs changelog; tagline \"a library of behaviors for agents to build the next generation of user interfaces.\""
status: PARTIALLY VERIFIED
sources:
  - "ui-sdk.dev/docs/core/changelog"
  - "github.com/vercel-labs/ui"
notes: "Changelog entry \"Introducing UI SDK\" is dated November 12, 2026. The tagline is on the GitHub README/About, not on ui-sdk.dev/docs (which words it differently)."
action_required: "Attribute the tagline to the GitHub README, not the docs. The date claim stands as 'per its docs changelog'."
```

### Claim 3: Generate from a catalog

```yaml
claim: "A2UI homepage: \"streams declarative JSON data with two-way bindings — never executable code.\""
status: VERIFIED
sources:
  - "a2ui.org"
notes: "Exact on the homepage (capital S)."
action_required: "None."
```

### Claim 4: Generate from a catalog

```yaml
claim: "Messages are JSON with a `version` field; components arrive as a flat list \"that refers to itself by ID\"; bindings use `{\"@path\": \"/reservation/destination\"}`; buttons send actions back with resolved values."
status: PARTIALLY VERIFIED
sources:
  - "a2ui.org/concepts/messages"
  - "a2ui.org/concepts/data-binding"
  - "a2ui.org/concepts/catalogs"
notes: "`version` field, `@path` syntax and resolved action context are all on the pages. 'Refers to itself by ID' is not; the pages say parent components reference child IDs, with one component id \"root\"."
action_required: "Reword: \"a flat list in which parent components reference child components by ID, with one component marked root.\""
```

### Claim 5: Generate from a catalog

```yaml
claim: "A catalog is \"a collection of components and functions that acts as a contract between an agent and a renderer\"; each component is a JSON Schema; \"Agents place only components you registered.\""
status: VERIFIED
sources:
  - "a2ui.org/concepts/catalogs"
  - "a2ui.org"
notes: "All three phrases verbatim."
action_required: "None."
```

### Claim 6: Generate from a catalog

```yaml
claim: "Functions carry permissions: who may call them, and whether a user gesture is required, so that an agent message cannot trigger navigation on its own."
status: PARTIALLY VERIFIED
sources:
  - "a2ui.org/concepts/actions-and-functions"
  - "A2UI evolution guide"
notes: "`allowedCallers` (default `rendererOnly`) is correct. `requiresUserActivation` defaults to false and is opt-in; when true it prevents agent messages from triggering navigation without user intent, and the basic catalog's `openUrl` sets it. The fields are on the actions page, not the catalogs page."
action_required: "Reword: \"allowedCallers defaults to rendererOnly; requiresUserActivation is opt-in and, when set, stops incoming agent messages from triggering navigation without user intent.\""
```

### Claim 7: Generate from a catalog

```yaml
claim: "json-render's README says \"AI can only use components in your catalog\"; its catalog uses Zod schemas; the `description` strings are written for the model to read."
status: VERIFIED
sources:
  - "github.com/vercel-labs/json-render"
notes: "Bullet reads \"Guardrailed - AI can only use components in your catalog\". The README says `catalog.prompt()` \"Includes component descriptions, props schemas, available actions\", which supports that descriptions are model-facing. `import { z } from \"zod\"` is in the Quick Start."
action_required: "None."
```

### Claim 8: Generate from a catalog

```yaml
claim: "The catalog code block matches the json-render README."
status: PARTIALLY VERIFIED
sources:
  - "github.com/vercel-labs/json-render"
notes: "Same tokens and content (the `format: z.enum([...]).nullable()` line is identical). The page presents it as one multi-line block; the draft shows only the start, ending after the Metric entry."
action_required: "Mark it as an excerpt (add an ellipsis after the last line) and re-copy from the raw README."
```

### Claim 9: Generate from a catalog

```yaml
claim: "assistant-ui and Tambo work the same way with Zod schemas."
status: VERIFIED
sources:
  - "assistant-ui.com/docs/tools/generative-ui"
  - "github.com/tambo-ai/tambo"
notes: "assistant-ui: \"declares a zod schema for its props, a description the model reads\" (field named `properties` in its example). Tambo: \"Register your components with Zod schemas.\""
action_required: "None."
```

### Claim 10: Generate from a catalog

```yaml
claim: "The Vercel AI SDK defines generative UI as \"the process of connecting the results of a tool call to a React component\"; the model picks a tool and developer code decides which component renders."
status: VERIFIED
sources:
  - "ai-sdk.dev generative-user-interfaces"
notes: "Sentence verbatim. The page's example renders `<Weather {...part.output} />` after a `part.state` check; the only validation shown is on tool input."
action_required: "None. (Resolves the earlier conflict: the page does not advise validating tool output.)"
```

### Claim 11: Trigger a shipped UI

```yaml
claim: "MCP Apps: a tool declares a `ui://` resource, written by the tool's author ahead of time; the model decides to call the tool and does not write the interface."
status: PARTIALLY VERIFIED
sources:
  - "modelcontextprotocol.io/extensions/apps/overview"
  - "ext-apps spec 2026-01-26"
notes: "The overview says the tool description carries `_meta.ui.resourceUri` pointing to a `ui://` resource; the spec says \"Predeclared resources\" and the resource \"MUST exist on the server\". 'Authored ahead of time by the tool author' and 'the model does not write the interface' are inferences, not statements."
action_required: "Reword: \"A tool points to a predeclared `ui://` resource the server supplies; the host fetches it when the model calls the tool.\" Mark 'the model does not write it' as my reading."
```

### Claim 12: Trigger a shipped UI

```yaml
claim: "The spec is marked \"Stable (2026-01-26)\"."
status: VERIFIED
sources:
  - "ext-apps spec header"
  - "ext-apps README"
notes: "Header: \"Status: Stable (2026-01-26)\"."
action_required: "None."
```

### Claim 13: Trigger a shipped UI

```yaml
claim: "Web hosts typically use a sandboxed iframe; the app talks to the host over JSON-RPC; the host builds the CSP from the domains an app declares."
status: VERIFIED
sources:
  - "MCP Apps overview"
  - "ext-apps spec"
notes: "Overview: \"Web hosts typically render the HTML inside a sandboxed iframe\". Spec: \"JSON-RPC 2.0 over postMessage\"; \"Host MUST construct CSP headers based on declared domains\". For web-page hosts the spec makes the sandbox proxy a MUST."
action_required: "Optional: add that the spec makes the sandbox mandatory for web-page hosts."
```

### Claim 14: Trigger a shipped UI

```yaml
claim: "\"Host support varies by client\" (MCP Apps docs)."
status: VERIFIED
sources:
  - "MCP Apps overview"
notes: "Verbatim. The overview host list (Claude, Claude Desktop, VS Code GitHub Copilot, Microsoft 365 Copilot, Goose, Postman, MCPJam, Archestra.AI) is unchanged; ChatGPT appears only on the repo README; the client-matrix MCP Apps column rendered blank for every row, so ChatGPT, Cursor and Gemini support cannot be confirmed from it."
action_required: "None for the quote. Do not name hosts beyond the overview list."
```

### Claim 15: Trigger a shipped UI

```yaml
claim: "AG-UI's docs say \"AG-UI is not a generative UI specification\" and that it supports A2UI, MCP-UI and Open-JSON-UI."
status: PARTIALLY VERIFIED
sources:
  - "docs.ag-ui.com/concepts/generative-ui-specs"
  - "docs.ag-ui.com/introduction"
  - "github.com/ag-ui-protocol/ag-ui"
notes: "Quote is verbatim (on the concept page). The concept page lists MCP-UI; the intro integration table and the README list MCP Apps instead."
action_required: "Say 'its docs list A2UI, MCP-UI and Open-JSON-UI (its README names MCP Apps)', or drop the list."
```

### Claim 16: Operate

```yaml
claim: "`createAgent` code, `agent.snapshot()` and `agent.act()` examples match the UI SDK docs."
status: PARTIALLY VERIFIED
sources:
  - "ui-sdk.dev/docs/agents/connect-an-agent"
notes: "The `createAgent` block is exact. The `act` example has the same tokens but the page breaks it over three lines."
action_required: "Use the multi-line form from the page."
```

### Claim 17: Operate

```yaml
claim: "The bridge works only on UI SDK components registered with it; the agent reads the registered components and the actions each supports."
status: PARTIALLY VERIFIED
sources:
  - "ui-sdk.dev/docs/agents/connect-an-agent"
notes: "Page: \"connects an agent to the ui-sdk components in your app\"; the bridge \"finds the components already on the page when you create it, and registers new ones as they're created\"; snapshot lists the first 100. 'Registered with it' is an inference."
action_required: "Reword to \"UI SDK components on the page\" and add the 100-component snapshot limit if the cap matters."
```

### Claim 18: Operate

```yaml
claim: "An `allow` callback runs before each step and can refuse it."
status: PARTIALLY VERIFIED
sources:
  - "ui-sdk.dev/docs/agents/connect-an-agent/permissions"
notes: "Page: \"The callback runs before the step changes anything\"; \"Return true to let an action run or false to refuse it.\""
action_required: "Reword: \"runs before a step changes anything and can refuse it.\""
```

### Claim 19: Operate

```yaml
claim: "\"An `allow` that returns `true` without reading `step.confirm` answers yes for the person.\""
status: VERIFIED
sources:
  - "permissions page"
notes: "Verbatim."
action_required: "None."
```

### Claim 20: Operate

```yaml
claim: "A control marked `data-agent-confirm` is meant to need a person."
status: VERIFIED
sources:
  - "permissions page"
notes: "Without `allow` the press fails and asks the person to press it themselves; with `allow` the step waits for the callback and `step.confirm` carries the sentence."
action_required: "None; the draft's hedge ('is meant to') is correct."
```

### Claim 21: Operate

```yaml
claim: "`data-agent-hidden` hides components from the agent; `data-agent-secret` redacts a value."
status: VERIFIED
sources:
  - "permissions page"
notes: "Hidden: left out of `snapshot` and `query`. Secret: value shown as \"[redacted]\" once filled; the agent can still type into it."
action_required: "None."
```

### Claim 22: Operate (map)

```yaml
claim: "What `allow` leaves open: it covers actions; \"unmarked components stay visible in `snapshot()`\"."
status: PARTIALLY VERIFIED
sources:
  - "permissions page"
notes: "Page: \"`allow` checks actions. Components and their actions remain visible in `snapshot()`\". The word 'unmarked' is not on the page (hidden components are excluded)."
action_required: "Drop the quotation marks around 'unmarked' or reword to 'components not marked hidden remain visible'."
```

### Claim 23: Operate

```yaml
claim: "The tools are marked `untrustedContentHint`; the docs say tool results can include text your users wrote."
status: VERIFIED
sources:
  - "ui-sdk.dev WebMCP page"
  - "connect-an-agent page"
notes: "`untrustedContentHint: true` is on the WebMCP page for all three tools; the 'text your users wrote' sentence is on the connect-an-agent page."
action_required: "Attribute the two statements to their pages in the source list."
```

### Claim 24: Write

```yaml
claim: "Install command `npx skills@latest add vercel-labs/ui --skill ui-sdk` is from the README."
status: VERIFIED
sources:
  - "github.com/vercel-labs/ui README"
  - "ui-sdk.dev/docs"
notes: "`@latest` is present in both."
action_required: "None."
```

### Claim 25: Write

```yaml
claim: "UI SDK's AGENTS.md describes testing helpers that check components against WAI-ARIA patterns."
status: PARTIALLY VERIFIED
sources:
  - "github.com/vercel-labs/ui/blob/main/AGENTS.md"
notes: "Exact: \"`@ui-sdk/core/testing` checks the result against its WAI-ARIA pattern, in right to left and on the server.\" The page does not say 'testing helpers'."
action_required: "Reword: \"AGENTS.md says `@ui-sdk/core/testing` checks the result against its WAI-ARIA pattern.\""
```

### Claim 26: Costs

```yaml
claim: "The README says \"UI SDK is in beta\"; 0.1.0-beta.13 was out on 19 November."
status: VERIFIED
sources:
  - "README"
  - "github.com/vercel-labs/ui/releases"
notes: "The @ui-sdk/web, react, vue, svelte and solid packages are 0.1.0-beta.13, released 19 Nov 12:21 (year not shown on the page), all pre-release; no bare repo-level release."
action_required: "Say 'the @ui-sdk packages' rather than 'UI SDK 0.1.0-beta.13'."
```

### Claim 27: What the controls leave open

```yaml
claim: "json-render's docs for its experimental composer say \"Completion is not a correctness guarantee\" and that registering an action does not make it safe to run with arbitrary values."
status: VERIFIED
sources:
  - "json-render.dev/docs/jev"
notes: "Both verbatim; the page is titled \"Jev (Experimental)\"."
action_required: "State that it is the experimental composer's page (the draft does)."
```

### Claim 28: What the controls leave open

```yaml
claim: "A2UI's `@checks` attach to input components; `regex`, `required` and `email` functions are documented for input validation, \"fields a person fills in, not content an agent authored.\""
status: PARTIALLY VERIFIED
sources:
  - "a2ui.org/concepts/catalogs"
  - "a2ui.org/concepts/actions-and-functions"
notes: "`@checks` on inputs and the three functions are documented. The pages do not say they exclude agent content: the agent writes the `@checks` rules inside `updateComponents`, and the renderer runs them against the input value."
action_required: "Reword: \"documented for validating inputs; the agent attaches the rules and the renderer runs them on what a person enters.\" Drop 'not content an agent authored'."
```

### Claim 29: What the controls leave open

```yaml
claim: "The blog says server-side binding means \"sensitive values never reach the model.\""
status: VERIFIED
sources:
  - "Google Developers Blog"
notes: "Sentence: \"A2UI reliably binds to your data and child components on the server, so sensitive values never reach the model.\""
action_required: "None."
```

### Claim 30: What the controls leave open

```yaml
claim: "The docs say server code can inject data into a surface without passing it through the model."
status: PARTIALLY VERIFIED
sources:
  - "a2ui.org/concepts/data-binding"
notes: "Page: \"deterministic code on the agent side ... directly into the surface without passing them through the model\". It says agent-side code, not server code."
action_required: "Replace 'server code' with 'deterministic agent-side code'."
```

### Claim 31: What the controls leave open

```yaml
claim: "Button actions send resolved values to the agent; `sendDataModel` attaches the full surface data model to every message to the agent that created the surface."
status: VERIFIED
sources:
  - "a2ui.org/concepts/messages"
  - "a2ui.org/concepts/data-binding"
notes: "Messages: \"on every message to the creating agent\". Data-binding: \"attach the full surface data model to the transport metadata of every outbound message\". Also: the action `userMessage` is described as \"suitable for adding to LLM conversation history\"."
action_required: "Optional: note the `userMessage` detail, which is explicitly for the LLM."
```

### Claim 32: What the controls leave open

```yaml
claim: "The docs say the data model can be updated by the language model during generation."
status: VERIFIED
sources:
  - "a2ui.org/concepts/data-binding"
notes: "Resolved: it is on the data-binding page (\"Populating the data model\"), not the messages page. Full sentence: \"the data model can be updated directly by the language model during generation, or from deterministic code on the agent side\"."
action_required: "The draft does not name the page; keep it that way or cite data-binding."
```

### Claim 33: What the controls leave open

```yaml
claim: "No A2UI page says whether data sent to the agent's server then reaches the model."
status: UNVERIFIED
sources:
  - "a2ui.org pages read"
notes: "Absence claim. No page read says so; the search covered the blog, home, messages, data-binding, actions, catalogs, roadmap and README only."
action_required: "Keep scoped as 'the pages read'. It is a core part of the argument, so the author should accept it explicitly at Gate 3."
```

### Claim 34: Where content is checked

```yaml
claim: "A2UI's roadmap lists, as available today, \"an eval framework that scores the project datasets with schema checks, assertions, and an LLM judge.\""
status: VERIFIED
sources:
  - "a2ui.org/roadmap"
notes: "Verbatim."
action_required: "None."
```

### Claim 35: Where content is checked

```yaml
claim: "The design has three stages (schema/structure; deterministic assertions such as required components and bindings; an LLM judge that grades against a rubric written for each sample)."
status: PARTIALLY VERIFIED
sources:
  - "eval/DESIGN.md"
notes: "Three stages confirmed. The judge grades against \"the sample's target rubric\"; 'written for each sample' is a fair reading, not literal."
action_required: "Reword to 'a rubric attached to each sample'."
```

### Claim 36: Where content is checked

```yaml
claim: "With the judge switched off, the scorer passes any sample that cleared the first two stages."
status: VERIFIED
sources:
  - "eval/DESIGN.md"
notes: "\"When the run was started with --no-judge, the scorer never calls the model and returns C for a sample that passed Stages 1 and 2.\""
action_required: "None."
```

### Claim 37: Where content is checked

```yaml
claim: "\"Tool usage as a judge\" is on the roadmap, not shipped."
status: VERIFIED
sources:
  - "a2ui.org/roadmap"
notes: "Under \"On the roadmap\"; not in DESIGN.md."
action_required: "None."
```

### Claim 38: Where content is checked

```yaml
claim: "The eval framework runs offline on the project's own datasets."
status: PARTIALLY VERIFIED
sources:
  - "eval/DESIGN.md"
  - "eval/README"
notes: "Datasets are the project's own but Transcrypt-encrypted at rest and need a project key. There is an `--profile offline` that disables the judge, and the default inference and judge provider is Google Gemini; CI runs only Gemini. 'Offline' in the draft means 'at development time, not at runtime', which the page does not use."
action_required: "Replace 'offline' with 'at development time, not at runtime', and add that the datasets are encrypted and the default judge is Gemini. Avoid 'offline' where the project uses it for a different profile."
```

### Claim 39: Where content is checked

```yaml
claim: "A2UI agent-side functions run on the server, with examples such as checking live seat inventory or verifying a booking code."
status: VERIFIED
sources:
  - "a2ui.org/concepts/catalogs"
notes: "\"Agent-side functions, introduced in v1.0, run on the server, such as checking live seat inventory or verifying a booking code.\""
action_required: "None."
```

### Claim 40: Where content is checked

```yaml
claim: "AG-UI lists interrupts, a way to pause for a human to approve, edit or retry."
status: PARTIALLY VERIFIED
sources:
  - "docs.ag-ui.com/introduction"
notes: "Exact: \"Pause, approve, edit, retry, or escalate mid flow without losing state.\""
action_required: "Add 'or escalate'."
```

### Claim 41: Where content is checked

```yaml
claim: "Offline benchmarks of generated UI exist, some run by competing vendors."
status: VERIFIED
sources:
  - "github.com/thesysdev/Generative-ui-bench"
  - "openui.com/benchmarks"
notes: "The repo is under `thesysdev`; openui.com's footer reads Thesys Inc. The benchmark ranks OpenUI against A2UI and json-render. It pins A2UI v0.9 and json-render 0.19, both out of date (A2UI v1.0 and json-render v0.23.2 are current)."
action_required: "Keep as stated (no figures cited). If a benchmark is cited later, name Thesys and its pinned versions."
```

### Claim 42: Costs

```yaml
claim: "A2UI's protocol is 1.0 and its released packages are 0.x, which the release notes show implementing it."
status: VERIFIED
sources:
  - "github.com/a2ui-project/a2ui/releases"
  - "a2ui.org/roadmap"
notes: "Release notes carry \"(v1_0)\" labels (for example agent-sdk 0.12.0: \"Emit @catalogId, @metadata, @accessibility, and @checks on v1.0 components\"); agent-sdk 0.12.0 and a2ui-core 0.7.0 are 0.x. The roadmap lists v1.0 Current. The releases page was only partly readable (first ~40k of ~61k characters verbatim)."
action_required: "None."
```

### Claim 43: Costs

```yaml
claim: "The Python agent SDK was 0.12.0 on 17 November, a week after 0.11.0."
status: PARTIALLY VERIFIED
sources:
  - "github.com/a2ui-project/a2ui/releases"
notes: "0.12.0 on 17 Nov 19:18 is verified. The date of 0.11.0 is not in the verbatim text; the 10 Nov 22:15 timestamp belongs to a2ui-core 0.6.0."
action_required: "Delete 'a week after 0.11.0' or confirm the 0.11.0 release date."
```

### Claim 44: Costs

```yaml
claim: "The announcement says Gemini supports 0.9.1 today, the Jetpack Compose renderer is at 0.9.1, and ByteDance's Lynx renderer is adapting."
status: VERIFIED
sources:
  - "Google Developers Blog"
notes: "\"supports A2UI 0.9.1 today\"; Compose \"currently v0.9.1, and v1.0 coming soon\"; Lynx \"supports A2UI 0.9 today and is adapting to 1.0 with the A2UI team\" (0.9, not 0.9.1)."
action_required: "State Lynx as 0.9."
```

### Claim 45: Costs

```yaml
claim: "The evolution guide says catalogs written for 0.9 \"cannot be used directly\" with 1.0."
status: VERIFIED
sources:
  - "evolution_guide.md"
notes: "\"Catalogs authored for v0.9 cannot be used directly with v1.0 protocol runtimes due to breaking structural changes\"."
action_required: "None."
```

### Claim 46: Costs

```yaml
claim: "The AI SDK's RSC route is \"currently experimental.\""
status: VERIFIED
sources:
  - "ai-sdk.dev/docs/ai-sdk-rsc/overview"
notes: "\"AI SDK RSC is currently experimental. We recommend using AI SDK UI for production.\""
action_required: "None."
```

### Claim 47: Costs

```yaml
claim: "Tambo's README opens with \"Tambo Cloud is shutting down.\""
status: PARTIALLY VERIFIED
sources:
  - "github.com/tambo-ai/tambo"
notes: "Quote verbatim, but the banner is dated language: hosted API was to stop after October 31, 2026 and user data is deleted November 30, 2026. Today is after the first date; the service status was not checked."
action_required: "Say it 'was scheduled to stop on October 31, 2026'; do not claim it has stopped."
```

### Claim 48: Map

```yaml
claim: "CopilotKit's page announces three pillars and shows four bands; vendors' maps (CopilotKit, AG-UI, a community list) each sort by how much freedom the agent has."
status: PARTIALLY VERIFIED
sources:
  - "copilotkit.ai/generative-ui-spectrum"
  - "docs.ag-ui.com/introduction"
  - "narrowin/awesome-generative-ui"
notes: "Three-pillars-versus-four-bands verified. CopilotKit's spectrum runs from developer control to agent autonomy. AG-UI names static and declarative; the community list splits constrained from unconstrained. Calling all three 'sorted by freedom' is a fair reading, not their words."
action_required: "Say 'CopilotKit's spectrum runs from full developer control to full agent autonomy; AG-UI and a community list draw similar lines' and mark it as my reading."
```

### Claim 49: Opening / Map

```yaml
claim: "In the documents read, no runtime control checks whether content is correct."
status: UNVERIFIED
sources:
  - "all pages read"
notes: "Absence claim over a finite reading. The falsification search found one partial counterexample (A2UI's development-time evals) and no runtime content check. It cannot be proven."
action_required: "Keep the scope 'in the documents read'. The author should accept this at Gate 3, as the thesis rests on it."
```

### Claim 50: Costs

```yaml
claim: "\"I found no independent evaluation of reliability, accessibility or security for any of these in the sources read.\""
status: UNVERIFIED
sources:
  - "search results"
notes: "Absence claim; one search pass."
action_required: "Keep the scope 'in the sources read'."
```

### Claim 51: Costs

```yaml
claim: "`allow` and `data-agent-confirm` run in the page, so authorization that matters belongs on the server."
status: OPINION
sources:
  - "(my analysis)"
notes: "The docs do not discuss server-side enforcement. The draft already labels it 'my reading'."
action_required: "None."
```

### Claim 52: The objection

```yaml
claim: "This is least privilege restated; a thin boundary might argue for spending effort elsewhere."
status: OPINION
sources:
  - "(argument)"
notes: "Opinion; not checkable."
action_required: "None."
```

### Claim 53: What the controls leave open

```yaml
claim: "A boundary caps the worst case; the model and any checks set the typical case; a catalog with poor descriptions fails with a good model."
status: OPINION
sources:
  - "(interpretation)"
notes: "The first part is an interpretation. The 'poor descriptions fail with a good model' point is the critic's steelman and has no source."
action_required: "Mark the last clause as my reading or cut it."
```

## Not checked

- A2UI Agent SDK source, eval/tests, conformance; the AI SDK tool-approval and policy pages; MCP Apps spec tail (about 30k characters, read only as a summary); the MCP client matrix (MCP Apps column rendered blank).
- Star counts and release years: the release pages do not show the year; star counts are not cited in v2.
- Quoted code was compared with the live pages by the checkers; re-copy from the raw files before publication all the same.
