# Common Citation Errors in Empirical Economics and Agricultural Economics

Use this note when reviewing citations in economics papers, appendices, and referee responses.

This guide applies especially to empirical microeconomics, policy evaluation, agricultural economics, food and nutrition economics, public economics, labor, development, and related applied field papers.

---

## 1. Working Paper vs. Published Version Confusion

Common mistakes:

- citing a working-paper version when a journal version already exists
- mixing the working-paper year with the journal-publication year
- using the working-paper title together with the journal metadata
- citing a journal version in the manuscript but relying on claims or table numbers from an earlier working-paper version

Preferred fix:

- use the published journal version when the paper relies on the final published result
- keep the working-paper citation only when the paper has not yet appeared in a journal, or when the working-paper series itself is substantively relevant
- if the argument depends on material that only appears in the working-paper version, verify that explicitly instead of assuming the published version is identical
- do not mix title, year, venue, or claim details across versions without checking

---

## 2. Venue Metadata Errors

Common mistakes:

- wrong journal name
- missing journal field
- using an abbreviation instead of the full journal title
- using a working-paper series name for a published article
- citing the wrong field journal because the paper moved across outlets during revision

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

Preferred fix:

- use the full journal title in the `journal` field
- verify the actual publication venue from the publisher page, DOI landing page, or authoritative bibliographic source
- do not rely on memory or shorthand labels

---

## 3. DOI and URL Errors

Common mistakes:

- storing the full `https://doi.org/...` string in the DOI field
- attaching punctuation to the DOI
- placing a DOI in the URL field but leaving the DOI field empty
- keeping stale or unstable URLs when a publisher DOI is available

Preferred fix:

- keep only the DOI string in the DOI field
- use a stable publisher or DOI URL when a URL field is needed
- remove punctuation accidentally attached to DOI strings
- prefer DOI-based links over unstable search-result or session-based URLs

---

## 4. Author and Title Mismatch

Common mistakes:

- title copied from memory
- first author misspelled
- author order incorrect
- title from the working-paper version paired with the journal version
- subtitle omitted or altered in a way that creates mismatch

Preferred fix:

- verify against the publisher page, DOI landing page, or authoritative bibliographic source
- do not rely on memory
- check that author list, title, year, and venue all correspond to the same version

---

## 5. Duplicate Entries for the Same Paper

Common mistakes:

- one BibTeX entry for a working paper
- another BibTeX entry for the journal article
- both cited inconsistently in the manuscript, appendix, and referee response
- duplicate entries with different citation keys and slightly different metadata

Preferred fix:

- decide which version is substantively correct for the manuscript
- keep one main citation key for the paper discussed in the manuscript
- if both versions must be retained, distinguish them clearly and use them consistently for different purposes
- clean duplicates before submission

---

## 6. Claim Does Not Match the Source

Common mistakes:

- the cited paper exists, but the specific estimate, mechanism, or identification argument is not actually in that paper
- the cited paper is relevant background, but not direct support for the sentence
- the manuscript cites a published paper while the specific supporting claim appears only in an earlier working-paper version or in another paper by the same authors
- the referee response overstates what a cited source proves

Preferred fix:

- verify the section, table, proposition, appendix, or page where the claim appears
- distinguish direct evidence from indirect support
- if the claim comes from another version or another paper, cite that source instead
- do not present background literature as if it directly establishes the exact claim at issue

---

## 7. Inconsistent Citation Style Across the File

Common mistakes:

- journal names sometimes abbreviated, sometimes spelled out
- author names mixed between full names and initials
- page ranges formatted inconsistently
- capitalization rules applied unevenly across titles
- some entries include DOI while others omit it without reason

Preferred fix:

- choose one consistent house style
- use full journal names by default unless a journal-specific bibliography style requires otherwise
- enforce the same formatting conventions across the bibliography before submission

---

## 8. Policy, Institutional, and Data Citation Mismatch

Common mistakes:

- citing the wrong policy year
- citing a paper for a policy fact that actually comes from an official document
- citing a secondary paper for a dataset description when the primary dataset documentation should be cited
- using a national policy citation to support a province-level implementation fact without verifying the implementation timing
- mixing official policy dates, pilot dates, and rollout dates

Preferred fix:

- verify policy dates, institutional definitions, and official terminology from primary sources when possible
- cite official policy documents for institutional facts
- cite dataset documentation or official survey documentation for data-source descriptions
- use academic papers to support interpretation, mechanism, or empirical precedent, not to replace primary institutional verification

---

## 9. Appendix Citation Drift

Common mistakes:

- citations updated in the main text but not in the appendix
- appendix tables or notes cite outdated working-paper versions
- variable definitions in the appendix rely on uncited or mismatched sources
- robustness notes refer to literature that is not in the bibliography

Preferred fix:

- cross-check appendix citations separately from the main text
- verify that appendix notes, robustness discussions, and variable-definition sections use the same finalized citations as the manuscript
- ensure all appendix-only citations appear in the bibliography if required by the house style

---

## 10. Referee Response Citation Errors

Common mistakes:

- the response letter cites literature that does not directly address the referee’s concern
- the response claims that “the literature shows” something more strongly than the cited papers support
- the response references manuscript changes and supporting citations inconsistently
- the response uses a citation as if it resolves a design concern when it only offers background context

Preferred fix:

- use citations in referee responses with the same discipline as in the manuscript
- distinguish clearly between:
  - direct support
  - indirect support
  - background context
- verify that citations used to answer referee concerns actually address the specific claim being made
- avoid overstating what the literature establishes

---

## 11. Full Journal Names by Default

Preferred default:

- use full journal names in BibTeX and reference files unless a journal-specific style explicitly requires abbreviation
- keep journal metadata consistent across economics and agricultural economics sources
- do not mix abbreviations and full names within the same bibliography file

Examples of preferred full journal naming:

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
- `American Journal of Agricultural Economics`
- `Applied Economic Perspectives and Policy`
- `Agricultural Economics`
- `European Review of Agricultural Economics`
- `Journal of Agricultural Economics`
- `Food Policy`

---

## Recommended Source Hierarchy for Economics and Agricultural Economics

Default source order:

1. publisher page / DOI landing page
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
5. `Google Scholar` for discovery only
6. `arXiv` only as a fallback for non-economics citations or cross-disciplinary references when no better source is available

---

## Practical Review Rule

Before approving a citation in the manuscript, appendix, or referee response, verify:

- does the paper exist in the cited version?
- do author, title, year, and venue belong to the same version?
- does the specific claim actually appear in the cited source?
- is this the substantively correct version to cite?
- is the citation style consistent with the rest of the bibliography?
- if this is a policy, dataset, or institutional fact, should the citation instead be a primary source?

If any answer is uncertain, mark it for verification rather than assuming it is correct.
