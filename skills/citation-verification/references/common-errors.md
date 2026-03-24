# Common Citation Errors in Empirical Economics

Use this note when reviewing citations in economics papers, appendices, and referee responses.

## 1. Working Paper vs. Published Version Confusion

Common mistake:

- citing an `NBER Working Paper` when a journal version already exists
- mixing the working-paper year with the journal-publication year

Preferred fix:

- use the published journal version when the paper relies on the final published result
- keep the working-paper citation only when the paper has not yet appeared in a journal or when the working-paper series is substantively relevant

## 2. Venue Metadata Errors

Common mistake:

- wrong journal name
- missing journal field
- using a vague short label instead of the actual venue

Example:

```bibtex
@article{chetty2011,
  author={Chetty, Raj and Looney, Adam and Kroft, Kory},
  title={Salience and Taxation: Theory and Evidence},
  journal={AER},
  year={2011}
}
```

Better:

```bibtex
@article{chetty2011,
  author={Chetty, Raj and Looney, Adam and Kroft, Kory},
  title={Salience and Taxation: Theory and Evidence},
  journal={American Economic Review},
  year={2011}
}
```

## 3. DOI and URL Errors

Common mistakes:

- storing the full `https://doi.org/...` string in the DOI field
- attaching punctuation to the DOI
- keeping stale URLs when the publisher DOI is available

Preferred fix:

- keep only the DOI in the DOI field
- use a stable publisher or DOI URL when needed

## 4. Author and Title Mismatch

Common mistake:

- title copied from memory
- first author misspelled
- title from working-paper version, venue from journal version

Preferred fix:

- verify against publisher page, DOI landing page, or `NBER/RePEc/IDEAS`
- do not rely on memory

## 5. Duplicate Entries for the Same Paper

Common mistake:

- one BibTeX entry for `NBER Working Paper`
- another for the journal article
- both cited inconsistently in the manuscript

Preferred fix:

- decide which version is substantively correct
- keep one main citation key for the paper discussed in the manuscript

## 6. Claim Does Not Match the Source

Common mistake:

- the cited paper exists, but the specific estimate, mechanism, or identification argument is not actually in that paper

Preferred fix:

- verify the section, table, proposition, or page where the claim appears
- if the claim comes from another version or another paper, cite that source instead

## 7. Inconsistent Citation Style Across the File

Common mistake:

- journal names sometimes abbreviated, sometimes spelled out
- author names mixed between full names and initials
- page ranges formatted inconsistently

Preferred fix:

- choose one consistent house style
- enforce it across the bibliography before submission

## Recommended Economics Sources

Default source order:

1. publisher page / DOI
2. `AEA`, `Econometrica`, `QJE`, `JPE`, `ReStud`, `EJ`, `JPubE`, `JHR`, `AEJ`
3. `NBER`, `RePEc`, `IDEAS`, `SSRN`
4. `Google Scholar` for discovery only
5. `arXiv` only as a fallback for non-economics citations
