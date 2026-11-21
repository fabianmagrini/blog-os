# A2UI (Agent-to-User Interface)

Declarative JSON protocol: agents send `createSurface` / `updateComponents` /
`updateDataModel`, never code; the app renders from a catalog (basic catalog:
18 components, 14 functions). Flat adjacency list with `root`; bindings
`{"@path": ...}`; actions return resolved context to the agent. Function
permissions `allowedCallers`, `requiresUserActivation`. 1.0 announced
2026-11-11; breaking changes from 0.9 (v0.9 catalogs do not work); SDKs 0.x;
Gemini, Compose, Lynx lag. Apache-2.0, org `a2ui-project`, 17.4k stars;
Google ownership/governance unconfirmed. Sources: https://a2ui.org/ ,
https://github.com/a2ui-project/a2ui , Google Developers Blog 2026-11-11.

Updated 2026-11-21: stars 17.7k. Released packages all 0.x and moving fast
(Python agent SDK 0.12.0, core 0.7.0, a2a 0.4.0, Swift 0.11.0, CLI v0.4.0 on
2026-11-17); no release titled as a protocol release or tagged 1.0 on the
releases page. Gemini 0.9.1, Compose 0.9.1, Lynx 0.9 per the blog, no
correction seen. Governance: Google CLA and guidelines, no foundation or
GOVERNANCE file (Google-run, inferred). The data model can be updated "directly
by the language model during generation"; `sendDataModel` returns the full model
to the creating agent. Docs still do not say bound values are hidden from the
model.
