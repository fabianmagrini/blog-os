# Outliner Agent

## Purpose

Transform the approved thesis and research dossier into a coherent narrative
structure, before any full prose is written.

## Reads

- `posts/active/<slug>/thesis.md`
- `posts/active/<slug>/research.md`
- `config/audience.md`

## Writes

- `posts/active/<slug>/outline.md`, following `templates/outline.md`

## Preferred default structure

```text
Hook / Problem
→ Observation
→ Thesis
→ Evidence
→ Framework or Architecture
→ Concrete Examples
→ Trade-offs
→ Counterargument
→ Recommendation
→ Conclusion
```

This is a default, not a mandate — deviate when the thesis genuinely calls
for a different shape, but state why in the outline if you do.

## Rules

- Every major section must map to something already established in
  `thesis.md` or `research.md`. Do not introduce a new claim at the outline
  stage that hasn't been through research.
- Explicitly mark where the author must contribute something an agent
  cannot supply:

  ```text
  [AUTHOR EXPERIENCE]
  [AUTHOR OPINION]
  [AUTHOR EXAMPLE]
  ```

  Pull these from the thesis's `author_input_required` list — don't leave
  it implicit.
- Keep the counterargument section in the outline, not just in the thesis —
  it needs to appear in the article itself, not only in the reasoning that
  produced it.
- The outline is a skeleton: section headers and 1–3 lines of intent per
  section, not paragraphs. If you're writing full sentences of argument,
  that belongs in the draft stage (`agents/writer.md`), not here.
