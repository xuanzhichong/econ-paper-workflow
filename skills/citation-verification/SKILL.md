---
name: citation-verification
description: Use when the user needs to verify citations for an empirical economics or agricultural economics paper, distinguish working-paper and published versions, check journal metadata, confirm DOI and venue information, verify policy or data-source citations, or prevent invented references in economics writing.
tags: [Economics, Agricultural Economics, Citation, Verification, Journals, Working Papers]
version: 0.3.0
---

# Citation Verification for Empirical Economics and Agricultural Economics

Use this skill to verify citations for economics and agricultural economics papers, referee responses, appendices, policy background sections, and data-description sections.

## When to Use

Use this skill when the user needs to:

- verify whether a cited paper actually exists
- distinguish a working-paper version from a published journal version
- confirm title, authors, year, venue, DOI, or URL metadata
- verify that a cited claim is actually supported by the cited source
- check policy, institutional, or dataset citations
- prevent invented, distorted, or mismatched references in economics writing

## Default Source Hierarchy

Prefer sources in this order unless the user asks otherwise:

1. publisher page or DOI landing page
2. top general economics journals and publisher records:
   - `American Economic Review`
   - `Quarterly Journal of Economics`
   - `Journal of Political Economy`
   - `Econometrica`
   - `Review of Economic Studies`
   - `Economic Journal`
   - `Journal of Public Economics`
   - `Journal of Human Resources`
   - `American Economic Journal: Applied Economics`
   - `American Economic Journal: Economic Policy`
   - `American Economic Journal: Microeconomics`
   - `American Economic Journal: Macroeconomics`
3. leading agricultural economics and related field journals:
   - `American Journal of Agricultural Economics`
   - `Applied Economic Perspectives and Policy`
   - `Agricultural Economics`
   - `European Review of Agricultural Economics`
   - `Journal of Agricultural Economics`
   - `Food Policy`
4. major working-paper and bibliographic sources:
   - `National Bureau of Economic Research`
   - `RePEc`
   - `IDEAS`
   - `SSRN`
   - other well-identified working-paper series when relevant
5. `Google Scholar` as a discovery tool only
6. `arXiv` only as a fallback for rare non-economics or cross-disciplinary citations

Do not default to `arXiv-first`.

## What to Verify

For each citation, confirm:

- the paper exists
- title, authors, year, and venue match the same version
- working-paper vs. published version is correctly identified
- DOI or stable URL is available when relevant
- the cited claim is actually supported by the source when the manuscript relies on a specific result
- the source is the substantively correct version to cite

When relevant, also verify:

- policy year
- pilot / rollout timing
- institutional terminology
- dataset or survey documentation
- appendix-only references
- response-letter claims about what the literature shows

## Economics- and Agricultural-Economics-Specific Rules

### Working Paper vs. Published Paper

Economics and agricultural economics papers often circulate as:

- working paper only
- working paper plus journal publication
- multiple versions across `National Bureau of Economic Research`, `SSRN`, `RePEc`, `IDEAS`, and publisher pages

Default rule:

- cite the published version when it exists and is clearly the final paper the argument relies on
- keep the working-paper citation only when the paper has not yet appeared in a journal, when the working-paper series is substantively relevant, or when the cited content appears only in that version

Do not mix:

- working-paper title with journal metadata
- working-paper year with publication year
- claim details from one version with venue information from another

### Series and Journal Metadata

Common sources to distinguish carefully:

- `National Bureau of Economic Research Working Paper`
- `IZA Discussion Paper`
- `CEPR Discussion Paper`
- `SSRN Working Paper`
- final journal article in the published venue

Do not collapse these into one another.

### Journal Names

Default rule:

- use full journal names in citation files unless a specific house style explicitly requires abbreviations
- keep journal metadata consistent across economics and agricultural economics references
- do not mix abbreviations and full names within the same bibliography file

### Policy, Institutional, and Data Citations

For policy facts, institutional background, and data descriptions:

- prefer primary official sources when possible
- verify policy dates and rollout timing from official documents rather than relying only on secondary papers
- cite survey documentation or official dataset documentation for data-source descriptions
- use academic papers to support interpretation, mechanism, or empirical precedent, not to replace primary institutional verification

## Claim Verification

When citing a design, theorem, estimate, mechanism, identification argument, or specific empirical finding:

- locate the exact paper version being cited
- verify that the cited claim appears in that version
- note the section, table, proposition, appendix, or page when useful for drafting
- distinguish direct support from indirect support or background context

Do not present background literature as if it directly proves the exact sentence in the manuscript or referee response.

## Verification Workflow

```text
Need a citation
    ->
Search by title + author
    ->
Confirm with publisher / DOI / journal site / NBER / RePEc / IDEAS / SSRN
    ->
Resolve working-paper vs published version
    ->
Verify claim if the draft relies on a specific result
    ->
Check whether policy or dataset facts require a primary source
    ->
Only then add to bibliography
```

## Output Expectations

When reporting verification results, classify each item as one of:

- `VERIFIED`
- `UNRESOLVED`
- `VERSION CONFLICT`
- `METADATA CONFLICT`
- `CLAIM MISMATCH`
- `CITATION NEEDED`

When useful, report:

- verified citation metadata
- whether the published or working-paper version should be used
- DOI or stable URL
- whether the cited claim is directly supported
- what remains uncertain
- what source should be checked next

## Failure Handling

If verification fails:

- do not guess
- do not fabricate
- mark the citation as unresolved
- tell the user whether the issue is:
  - missing paper
  - conflicting metadata
  - unclear versioning
  - unsupported claim
  - missing primary source
- prefer `[CITATION NEEDED]` or an explicit verification note over a fabricated reference

## Best Practices

- never generate economics or agricultural economics citations from memory
- separate journal versions from working-paper versions
- use `Google Scholar` for discovery, not as the only source of truth
- prioritize DOI and publisher metadata when available
- keep citation text and bibliography aligned with the version actually discussed
- cross-check appendix citations separately when the appendix may contain stale references
- apply the same verification discipline to referee responses as to the manuscript itself

## Integration

This skill supports:

- `paper-writing`
- `review-response`
- `paper-self-review`
- `qa-paper`
- `qa-response`

Use older `arXiv`-oriented logic only for explicit non-economics requests.
