# Figure Caption Sheet

Use this template to draft a manuscript-ready caption for a figure produced under the `paper-figures` workflow.

This sheet is designed for empirical economics and agricultural economics papers in which:

- `Stata` prepares the processed `.dta` file
- `R` produces the final figure
- the figure is intended for a journal-ready manuscript
- the visual style should remain clear, restrained, and consistent with **Nature / Nature-subjournal** expectations when relevant

This is a **working template**, not a rigid form.  
Complete only the parts that are useful for the specific figure.

---

## 1. Basic Figure Information

- **Figure number**:
- **Short figure title**:
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

---

## 2. Figure Purpose

- **What is this figure supposed to show?**  
  [One sentence]

- **Why is this figure in the paper?**  
  [One sentence]

- **What should the reader learn from it?**  
  [One sentence]

---

## 3. Data and Scope

- **Input `.dta` file**:
- **Sample**:
- **Unit of observation / aggregation**:
- **Year / period shown**:
- **Group / region / category coverage**:
- **Any important restriction already imposed in `Stata`**:

---

## 4. Variable Information

- **Main plotted variable(s)**:
- **Displayed unit(s)**:
  - level
  - share
  - percent
  - percentage points
  - index
  - log value
  - other:
- **Any transformation or normalization**:
- **How missing values are handled / displayed**:

---

## 5. Evidence Type

- **This figure is primarily**:
  - descriptive
  - regression-based
  - event-study based
  - coefficient-summary based
  - mixed

- **Interpretation boundary**:
  [e.g., "This figure is descriptive and should not be interpreted as causal evidence."]

---

## 6. Panel Information (if multi-panel)

### Panel structure

- **Panel (a)**:
- **Panel (b)**:
- **Panel (c)**:
- **Panel (d)**:

### Panel logic

- **Why do these panels belong together?**
- **What is the intended reading order?**

---

## 7. Construction Notes

Complete only if relevant.

- **Values shown are**:
  - raw means
  - weighted means
  - totals
  - shares
  - rates
  - regression coefficients
  - event-study coefficients
  - other:

- **Confidence intervals / standard errors shown?**
  - yes
  - no

- **If yes, specify type**:
  - 95% confidence interval
  - 90% confidence interval
  - standard error bars
  - other:

- **Omitted period / reference category / normalization**:
- **Map merge key or spatial unit**:
- **Grouped leads/lags or binned categories**:
- **Other construction detail needed for interpretation**:

---

## 8. Draft Caption: Short Version

Write a compact working caption here.

> **Figure X. [Short title].**  
> [One to three sentences describing what is shown, for what sample / period, and how it should be interpreted.]

---

## 9. Draft Caption: Full Version

Write the fuller manuscript-ready caption here.

> **Figure X. [Full title].**  
> [Sentence 1: what the figure shows.]  
> [Sentence 2: sample, period, or unit of observation.]  
> [Sentence 3: construction detail, if needed.]  
> [Sentence 4: interpretation boundary, if needed.]

---

## 10. Optional Figure Note

Use this only if the journal style or figure complexity makes a separate note useful.

**Note:**  
[State omitted period, confidence interval type, missing-value display, weighting, map shading logic, grouped endpoints, or other technical details.]

---

## 11. Suggested Main-Text Reference

Draft one sentence for the manuscript body that introduces the figure.

Examples:

- `Figure X shows the evolution of ... over time.`
- `Figure X compares ... across regions.`
- `Figure X summarizes the descriptive spatial distribution of ...`
- `Figure X presents the event-study estimates around ...`

**Draft sentence:**

---

## 12. Claim-Strength Check

Before finalizing, confirm the caption does **not** overstate the figure.

### Check the caption for the following:

- [ ] It clearly says what is plotted
- [ ] It states the sample / year / unit when relevant
- [ ] It distinguishes descriptive from regression-based evidence
- [ ] It does not make a stronger claim than the figure supports
- [ ] It defines intervals, omitted periods, or normalization when needed
- [ ] It explains each panel clearly if the figure is multi-panel
- [ ] It uses reader-facing language, not raw variable names

---

## 13. Common Caption Patterns

### Descriptive trend figure

> **Figure X. Trend in [variable] over time.**  
> The figure reports [national / regional / subgroup-specific] average values of [variable] from [start year] to [end year] for [sample]. The figure is descriptive.

### Group comparison figure

> **Figure X. Comparison of [variable] across [groups].**  
> The figure reports average [variable] for [groups] in [year / period / sample]. Values are [means / shares / totals]. The figure is descriptive.

### Structure / composition figure

> **Figure X. Composition of [outcome] in [year].**  
> The figure reports the shares of [components] in [aggregate] for [sample]. Shares sum to [100% / total value] unless otherwise noted.

### Map figure

> **Figure X. Geographic distribution of [variable], [year].**  
> The map reports [province-level / county-level] average values of [variable] for [sample] in [year]. Darker shades indicate higher values. Grey areas indicate missing values. The figure is descriptive.

### Coefficient plot

> **Figure X. Estimated effects across [outcomes / subgroups / specifications].**  
> Points indicate coefficient estimates, and horizontal lines indicate 95% confidence intervals. Estimates correspond to the specification reported in Table X.

### Event-study figure

> **Figure X. Event-study estimates around [policy / treatment].**  
> Points indicate event-study coefficient estimates, and vertical bars indicate 95% confidence intervals. The omitted period is \( t = -1 \). The vertical line separates pre-treatment and post-treatment periods. See Table X for the corresponding specification.

### Multi-panel figure

> **Figure X. Descriptive patterns of [topic].**  
> Panel (a) shows [content]. Panel (b) reports [content]. Panel (c) displays [content]. All panels are [descriptive / based on the same regression specification / otherwise specified].

---

## 14. Final Working Rule

A good caption should let the reader answer quickly:

1. what is this figure showing?
2. for what sample or period?
3. how was it constructed?
4. how should it be interpreted?
5. what should not be over-interpreted?

If the caption does not make those points easy to recover, revise it before treating the figure as submission-ready.
