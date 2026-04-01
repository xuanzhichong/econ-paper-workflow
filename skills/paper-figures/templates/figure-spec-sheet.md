# Figure Specification Sheet

Use this template to record the **technical and substantive specification** of one figure under the `paper-figures` workflow.

This sheet is designed for empirical economics and agricultural economics papers in which:

- `Stata` handles data cleaning, sample construction, variable generation, aggregation, and exports processed `.dta` files
- `R` imports the processed `.dta` files and produces publication-ready figures

The purpose of this sheet is to make each figure:

- traceable
- reproducible
- easy to revise
- easy to describe in the manuscript
- easy to align with the `Stata -> R` handoff logic

This is a **working specification document**, not a polished manuscript artifact.

---

## 1. Basic Figure Metadata

- **Figure number**:
- **Working figure name**:
- **Main text or appendix**:
- **Figure type**:
  - descriptive trend
  - group comparison
  - structure / composition
  - distribution
  - map
  - multi-panel figure
  - coefficient plot
  - event-study figure
  - other:
- **Current status**:
  - planned
  - drafting
  - revised
  - finalized

---

## 2. Figure Purpose

- **Main analytical purpose**:
- **What question does this figure answer?**
- **Why is a figure better than a table here?**
- **What should the reader learn from it in one sentence?**

---

## 3. Data Provenance

- **Source analytical dataset in `Stata`**:
- **Processed `.dta` filename used for plotting**:
- **Which Stata script creates this `.dta`?**
- **Date of latest `.dta` generation**:
- **Does this figure use one `.dta` or multiple `.dta` files?**
  - one
  - multiple

### If multiple, list them here:

- `.dta` file 1:
- `.dta` file 2:
- `.dta` file 3:

---

## 4. Sample Definition

- **Unit of observation / aggregation**:
- **Time period shown**:
- **Geographic coverage**:
- **Group / category coverage**:
- **Any subgroup restriction**:
- **Any year restriction**:
- **Any sample exclusion that matters for interpretation**:
- **Any weighting rule used before export from `Stata`**:
- **Any missing-data rule that matters for the figure**:

---

## 5. Variable Specification

### Main plotted variable(s)

- **Variable 1**:
- **Variable 2**:
- **Variable 3**:

### Reader-facing names

- **Display label 1**:
- **Display label 2**:
- **Display label 3**:

### Units

- **Displayed unit(s)**:
  - level
  - share
  - percent
  - percentage points
  - index
  - log value
  - standardized value
  - other:

### Construction notes

- **How was the variable constructed in `Stata`?**
- **Any transformation / normalization / scaling?**
- **Any benchmark or baseline value?**
- **Any omitted category / omitted period / reference category?**

---

## 6. Figure Geometry Specification

- **Primary geometry**:
  - line
  - point
  - line + point
  - bar / column
  - dot plot
  - area / stacked area
  - density / histogram
  - map
  - other:

- **Why is this geometry appropriate?**
- **Any secondary geometry used?**
  - error bars
  - reference line
  - shaded band
  - text labels
  - other:

- **What is the main comparison structure?**
  - over time
  - across groups
  - across regions
  - across categories
  - across panels
  - across specifications
  - other:

---

## 7. Visual Mapping Specification

Fill only what is relevant.

- **x-axis variable**:
- **y-axis variable**:
- **group variable**:
- **color variable**:
- **fill variable**:
- **linetype variable**:
- **shape variable**:
- **facet / panel variable**:
- **label variable**:
- **ordering variable**:

### Mapping logic

- **Why is this mapping the right one for the figure?**
- **What should the reader compare first?**
- **What should the reader compare second?**

---

## 8. Scale Specification

- **x-axis title**:
- **y-axis title**:
- **Legend title**:
- **Scale type**:
  - continuous
  - discrete
  - date / year
  - map gradient
  - other:

- **Common scale across panels?**
  - yes
  - no
  - not applicable

- **If no, why not?**
- **Any transformation of displayed scale?**
  - log
  - percent
  - centered
  - normalized
  - none
  - other:

- **Reference line needed?**
  - zero line
  - average line
  - treatment timing line
  - cutoff line
  - none
  - other:

---

## 9. Panel Specification (if multi-panel)

### Panel layout

- **Single-panel or multi-panel**:
  - single-panel
  - multi-panel

- **Number of panels**:
- **Planned layout**:
  - side by side
  - stacked
  - grid
  - one large + smaller panels
  - other:

### Panel details

- **Panel (a)**:
- **Panel (b)**:
- **Panel (c)**:
- **Panel (d)**:

### Panel logic

- **Why do these panels belong together?**
- **What is the intended reading order?**
- **Does panel order match the manuscript logic?**
  - yes
  - no
  - needs revision

---

## 10. Style Specification

- **Target style**:
  - default paper style
  - Nature / Nature-subjournal style
  - appendix style
  - slide style
  - other:

- **Font family**:
- **Base font size**:
- **Panel label style**:
- **Color strategy**:
  - black / grey only
  - restrained two-group palette
  - restrained multi-group palette
  - gradient
  - diverging gradient
  - map palette
  - other:

- **Legend placement**:
- **Direct labeling instead of legend?**
  - yes
  - no
  - partial

- **Any annotation planned?**
  - note on missing values
  - north arrow
  - scale bar
  - panel titles
  - confidence intervals
  - omitted period marker
  - other:

---

## 11. Interpretation Specification

- **Evidence type**:
  - descriptive
  - regression-based
  - mixed

- **What the figure supports**:
  - descriptive context
  - identification support
  - main empirical result
  - mechanism interpretation
  - heterogeneity interpretation
  - robustness
  - appendix transparency
  - other:

- **What the figure should not be interpreted as**:
- **Should the caption explicitly say “descriptive”?**
  - yes
  - no
  - not needed

- **Any claim-strength caution needed?**
- **Any wording that must be avoided?**

---

## 12. Manuscript Linkage

- **Which section cites this figure?**
- **Which paragraph introduces this figure?**
- **Does the figure correspond to a table as well?**
  - yes
  - no

- **If yes, which table?**
- **Does the figure duplicate a table too closely?**
  - yes
  - no
  - partly

- **If yes, why is the figure still needed?**

---

## 13. Caption Specification

- **Short title for caption**:
- **One-sentence caption summary**:
- **Must the caption state sample / year / aggregation?**
  - yes
  - no

- **Must the caption define intervals / omitted period / missing values?**
  - yes
  - no
  - not applicable

- **Draft note needed?**
  - yes
  - no

- **If yes, what must the note clarify?**

---

## 14. Export Specification

- **R script filename**:
- **Output filename**:
- **Output format**:
  - pdf
  - svg
  - png
  - tiff
  - other:

- **Target width**:
- **Target height**:
- **Units**:
- **Target use**:
  - one-column
  - two-column
  - appendix
  - slide
  - other:

- **Export directory**:
- **Does the exported filename match manuscript figure numbering?**
  - yes
  - no
  - temporary

---

## 15. Revision Log

### Round 1
- **Date**:
- **What changed**:
- **Why**:

### Round 2
- **Date**:
- **What changed**:
- **Why**:

### Round 3
- **Date**:
- **What changed**:
- **Why**:

Use more rounds if needed.

---

## 16. Quality Checks

Before treating the figure as submission-ready, check:

### Data and provenance
- [ ] The `.dta` source file is clearly identified
- [ ] The sample and aggregation are already settled in `Stata`
- [ ] The plotted variables are clearly defined
- [ ] The figure does not depend on undocumented substantive transformations in `R`

### Design
- [ ] The geometry matches the analytical purpose
- [ ] The main comparison is clear
- [ ] The ordering is meaningful
- [ ] The labels are reader-facing
- [ ] The scales are honest and readable
- [ ] The visual hierarchy is clean

### Interpretation
- [ ] The evidence type is clear
- [ ] The figure does not overstate the evidence
- [ ] The figure supports the manuscript narrative clearly
- [ ] The figure belongs in the main text or appendix for a good analytical reason

### Reproducibility
- [ ] The R script and output filename are explicit
- [ ] The export format and dimensions are specified
- [ ] Another reader could reproduce the figure from this sheet plus the scripts

---

## 17. Final One-Sentence Figure Definition

Complete this line before finalizing:

> **This figure is a [figure type] that uses [processed `.dta` / data source] to show [main pattern] for [sample / unit / period], and it supports the paper by [narrative role].**

---

## 18. Working Rule

A good figure specification sheet should make it easy to answer:

1. what exactly is this figure?
2. what data file feeds it?
3. what sample and variables does it use?
4. how is it visually constructed?
5. how should it be interpreted?
6. how is it linked to the manuscript?

If those questions are still hard to answer, the figure is not yet well specified enough for smooth revision and submission.
