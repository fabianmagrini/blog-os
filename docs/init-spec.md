# blog-os

## 1. Purpose

`blog-os` is an agentic operating system for producing high-quality technical blog posts on a sustainable cadence.

Its goal is to help an individual author consistently publish at least **one strong post per month** by turning blogging into a repeatable workflow:

```text
Signals
→ Ideas
→ Thesis
→ Research
→ Outline
→ Draft
→ Critique
→ Revision
→ Publish
→ Learn
```

The system should automate the repetitive, research-heavy, and editorial parts of writing while preserving the parts that matter most for authentic authorship:

* choosing what is worth writing about
* deciding what the author believes
* contributing personal experience and judgment
* approving the final article

Core principle:

> AI can accelerate the writing process, but the author owns the point of view.

---

# 2. Goals

`blog-os` should:

1. continuously capture useful signals and potential topics
2. maintain a structured backlog of article ideas
3. rank ideas by usefulness and originality
4. turn selected ideas into strong theses
5. research claims using credible sources
6. produce structured research dossiers
7. generate article outlines
8. draft articles from approved arguments
9. challenge drafts using independent critic agents
10. verify factual claims
11. enforce a consistent author voice
12. prepare content for publication
13. repurpose articles into secondary content
14. retain knowledge from previous articles
15. improve the process over time
16. support a minimum cadence of one published article per month

---

# 3. Non-Goals

`blog-os` is not intended to:

* autonomously publish articles without human approval
* generate high-volume SEO content
* create generic AI-written posts
* fabricate sources, experience, opinions, or evidence
* optimize primarily for clicks
* remove the author from the writing process
* automatically manufacture controversial opinions

The priority order is:

```text
Quality
→ Originality
→ Credibility
→ Consistency
→ Frequency
```

---

# 4. Target Content

The initial focus is long-form technical writing.

Typical themes may include:

* AI-native software engineering
* software architecture
* agentic engineering
* developer platforms
* developer productivity
* AI-native SDLC
* software factories
* platform engineering
* engineering operating models
* developer experience
* frontend architecture
* enterprise architecture
* agent harnesses
* engineering leadership
* emerging developer tools
* cloud architecture
* system design

---

# 5. Target Audience

Primary readers:

* senior software engineers
* principal engineers
* staff engineers
* architects
* engineering managers
* engineering leaders
* heads of engineering
* CTOs
* platform engineers
* technical product leaders

The writing should assume an experienced reader.

Avoid explaining every fundamental concept unless it is necessary to support the argument.

---

# 6. Editorial Philosophy

## 6.1 Thesis before prose

Agents should never begin an article by immediately producing several thousand words.

The system should establish:

```text
Question
→ Thesis
→ Arguments
→ Evidence
→ Counterargument
→ Outline
```

before drafting.

---

## 6.2 Evidence before certainty

Externally verifiable claims should be supported by reliable evidence.

Prefer sources in roughly this order:

1. original research
2. academic papers
3. official documentation
4. source repositories
5. engineering blogs from the people building the technology
6. standards
7. conference presentations
8. reputable technical analysis
9. high-quality secondary reporting

Avoid depending heavily on:

* SEO content farms
* uncited summaries
* generic AI-generated content
* unattributed social media claims

---

## 6.3 Opinion should be explicit

Articles should distinguish:

```text
FACT
OBSERVATION
INTERPRETATION
OPINION
PREDICTION
```

The strongest articles will often combine externally verifiable evidence with the author's professional judgment.

Agents must never imply that they personally experienced something.

---

## 6.4 Critics must be independent

The same reasoning path that produced a draft should not be the only reasoning path used to validate it.

Every substantial article should therefore pass through independent critique.

At minimum:

```text
Technical Critic
Argument Critic
```

Optionally:

```text
Fact Checker
Editorial Critic
Skeptical Reader
```

---

# 7. Operating Model

The fundamental operating loop is:

```text
                   ┌─────────────┐
                   │   Signals   │
                   └──────┬──────┘
                          ↓
                   ┌─────────────┐
                   │    Ideas    │
                   └──────┬──────┘
                          ↓
                   ┌─────────────┐
                   │  Prioritize │
                   └──────┬──────┘
                          ↓
                     HUMAN GATE
                          ↓
                   ┌─────────────┐
                   │   Thesis    │
                   └──────┬──────┘
                          ↓
                     HUMAN GATE
                          ↓
                   ┌─────────────┐
                   │  Research   │
                   └──────┬──────┘
                          ↓
                   ┌─────────────┐
                   │   Outline   │
                   └──────┬──────┘
                          ↓
                   ┌─────────────┐
                   │    Draft    │
                   └──────┬──────┘
                          ↓
                ┌─────────┴─────────┐
                ↓                   ↓
        Technical Critic      Argument Critic
                └─────────┬─────────┘
                          ↓
                       Revise
                          ↓
                     Fact Check
                          ↓
                     Voice Edit
                          ↓
                     HUMAN GATE
                          ↓
                       Publish
                          ↓
                        Learn
```

---

# 8. Human Gates

`blog-os` should deliberately retain human checkpoints.

## Gate 1 — Idea selection

The system recommends ideas.

The human decides:

> Is this worth saying?

---

## Gate 2 — Thesis approval

The system proposes the argument.

The human decides:

> Is this what I actually believe?

---

## Gate 3 — Publication approval

The system presents the completed article.

The human decides:

> Am I prepared to put my name on this?

No publishing workflow should bypass Gate 3.

---

# 9. Agent Model

Each agent should have a focused responsibility.

Recommended initial agent set:

```text
Scout
Editor
Thesis
Researcher
Outliner
Writer
Technical Critic
Argument Critic
Fact Checker
Voice Editor
Publisher
Retrospective
```

Agents should communicate primarily through files rather than hidden conversational context.

This makes the system:

* inspectable
* reproducible
* version controlled
* tool independent
* easy to run with different models

---

# 10. Scout Agent

## Purpose

Discover signals that could eventually become articles.

## Typical sources

The Scout may inspect:

* GitHub
* arXiv
* engineering blogs
* technical newsletters
* documentation releases
* conference talks
* Hacker News
* standards
* research papers
* product announcements
* architecture discussions

## Responsibilities

For each signal:

* summarize what happened
* explain why it matters
* connect it to existing themes
* suggest an interesting writing angle
* identify whether it confirms or contradicts existing assumptions

## Signal schema

```yaml
id: signal-YYYY-MM-DD-001

title:

date:

source:
  name:
  url:
  type:

themes: []

summary:

why_it_matters:

potential_angles: []

related_signals: []

confidence: high | medium | low
```

---

# 11. Idea Agent

The Idea Agent converts one or more signals into article candidates.

A topic is not yet an idea.

Weak:

```text
Agentic coding
```

Strong:

```text
The Agent Harness Is Becoming More Important Than the Model
```

## Idea schema

```yaml
id: idea-001

working_title:

question:

hypothesis:

why_now:

target_reader:

potential_argument:

supporting_signals: []

counterargument:

author_experience_required:

originality_score:

status:
  backlog | shortlisted | selected | rejected
```

---

# 12. Idea Ranking

Ideas should be scored to make selection easier.

Initial scoring dimensions:

| Dimension             | Weight |
| --------------------- | -----: |
| Relevance             |    20% |
| Originality           |    20% |
| Author expertise      |    20% |
| Reader value          |    15% |
| Evidence availability |    15% |
| Timeliness            |    10% |

Each dimension receives a score from 1–5.

Example:

```yaml
scores:
  relevance: 5
  originality: 4
  author_expertise: 5
  reader_value: 5
  evidence: 4
  timeliness: 5
```

The resulting score is advisory rather than authoritative.

---

# 13. Thesis Agent

The Thesis Agent turns an idea into a defensible argument.

It must not produce the article itself.

## Output

```markdown
# Thesis

## Working title

## Question

What question is the article attempting to answer?

## Thesis

One strong declarative sentence.

## Why now

Why is the topic relevant now?

## Argument 1

## Argument 2

## Argument 3

## Counterargument

What would the strongest intelligent skeptic say?

## Response

Why does the thesis still hold?

## Novel contribution

What does this article add that is not already obvious?

## Evidence required

- ...

## Author input required

- ...
```

The article should not proceed until the thesis has been accepted.

---

# 14. Research Agent

The Research Agent investigates the claims needed to support or challenge the thesis.

The goal is not:

> Find everything about this topic.

The goal is:

> Determine whether these claims are supportable.

## Claim record

```yaml
claim:

type:
  factual | interpretive | opinion | prediction

supporting_sources: []

contrary_sources: []

confidence:
  high | medium | low

notes:
```

---

# 15. Source Schema

Every important source should have structured metadata.

```yaml
id:

title:

author:

publisher:

date:

url:

source_type:
  paper |
  documentation |
  repository |
  engineering-blog |
  conference-talk |
  benchmark |
  standard |
  news |
  analysis

primary_source: true | false

relevance:

credibility:

claims_supported: []

notes:
```

---

# 16. Research Dossier

Research output should be a reusable artifact rather than immediately becoming prose.

Example:

```markdown
# Research Dossier

## Article

The Agent Harness Is Becoming More Important Than the Model

## Thesis

...

---

# Claim 1

Model capability is becoming increasingly interchangeable for some engineering tasks.

## Supporting evidence

...

## Contrary evidence

...

## Assessment

...

## Confidence

Medium

---

# Claim 2

Harness design increasingly determines agent reliability.

## Supporting evidence

...

## Contrary evidence

...

## Assessment

...

## Confidence

High

---

# Useful examples

...

# Useful quotes

...

# Open questions

...

# Claims requiring author judgment

...
```

---

# 17. Outline Agent

The Outline Agent transforms thesis and research into a coherent narrative.

Preferred default structure:

```text
Hook / Problem
↓
Observation
↓
Thesis
↓
Evidence
↓
Framework or Architecture
↓
Concrete Examples
↓
Trade-offs
↓
Counterargument
↓
Recommendation
↓
Conclusion
```

The outline should identify places requiring human contribution:

```text
[AUTHOR EXPERIENCE]

[AUTHOR OPINION]

[AUTHOR EXAMPLE]
```

---

# 18. Writer Agent

The Writer produces the first complete article.

Inputs:

```text
thesis.md
research.md
outline.md
voice-guide.md
```

## Writing rules

The Writer should:

* preserve the approved thesis
* prioritize clarity
* use evidence where appropriate
* distinguish opinion from fact
* avoid exaggerated certainty
* use concrete examples
* discuss trade-offs
* write for experienced technical readers
* prefer short paragraphs
* avoid generic introductions

The Writer should not introduce new factual claims without sourcing them.

---

# 19. Technical Critic

The Technical Critic behaves like a skeptical Principal Engineer reviewing the article.

It should search for:

* incorrect terminology
* incorrect technical claims
* outdated information
* hidden assumptions
* missing constraints
* missing failure modes
* architectural oversimplification
* weak comparisons
* unrealistic recommendations
* missing implementation consequences

## Output

```markdown
# Technical Review

## Critical issues

## Major issues

## Minor issues

## Unsupported claims

## Missing trade-offs

## Missing constraints

## Recommended changes
```

---

# 20. Argument Critic

The Argument Critic reviews reasoning rather than technical implementation.

It should challenge:

* the thesis
* causality
* generalization
* logic
* unsupported conclusions
* confirmation bias
* straw-man arguments
* weak counterarguments
* overconfidence
* unoriginal conclusions

## Output

```markdown
# Argument Review

## Strongest part of the argument

## Weakest part

## Unsupported inference

## Missing counterargument

## Areas of excessive certainty

## Sections that add little value

## How the thesis could be stronger
```

---

# 21. Fact Checker

The Fact Checker reviews externally verifiable statements.

Each important claim should receive one of:

```text
VERIFIED
PARTIALLY VERIFIED
UNVERIFIED
CONTESTED
OPINION
PREDICTION
```

Example:

```yaml
claim:

status:

sources: []

notes:

action_required:
```

High-impact factual claims should not remain `UNVERIFIED` at publication time unless explicitly accepted by the author.

---

# 22. Voice Editor

The Voice Editor makes the article sound like the author rather than like a generic language model.

It may change:

* phrasing
* sentence structure
* pacing
* paragraph structure
* transitions
* verbosity

It must not change:

* factual meaning
* thesis
* technical conclusions
* evidence
* citations

---

# 23. Voice Guide

Create:

```text
config/voice-guide.md
```

Initial version:

```markdown
# Voice Guide

## Audience

Experienced software engineers, architects, and engineering leaders.

## Prefer

- direct language
- strong but defensible opinions
- concrete examples
- architecture diagrams
- trade-off analysis
- implementation recommendations
- short paragraphs
- precise technical terminology
- pragmatic conclusions

## Common patterns

Prefer structures such as:

Problem
→ Observation
→ Thesis
→ Model
→ Example
→ Trade-offs
→ Recommendation

## Avoid

- excessive hype
- marketing language
- generic AI optimism
- unnecessarily long introductions
- repeated conclusions
- fake anecdotes
- fake personal experience
- excessive bullet lists
- overuse of rhetorical questions

## Avoid phrases such as

"In today's rapidly evolving landscape"

"Let's dive in"

"It is important to note"

"Game-changing"

"Revolutionary"

"Unlock the power of"

"This paradigm shift"

"The possibilities are endless"
```

This guide should evolve based on published writing.

---

# 24. Publisher Agent

The Publisher prepares the approved article for distribution.

Potential outputs:

```text
article.md
article.html
metadata.yaml
linkedin.md
short-post.md
x-thread.md
diagram-prompts.md
follow-ups.md
```

The Publisher should not significantly alter the argument.

---

# 25. Content Repurposing

One article should become several useful artifacts.

For example:

```text
Article
├── LinkedIn launch post
├── LinkedIn standalone insight
├── short social post
├── X / Bluesky thread
├── diagram
├── presentation outline
├── talk proposal
├── demo idea
└── follow-up article ideas
```

The purpose is not to maximize posting volume.

It is to extract more value from ideas already developed deeply.

---

# 26. Retrospective Agent

After publication, the Retrospective Agent captures what was learned.

Potential inputs:

* page views
* reading time
* reactions
* comments
* LinkedIn engagement
* newsletter engagement
* references from other writers
* author's own observations

Output:

```markdown
# Article Retrospective

## What worked

## What did not work

## Reader reactions

## Arguments readers challenged

## New questions raised

## Follow-up articles

## Changes to the voice guide

## Changes to the editorial process
```

---

# 27. Monthly Operating Cadence

The system should optimize for one substantial article every month.

## Week 1 — Signals and ideas

```text
Scout
→ collect signals
→ generate article ideas
→ rank backlog
```

Target:

```text
5–10 serious article candidates
```

---

## Week 2 — Thesis and research

```text
Human selects idea
→ Thesis Agent
→ human thesis review
→ Research Agent
```

Target:

```text
approved thesis
+
research dossier
```

---

## Week 3 — Writing and critique

```text
Outline
→ Draft
→ Technical Critic
→ Argument Critic
→ Revision
→ Fact Check
```

Target:

```text
publication-quality candidate
```

---

## Week 4 — Editorial and publication

```text
Voice Edit
→ Human Review
→ Publish
→ Repurpose
```

Target:

```text
1 published article
+
supporting content
```

---

# 28. Continuous Workflow

Although the cadence is monthly, the pipeline should not be purely sequential.

Ideally:

```text
Article A → publishing

Article B → research

Article C → thesis

Article D → backlog

Scout → continuously finding future ideas
```

This creates an editorial pipeline rather than a monthly restart.

---

# 29. Repository Structure

Recommended initial structure:

```text
blog-os/
│
├── README.md
├── AGENTS.md
├── CONTRIBUTING.md
│
├── config/
│   ├── audience.md
│   ├── themes.md
│   ├── voice-guide.md
│   ├── editorial-principles.md
│   └── source-policy.md
│
├── agents/
│   ├── scout.md
│   ├── editor.md
│   ├── thesis.md
│   ├── researcher.md
│   ├── outliner.md
│   ├── writer.md
│   ├── technical-critic.md
│   ├── argument-critic.md
│   ├── fact-checker.md
│   ├── voice-editor.md
│   ├── publisher.md
│   └── retrospective.md
│
├── signals/
│   ├── inbox/
│   └── archive/
│
├── ideas/
│   ├── backlog.yaml
│   ├── shortlisted/
│   └── rejected/
│
├── posts/
│   ├── active/
│   ├── published/
│   └── abandoned/
│
├── knowledge/
│   ├── sources/
│   ├── concepts/
│   ├── people/
│   ├── companies/
│   └── technologies/
│
├── templates/
│   ├── signal.yaml
│   ├── idea.yaml
│   ├── thesis.md
│   ├── research.md
│   ├── outline.md
│   ├── article.md
│   ├── technical-review.md
│   ├── argument-review.md
│   └── retrospective.md
│
├── workflows/
│   ├── discover.md
│   ├── develop.md
│   ├── research.md
│   ├── write.md
│   ├── review.md
│   └── publish.md
│
├── scripts/
│
└── .github/
    ├── ISSUE_TEMPLATE/
    └── workflows/
```

---

# 30. Per-Article Structure

Each article should have its own working directory.

Example:

```text
posts/active/agent-harnesses/
│
├── article.yaml
├── thesis.md
├── research.md
├── outline.md
│
├── drafts/
│   ├── v1.md
│   ├── v2.md
│   └── final.md
│
├── reviews/
│   ├── technical.md
│   ├── argument.md
│   └── fact-check.md
│
├── sources/
│   └── sources.yaml
│
├── assets/
│   ├── diagrams/
│   └── images/
│
└── publish/
    ├── article.md
    ├── article.html
    ├── linkedin.md
    └── social.md
```

This preserves the reasoning and editorial history behind each post.

---

# 31. Article Metadata

`article.yaml`

Example:

```yaml
id: agent-harnesses

title: The Agent Harness Is Becoming More Important Than the Model

status: research

created: 2026-09-01

target_publish_date: 2026-09-30

themes:
  - ai-native-engineering
  - coding-agents
  - developer-platforms

audience:
  - principal-engineers
  - architects
  - engineering-leaders

word_count_target: 2200

thesis_approved: false

publication_approved: false
```

---

# 32. Article State Machine

Recommended states:

```text
idea
↓
selected
↓
thesis
↓
research
↓
outline
↓
draft
↓
review
↓
revision
↓
ready
↓
published
```

Alternative exits:

```text
abandoned
deferred
merged
```

An article should always have an explicit state.

---

# 33. AGENTS.md

The root `AGENTS.md` should describe how any coding or reasoning agent should operate inside `blog-os`.

Example principles:

```markdown
# Agent Instructions

## Core principle

The author owns the point of view.

## Never

- fabricate sources
- fabricate quotes
- invent author experience
- silently change an approved thesis
- publish without approval
- treat model-generated text as evidence

## Prefer

- primary sources
- explicit uncertainty
- structured artifacts
- independent critique
- concrete technical examples
- visible reasoning through repository files

## Workflow

Always determine the current article state before acting.

Do not skip mandatory stages unless explicitly requested.
```

---

# 34. Commands

The system should eventually support simple commands.

Conceptually:

```bash
blog scout
```

Collect signals.

```bash
blog ideas
```

Generate and rank ideas.

```bash
blog start <idea>
```

Create a new article workspace.

```bash
blog thesis <article>
```

Develop the thesis.

```bash
blog research <article>
```

Build the research dossier.

```bash
blog draft <article>
```

Generate the first draft.

```bash
blog review <article>
```

Run critics and fact checking.

```bash
blog publish <article>
```

Prepare publication artifacts.

The first implementation does not need a CLI.

Markdown workflows are sufficient initially.

---

# 35. Tool Independence

`blog-os` should not depend on a single AI platform.

Agents should communicate through repository artifacts so that individual stages can be executed using:

* ChatGPT
* Codex
* Claude Code
* GitHub Copilot
* Gemini CLI
* Amp
* local models
* future agent harnesses

The repository should be the system of record.

Models are interchangeable workers.

---

# 36. Context Strategy

Agents should receive the minimum useful context.

For example, the Writer should generally receive:

```text
config/audience.md
config/voice-guide.md
article/thesis.md
article/research.md
article/outline.md
```

It should not necessarily receive the entire repository.

This reduces:

* irrelevant context
* instruction conflicts
* token consumption
* accidental stylistic drift

---

# 37. Knowledge Base

Research from previous articles should become reusable knowledge.

Example:

```text
knowledge/
├── concepts/
│   ├── agent-harness.md
│   ├── agentic-sdlc.md
│   └── software-factory.md
│
├── technologies/
│   ├── agentcore.md
│   ├── strands.md
│   └── langgraph.md
│
└── sources/
```

This prevents repeated research and allows future agents to connect ideas across articles.

---

# 38. Source Policy

`config/source-policy.md` should define research expectations.

Example:

```markdown
# Source Policy

Prefer primary sources.

For important claims:

- locate the original source where possible
- record the publication date
- distinguish observation from interpretation
- include contrary evidence
- note uncertainty
- never invent citations

A secondary source should not be used when the primary source is easily available.
```

---

# 39. Automation Strategy

Automate the low-risk parts first.

Recommended automation sequence:

## Stage 1

Automate:

```text
signal collection
idea generation
idea ranking
```

Keep writing manual or explicitly invoked.

---

## Stage 2

Automate:

```text
research collection
source extraction
claim checking
critic reviews
```

---

## Stage 3

Introduce workflow orchestration.

For example:

```text
selected article
   ↓
Research Agent
   ↓
Research complete
   ↓
Outline Agent
   ↓
Writer
   ↓
Critics
```

Human gates remain.

---

# 40. GitHub Integration

GitHub should act as both:

```text
content repository
+
workflow engine
```

Potential use of Issues:

```text
Idea
Research Needed
Article
Editorial Task
```

Potential labels:

```text
signal
idea
selected
research
draft
review
ready
published
blocked
```

Pull requests can become the editorial review mechanism for substantial article changes.

---

# 41. Future GitHub Actions

Potential workflows:

```text
weekly-scout.yml
```

Collect new signals.

```text
validate-sources.yml
```

Check source metadata and broken URLs.

```text
article-check.yml
```

Validate required files and metadata.

```text
publish.yml
```

Generate publication formats after human approval.

```text
monthly-retrospective.yml
```

Generate a summary of editorial activity.

---

# 42. Quality Gates

An article should not become `ready` unless:

```text
✓ thesis exists

✓ thesis approved

✓ research dossier exists

✓ important factual claims have sources

✓ counterargument considered

✓ technical review complete

✓ argument review complete

✓ fact check complete

✓ voice edit complete

✓ human review complete
```

---

# 43. Definition of Done

A blog post is done when:

* the thesis is clear
* the author agrees with the thesis
* the argument is coherent
* significant factual claims are supported
* meaningful counterarguments have been addressed
* technical recommendations include trade-offs
* AI filler has been removed
* the article sounds consistent with the author's voice
* publication assets have been created
* the author has explicitly approved publication

---

# 44. Metrics

Do not optimize primarily for engagement.

Track both output and quality.

## Process metrics

```text
signals collected
ideas created
ideas selected
articles started
articles published
time from idea → publish
research sources/article
articles abandoned
```

## Outcome metrics

```text
posts/month
readers
completion rate
comments
meaningful technical discussions
citations/backlinks
newsletter subscribers
social engagement
```

## Primary metric

Initially:

> Publish at least one article each month that the author is genuinely satisfied to put their name on.

---

# 45. Initial MVP

The MVP should deliberately be simple.

No custom application is required.

Start with:

```text
GitHub
+
Markdown
+
YAML
+
AI coding/research agents
```

MVP capabilities:

```text
✓ signal inbox

✓ idea backlog

✓ idea scoring

✓ article workspace

✓ thesis template

✓ research dossier

✓ Writer Agent

✓ Technical Critic

✓ Argument Critic

✓ voice guide

✓ publishing template
```

Everything can initially be invoked manually.

---

# 46. Phase 2

After several articles, add:

```text
automated weekly Scout

research automation

source validation

CLI

GitHub Issue integration

GitHub Actions

article state validation

automatic derivative content generation
```

---

# 47. Phase 3

Potential future direction:

```text
                    Blog OS

                       │
              Editorial Orchestrator

                       │
     ┌─────────────────┼─────────────────┐
     ↓                 ↓                 ↓
 Research Agents   Writing Agents    Review Agents
     │                 │                 │
     └─────────────────┼─────────────────┘
                       ↓
                Knowledge Graph
                       ↓
                  Publisher
                       ↓
                   Analytics
                       ↓
                  Learning Loop
```

At that point, `blog-os` becomes a genuine personal editorial agent system rather than simply a collection of prompts.

---

# 48. Design Principle

The repository should embody one architectural rule:

> **The repository owns the workflow. Agents perform the work.**

This means:

* state lives in files
* sources are persisted
* decisions are visible
* drafts are version controlled
* models can be replaced
* agent prompts can evolve independently
* human decisions remain explicit

That makes `blog-os` both useful today and compatible with future agent tooling.

---

# 49. Success Criteria

Within the first three months, `blog-os` should enable:

```text
3+ high-quality published articles

50+ captured signals

15+ serious article ideas

a reusable research knowledge base

a stable author voice guide

a repeatable research → publish workflow
```

Most importantly, starting a new article should no longer feel like starting from an empty page.

The system should always have:

```text
signals waiting
ideas developing
research accumulating
articles moving through the pipeline
```

That continuous editorial pipeline is the central value of `blog-os`.
