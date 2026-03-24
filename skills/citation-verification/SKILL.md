---
name: citation-verification
description: Use when the user needs to verify citations for an empirical economics paper, distinguish working-paper and published versions, check journal metadata, confirm DOI and venue information, or prevent invented references in economics writing.
tags: [Economics, Citation, Verification, Journals, Working Papers]
version: 0.2.0
---

# Citation Verification for Empirical Economics

Use this skill to verify citations for economics papers, referee responses, and appendices.

## Default Source Hierarchy

Prefer sources in this order unless the user asks otherwise:

1. publisher page or DOI landing page
2. `AEA`, `Econometrica`, `QJE`, `JPE`, `ReStud`, `EJ`, `JPubE`, `JHR`, `AEJ`, and field-journal websites
3. `NBER`, `RePEc`, `IDEAS`, `SSRN`
4. `Google Scholar` as a search aid
5. `arXiv` only as a fallback for rare non-economics or cross-disciplinary citations

Do not default to `arXiv-first`.

## What to Verify

For each citation, confirm:

- the paper exists
- title, authors, year, and venue match
- working-paper vs. published version is correctly identified
- DOI or stable URL is available
- the cited claim is actually supported by the source when the paper text relies on a specific result

## Economics-Specific Rules

### Working Paper vs. Published Paper

Economics papers often circulate as:

- working paper only
- working paper plus journal publication
- multiple versions across `NBER`, `SSRN`, `RePEc`, and publisher pages

Default rule:

- cite the published version when it exists and is clearly the final paper the argument relies on
- mention the working-paper series only when it is the relevant accessible version or when the discussion is explicitly about the working-paper stage

### Series and Journal Metadata

Common series and sources to distinguish carefully:

- `NBER Working Paper`
- `IZA Discussion Paper`
- `CEPR Discussion Paper`
- `SSRN Working Paper`
- journal article in the final venue

Do not collapse these into one another.

### Claim Verification

When citing a design, theorem, estimate, or specific empirical finding:

- locate the exact paper version being cited
- verify that the cited claim appears in that version
- note the section, table, proposition, or page when useful for drafting

## Verification Workflow

```text
Need a citation
    ->
Search by title + author
    ->
Confirm with publisher / DOI / NBER / RePEc / SSRN
    ->
Resolve working-paper vs published version
    ->
Verify claim if the draft relies on a specific result
    ->
Only then add to bibliography
```

## Failure Handling

If verification fails:

- do not guess
- mark the citation as unresolved
- tell the user whether the issue is missing paper, conflicting metadata, or unclear versioning
- prefer `[CITATION NEEDED]` or a note in the draft over a fabricated reference

## Best Practices

- never generate economics citations from memory
- separate journal version from working-paper version
- use `Google Scholar` for discovery, not as the only source of truth
- prioritize DOI and publisher metadata when available
- keep citation text and bibliography aligned with the version actually discussed

## Integration

This skill supports:

- `paper-writing`
- `review-response`
- `paper-self-review`
- `qa-paper`
- `qa-response`

Use the older `arXiv`-oriented logic only for explicit non-economics requests.
