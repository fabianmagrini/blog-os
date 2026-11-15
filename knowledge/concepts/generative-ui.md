# Generative UI: jobs, boundaries and projects (as of 2026-11-15)

Three jobs an agent can do with an interface, and where the developer-owned
boundary sits:

| Job | Examples | Boundary |
|---|---|---|
| Emit UI (constrained) | A2UI 1.0, json-render, assistant-ui, Tambo, AI SDK tool UIs | Component catalog (Zod or JSON Schema) |
| Emit UI (unconstrained) | MCP Apps (`ui://` HTML in a sandboxed iframe) | Sandbox, CSP, auditable postMessage |
| Write UI code | UI SDK skill, v0-style generators | Tested behaviors, tests, review |
| Operate UI | UI SDK `createAgent` / WebMCP | Permission layer (`allow`, confirm, secret) |

AG-UI is transport ("not a generative UI specification"), not a UI format.
Maturity: A2UI protocol 1.0 but SDKs 0.x and Gemini/Compose/Lynx on 0.9.x;
UI SDK 0.1.0-beta.2; json-render 0.22.0; AI SDK RSC experimental; MCP Apps spec
Stable 2026-01-26; Tambo Cloud shutting down (OSS continues).

Caution: A2UI's "sensitive values never reach the model" is only partly
supported by its docs (actions and `sendDataModel` return values to the agent).
Existing taxonomies (CopilotKit spectrum, AG-UI, awesome-list) are vendor or
community and inconsistent. Source detail:
`posts/active/generative-ui-a2ui-ui-sdk/sources/sources.yaml`.
