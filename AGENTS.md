# Agent Instructions

These rules apply to any agent — human-directed AI assistant, autonomous
agent, or coding tool — operating inside `blog-os`, regardless of which model
or platform is running it.

## Core principle

**The author owns the point of view.**

Agents accelerate research, drafting, and critique. They do not decide what
the author believes, and they do not decide what gets published.

## Never

- fabricate sources, quotes, statistics, or citations
- invent or imply personal/lived author experience the author did not provide
- silently change a thesis after it has been approved (`thesis_approved: true`
  in `article.yaml`) — flag the conflict instead and ask for re-approval
- publish or mark an article `published` without explicit human approval at
  Gate 3
- treat model-generated text as evidence for a factual claim
- leave a high-impact factual claim `UNVERIFIED` at publication time without
  the author explicitly accepting that risk
- skip a mandatory pipeline stage (see `docs/init-spec.md` §32, §42) unless
  the human explicitly requests skipping it
- write directly to `posts/published/` — publication moves a workspace there
  only after Gate 3

## Prefer

- primary sources over secondary summaries (`config/source-policy.md`)
- explicit uncertainty over false confidence — mark claims
  FACT / OBSERVATION / INTERPRETATION / OPINION / PREDICTION
  (`docs/init-spec.md` §6.3)
- structured artifacts (the `templates/` schemas) over free-form prose when
  producing an intermediate work product
- independent critique — a draft should be reviewed by an agent that did not
  write it (`agents/technical-critic.md`, `agents/argument-critic.md`)
- concrete technical examples over abstract claims
- visible reasoning through repository files rather than context that only
  exists inside a chat session

## Workflow

1. **Determine the current article state before acting.** Read
   `posts/active/<article>/article.yaml` → `status`. The state machine is
   defined in `docs/init-spec.md` §32. Do not act as if the article is in a
   later or earlier state than its `status` field says.
2. **Read only what the stage needs.** `docs/init-spec.md` §36 (Context
   Strategy) — e.g. the Writer needs `config/audience.md`,
   `config/voice-guide.md`, and the article's `thesis.md` / `research.md` /
   `outline.md`. It does not need the whole repository.
3. **Write outputs to the file the stage owns**, following the matching
   template in `templates/`. Do not invent new file names or shapes for
   artifacts that already have a schema.
4. **Stop at Human Gates.** After idea ranking, after thesis drafting, and
   after voice-editing, present the artifact and wait for an explicit human
   decision before moving the article to the next state. Do not advance
   `status` in `article.yaml` past a gate on your own.
5. **Check quality gates before proposing `ready`.** See
   `docs/init-spec.md` §42. If a gate is unmet, say which one and why,
   rather than marking the article ready anyway.
6. **When in doubt about scope, do less.** A missing citation, an
   unaddressed counterargument, or an unclear thesis is a reason to return
   the artifact for revision, not to paper over it with confident prose.

## Per-agent responsibilities

Each agent's detailed job, inputs, outputs, and constraints live in its own
file under `agents/`. Read the specific agent file for the stage you are
running before acting — this file states the invariants that apply across
all of them.
