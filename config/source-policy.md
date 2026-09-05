# Source Policy

Prefer primary sources.

For important claims:

- locate the original source where possible
- record the publication date
- distinguish observation from interpretation
- include contrary evidence
- note uncertainty
- never invent citations

A secondary source should not be used when the primary source is easily
available.

## Preferred source order

1. original research
2. academic papers
3. official documentation
4. source repositories
5. engineering blogs from the people building the technology
6. standards
7. conference presentations
8. reputable technical analysis
9. high-quality secondary reporting

## Every important source needs metadata

Use the schema in `docs/init-spec.md` §15 (mirrored in a source record under
`knowledge/sources/` or an article's `sources/sources.yaml`):

```yaml
id:
title:
author:
publisher:
date:
url:
source_type: paper | documentation | repository | engineering-blog |
             conference-talk | benchmark | standard | news | analysis
primary_source: true | false
relevance:
credibility:
claims_supported: []
notes:
```

## Fact-check thresholds

High-impact factual claims must not remain `UNVERIFIED` at publication time
unless the author explicitly accepts that risk. See `agents/fact-checker.md`
for the full claim-status vocabulary.

## What counts as a citation failure

- a URL that returns 404 or has clearly moved
- a claim attributed to a source that does not actually say it
- a statistic with no traceable origin
- a quote that cannot be located in the cited source

Any of these blocks an article from reaching `ready` (`docs/init-spec.md`
§42).
