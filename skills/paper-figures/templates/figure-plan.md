# Figure Plan

Use this template before writing `R` plotting code under the `paper-figures` workflow.

This template is designed for empirical economics and agricultural economics papers in which:

- `Stata` handles data cleaning, sample construction, variable generation, aggregation, and exports processed `.dta` files
- `R` imports the processed `.dta` files and produces publication-ready figures

The goal of this sheet is to make the figure’s **analytical purpose** clear before coding begins.

A figure should not be planned as “a nice-looking chart.”  
It should be planned as **one visual answer to one substantive question**.

---

## 1. Basic Figure Information

- **Figure number**:
- **Working figure name**:
- **Main text or appendix**:
- **Planned output filename**:
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

---

## 2. Figure Goal

- **What question is this figure supposed to answer?**  
  [One sentence]

- **Why is this figure needed in the paper?**  
  [One sentence]

- **What should the reader learn from this figure?**  
  [One sentence]

- **Why is a figure better than a table here?**  
  [One sentence]

---

## 3. Narrative Role in the Paper

- **Which section of the paper does this figure support?**
  - introduction
  - institutional background / context
  - data
  - descriptive overview
  - empirical strategy support
  - main results
  - mechanism / heterogeneity
  - robustness
  - appendix
  - other:

- **What paragraph or discussion will introduce this figure?**
- **What part of the broader argument does this figure support?**
- **Is this figure central or supportive?**
  - central
  - supportive
  - appendix-only

---

## 4. Data Source and Handoff

- **Source dataset in `Stata`**:
- **Processed `.dta` filename**:
- **Which Stata script creates this `.dta`?**
- **What sample restrictions are already imposed in `Stata`?**
- **What aggregation or collapse has already been done in `Stata`?**
- **What should `R` still do, if anything, besides plotting?**
  - none
  - light relabeling
  - factor ordering
  - light reshaping for plotting
  - panel assembly
  - other:

---

## 5. Unit of Observation and Scope

- **Unit of observation / aggregation**:
- **Year / period shown**:
- **Geographic scope**:
- **Group / region / category coverage**:
- **Any subgroup restriction**:
- **Any important missing-data rule**:
- **Any weighting or averaging rule that matters for interpretation**:

---

## 6. Main Variables to Plot

- **Main plotted variable(s)**:
- **Displayed unit(s)**:
  - level
  - share
  - percent
  - percentage points
  - index
  - log value
  - standardized value
  - other:
- **Any transformation or normalization**:
- **Any benchmark / reference value in the plot**:
- **Any omitted period / cutoff / baseline group**:

---

## 7. Figure Structure

### If single-panel

- **Planned geometry**:
  - line
  - point
  - line + point
  - bar / column
  - dot plot
  - area / stacked area
  - density / histogram
  - map
  - other:

- **Why is this geometry the right choice?**

### If multi-panel

- **Number of panels**:
- **Panel order**:
- **What does each panel show?**
  - **Panel (a)**:
  - **Panel (b)**:
  - **Panel (c)**:
  - **Panel (d)**:
- **Why do these panels belong together?**
- **What is the intended reading order?**

---

## 8. Visual Mapping Plan

Fill in only what is relevant.

- **x-axis**:
- **y-axis**:
- **color**:
- **fill**:
- **linetype**:
- **point shape**:
- **size**:
- **facet / panel variable**:
- **legend needed?**
  - yes
  - no

- **If yes, what should the legend communicate?**

---

## 9. Comparison Logic

- **What is the primary comparison the reader should make?**
  - over time
  - across groups
  - across regions
  - across categories
  - across panels
  - across specifications
  - other:

- **What is the secondary comparison, if any?**
- **Does the figure need a common scale across groups or panels?**
  - yes
  - no
  - not applicable

- **If not, why not?**

---

## 10. Interpretation Boundary

- **Is this figure descriptive or regression-based?**
  - descriptive
  - regression-based
  - mixed

- **How should the figure be interpreted?**
- **What should the reader not infer from this figure?**
- **Should the caption explicitly say “descriptive”?**
  - yes
  - no
  - not needed

---

## 11. Style Plan

- **Target visual standard**:
  - paper default
  - Nature / Nature-subjournal style
  - appendix style
  - slide style
  - other:

- **Color logic**:
  - black / grey only
  - restrained two-group palette
  - restrained multi-group palette
  - gradient
  - map gradient
  - other:

- **Font family**:
- **Panel label style**:
- **Legend position**:
- **Any direct labeling instead of legend?**
- **Any annotation needed?**
  - zero line
  - treatment timing line
  - north arrow
  - scale bar
  - text labels
  - note on missing values
  - other:

---

## 12. Export Plan

- **Preferred export format**:
  - pdf
  - svg
  - png
  - tiff
  - other:

- **Target width**:
- **Target height**:
- **One-column / two-column / appendix / slide**:
- **Expected export path**:
- **Any grayscale or print-readability concern to check?**

---

## 13. Draft Figure Title

Write a short working title here.

> **Figure X. [Working title]**

---

## 14. Draft One-Sentence Main-Text Introduction

Write one sentence that will introduce the figure in the manuscript.

Examples:

- `Figure X shows the evolution of ... over time.`
- `Figure X compares ... across regions.`
- `Figure X summarizes the descriptive spatial distribution of ...`
- `Figure X presents three related descriptive patterns that motivate the empirical analysis.`

**Draft sentence:**

---

## 15. Draft Figure Message

Write one sentence answering:

> **What is the figure’s main message?**

---

## 16. Main Text vs Appendix Decision

### Current placement choice

- **Planned placement**:
  - main text
  - appendix
  - undecided

### Reason

- **Why does it belong there?**

### Check

- [ ] This figure supports a central part of the narrative
- [ ] This figure is easier to read than the corresponding table
- [ ] This figure does not duplicate another figure unnecessarily
- [ ] This figure is important enough for main-text space  
or
- [ ] This figure is useful but supplementary
- [ ] This figure supports transparency or robustness rather than the core narrative

---

## 17. Pre-Coding Checklist

Before writing the `R` code, check:

- [ ] The figure answers one clear question
- [ ] The processed `.dta` already exists or is clearly defined
- [ ] The sample and aggregation are already settled in `Stata`
- [ ] The main comparison is clear
- [ ] The geometry choice is justified
- [ ] The labels can be made reader-facing
- [ ] The figure will not overstate the evidence
- [ ] The planned caption logic is already clear
- [ ] The figure belongs in the paper for an analytical reason, not only for visual variety

---

## 18. Post-Coding Review Notes

Complete after the first draft of the figure is made.

- **Did the figure successfully show the intended pattern?**
- **What needed revision?**
- **Was the scale readable?**
- **Was the legend or labeling too heavy?**
- **Did the figure look coherent with the rest of the paper?**
- **Does it still deserve main-text placement?**

---

## 19. Final Working Rule

A good figure plan should make it easy to answer before coding starts:

1. what is this figure for?
2. what exact pattern should it show?
3. what data file feeds it?
4. what should the reader compare?
5. how should the figure be interpreted?
6. why does it belong in the paper?

If those questions are still hard to answer, the figure is not yet ready to code.
