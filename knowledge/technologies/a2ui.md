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
