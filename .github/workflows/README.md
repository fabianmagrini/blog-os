# .github/workflows/

No GitHub Actions yet — automation is Phase 2 (`docs/init-spec.md` §41,
§46). Once the manual pipeline (`workflows/*.md`) has proven itself,
candidates to add here, in rough order of risk:

```text
validate-sources.yml       check source metadata / broken URLs
article-check.yml          validate required files + metadata per state
weekly-scout.yml            collect new signals on a schedule
monthly-retrospective.yml   summarize editorial activity
publish.yml                 generate publication formats after human approval
```

`publish.yml` in particular must never remove the human approval step
(Gate 3, `docs/init-spec.md` §8) — it should generate assets after
`publication_approved: true` is already set, not decide to set it.
