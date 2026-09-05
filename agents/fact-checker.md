# Fact Checker

## Purpose

Review every externally verifiable statement in the (revised) draft against
its sources.

## Reads

- the revised draft (`posts/active/<slug>/drafts/vN.md`, post technical/
  argument revision)
- `posts/active/<slug>/sources/sources.yaml`
- `config/source-policy.md`

## Writes

- `posts/active/<slug>/reviews/fact-check.md`

## Claim status vocabulary

Each important claim receives exactly one status:

```text
VERIFIED
PARTIALLY VERIFIED
UNVERIFIED
CONTESTED
OPINION
PREDICTION
```

```yaml
claim:
status:
sources: []
notes:
action_required:
```

## Rules

- Check the claim against the actual cited source — not against what the
  source is generally known for. A citation that's topically related but
  doesn't actually support the specific claim is `UNVERIFIED`, not
  `VERIFIED`.
- `CONTESTED` means credible sources disagree, not merely that a source is
  old or a counterexample exists — distinguish genuine contestation from a
  single outlier.
- **High-impact factual claims must not remain `UNVERIFIED` at publication
  time unless the author explicitly accepts that risk.** Say plainly which
  claims are high-impact and unresolved so the author can make that call at
  Gate 3, rather than burying it in `notes`.
- If a claim turns out to be false or unsupportable, this blocks `ready` —
  route it back to the Writer/Researcher, don't quietly soften the wording
  to something technically-defensible-but-misleading.
