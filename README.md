# blog-os

`blog-os` is an agentic operating system for producing high-quality technical
blog posts on a sustainable cadence: **at least one strong article per
month**, without sacrificing quality, originality, or authorial ownership.

> AI can accelerate the writing process, but the author owns the point of view.

Full rationale, philosophy, and design rules: [docs/init-spec.md](docs/init-spec.md).
Operating rules for any agent (human-directed AI, coding agent, or otherwise)
working in this repo: [AGENTS.md](AGENTS.md).

---

## How it works

`blog-os` treats writing as a pipeline, not an event:

```text
Signals → Ideas → Thesis → Research → Outline → Draft → Critique → Revision → Publish → Learn
```

The repository — not any particular chat session or tool — is the system of
record. Every stage produces a durable file. Every agent has a narrow job and
reads only the files it needs. Three points in the pipeline require an
explicit human decision (the **Human Gates**); nothing publishes itself.

```text
Gate 1 — Idea selection     "Is this worth saying?"
Gate 2 — Thesis approval    "Is this what I actually believe?"
Gate 3 — Publication        "Am I prepared to put my name on this?"
```

## Repository layout

```text
config/       audience, themes, voice, editorial principles, source policy
agents/       one file per agent role — its job, inputs, outputs, rules
signals/      raw inbox of things worth noticing, archived once processed
ideas/        the article backlog: shortlisted, rejected, scored
posts/        one working directory per article (active/published/abandoned)
knowledge/    durable research reused across articles (concepts, sources, ...)
templates/    the schema/shape every artifact in the pipeline must follow
workflows/    step-by-step instructions for running one stage of the pipeline
scripts/      future automation entry points (none required for the MVP)
```

See `docs/init-spec.md` §29–30 for the full rationale behind this layout.

## Using this repo today (MVP)

No CLI or automation is required to start. The pipeline runs by invoking an
AI agent (Claude Code, ChatGPT, Gemini CLI, Copilot, etc.) against the
relevant `agents/*.md` file and the relevant `workflows/*.md` file, with the
article's own directory as working context. See
[workflows/discover.md](workflows/discover.md) through
[workflows/publish.md](workflows/publish.md) for the concrete steps of each
stage, and [posts/active/agent-harnesses/](posts/active/agent-harnesses/) for
a worked example of a single article moving through the pipeline.

Conceptually, the stages map to:

```text
blog scout              → collect signals             (workflows/discover.md)
blog ideas               → generate + rank ideas        (workflows/discover.md)
blog start <idea>        → create article workspace     (workflows/develop.md)
blog thesis <article>    → develop the thesis            (workflows/develop.md)
blog research <article>  → build the research dossier    (workflows/research.md)
blog draft <article>     → outline + first draft         (workflows/write.md)
blog review <article>    → critics + fact check           (workflows/review.md)
blog publish <article>   → publication assets             (workflows/publish.md)
```

A real CLI wrapping these is a Phase 2 concern (`docs/init-spec.md` §46), not
a prerequisite.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for how to add signals, ideas, or move
an article through the pipeline.
