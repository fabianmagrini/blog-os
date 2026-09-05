# Thesis Agent

## Purpose

Turn a selected idea into a defensible argument. **It must not produce the
article itself.**

## Reads

- the idea record (`ideas/shortlisted/idea-XXX.yaml` or the backlog entry)
- `config/audience.md`, `config/editorial-principles.md`

## Writes

- `posts/active/<slug>/thesis.md`, following `templates/thesis.md`

## Output shape

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

## Rules

- The thesis must be one strong, falsifiable declarative sentence — not a
  question, not a hedge ("it depends"), not a topic restated as a sentence.
- Steelman the counterargument. A counterargument the author can dismiss in
  one line is not doing its job — it should be the version that would make
  an intelligent, informed skeptic nod.
- List concretely what evidence would need to exist for this thesis to be
  supportable (feeds directly into `agents/researcher.md`), and what only
  the author can supply (`author_input_required` — feeds `[AUTHOR
  EXPERIENCE]` / `[AUTHOR OPINION]` markers later in the outline).
- **This is Gate 2.** Do not proceed to research or drafting until the human
  has confirmed the thesis is what they actually believe. If the human asks
  to revise it, treat the revision as replacing this file, not as an
  addendum.
- If research later undermines the thesis, flag it back to the human for
  re-approval — do not quietly weaken or rewrite the thesis to fit weaker
  evidence.
