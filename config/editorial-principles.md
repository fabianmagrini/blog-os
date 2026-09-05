# Editorial Principles

## Core principle

> AI can accelerate the writing process, but the author owns the point of view.

## Priority order

When these values conflict, resolve in this order:

```text
Quality → Originality → Credibility → Consistency → Frequency
```

A month with no publishable article is preferable to a month with a weak one
published just to hit cadence.

## Thesis before prose (§6.1)

Never begin an article by producing several thousand words directly. Every
article must establish, in order:

```text
Question → Thesis → Arguments → Evidence → Counterargument → Outline
```

before a full draft is written.

## Evidence before certainty (§6.2)

Externally verifiable claims need reliable evidence. Preferred source order:

1. original research
2. academic papers
3. official documentation
4. source repositories
5. engineering blogs from the people building the technology
6. standards
7. conference presentations
8. reputable technical analysis
9. high-quality secondary reporting

Avoid depending heavily on SEO content farms, uncited summaries, generic
AI-generated content, or unattributed social media claims. Full detail:
`config/source-policy.md`.

## Opinion should be explicit (§6.3)

Every substantial claim in a dossier, outline, or draft should be
classifiable as one of:

```text
FACT
OBSERVATION
INTERPRETATION
OPINION
PREDICTION
```

Agents must never imply they personally experienced something. Personal
experience in an article comes only from the author, inserted at
`[AUTHOR EXPERIENCE]` markers in the outline.

## Critics must be independent (§6.4)

The reasoning path that produced a draft must not be the only reasoning path
that validates it. At minimum, every substantial article passes through:

```text
Technical Critic
Argument Critic
```

Optionally also: Fact Checker, Editorial Critic, Skeptical Reader.

## Non-goals

`blog-os` is not for:

- autonomous publishing without human approval
- high-volume SEO content
- generic AI-written posts
- fabricated sources, experience, opinions, or evidence
- optimizing primarily for clicks
- removing the author from the writing process
- manufacturing controversial opinions on demand
