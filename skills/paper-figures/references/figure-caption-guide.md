# Figure Caption Guide for Empirical Economics and Agricultural Economics

Use this guide when writing figure captions for empirical economics and agricultural economics papers.

This guide is designed for workflows in which:

- `Stata` handles data cleaning, sample construction, aggregation, and estimation
- `R` handles figure production, layout, styling, and export

The purpose of a figure caption is **not** to decorate the figure.  
Its purpose is to make the figure:

- interpretable
- traceable
- properly limited in claim strength
- readable without forcing the reader to reverse-engineer the plot

A good caption should help the reader understand **what is shown, how it was constructed, and how it should be interpreted**.

---

## 1. Core Principle

A figure caption should allow a careful reader to answer quickly:

1. what is being plotted?
2. on what sample?
3. at what unit of observation or aggregation?
4. how was the figure constructed?
5. how should the figure be interpreted?
6. where does it fit in the paper’s empirical logic?

A caption should be **specific enough to decode the figure**, but not so long that it becomes a substitute for the main text.

---

## 2. What a Good Caption Should Usually Contain

Depending on the figure type, a strong caption should state, as relevant:

- what is plotted
- sample
- unit of observation
- time period
- variable definition or outcome label
- whether the figure is descriptive or regression-based
- estimator or construction method
- confidence interval or standard error type
- omitted period / cutoff / normalization if relevant
- panel meanings for multi-panel figures
- where the corresponding table or section appears, if useful

Not every caption needs every element.  
But every caption should contain enough information for the reader to interpret the figure correctly.

---

## 3. Caption Functions

A good figure caption usually performs one or more of the following functions:

### 3.1 Decode the figure

It tells the reader what the points, lines, bars, colors, or shaded regions represent.

### 3.2 Define the scope

It tells the reader what sample, time period, or geographic unit is shown.

### 3.3 Clarify construction

It explains whether the figure is:

- descriptive
- aggregated from raw data
- based on regression estimates
- based on event-study coefficients
- mapped from regional averages
- built from grouped categories or collapsed means

### 3.4 Limit interpretation

It prevents the reader from overreading the figure, especially when the figure is descriptive rather than causal.

---

## 4. Default Caption Logic by Figure Type

## 4.1 Descriptive Trend Figures

A good descriptive trend caption should usually state:

- what variable is plotted
- over what time period
- for what sample
- whether the values are raw means, weighted means, or other descriptive summaries
- whether the figure is descriptive

### Example structure

> **Figure X. Trend in [outcome] over time.**  
> The figure reports [national / regional / subgroup-specific] average values of [outcome] from [start year] to [end year] for [sample]. Values are [raw means / weighted means / province-level averages]. The figure is descriptive.

---

## 4.2 Group Comparison Figures

A good group-comparison caption should usually state:

- what groups are being compared
- what variable is plotted
- sample and time period
- whether values are means, shares, totals, or normalized values

### Example structure

> **Figure X. Comparison of [outcome] across [groups].**  
> The figure reports average [outcome] for [groups] in [sample / year / period]. Values are [means / shares / aggregated values]. The figure is descriptive and is intended to summarize cross-group differences.

---

## 4.3 Composition or Structure Figures

A good composition caption should usually state:

- what the components are
- whether the values are shares or levels
- what year or sample is used
- whether the composition sums to a total

### Example structure

> **Figure X. Composition of [outcome / expenditure / intake / structure] in [year].**  
> The figure reports the share of [components] in [aggregate]. Values are computed for [sample] in [year]. Shares sum to [100% / total value] unless otherwise noted.

---

## 4.4 Distribution or Density Figures

A good distribution caption should usually state:

- what variable is distributed
- sample
- whether the plot shows raw values, trimmed values, or transformed values
- whether the figure is descriptive

### Example structure

> **Figure X. Distribution of [variable].**  
> The figure reports the distribution of [variable] for [sample]. Values are [raw / log-transformed / trimmed at ...]. The figure is descriptive.

---

## 4.5 Maps

A good map caption should usually state:

- what variable is mapped
- geographic unit
- year or period
- whether values are averages, totals, or rates
- how missing values are shown
- that the figure is descriptive unless it is clearly model-based

### Example structure

> **Figure X. Geographic distribution of [variable], [year].**  
> The map reports [province-level / county-level] average values of [variable] for [sample] in [year]. Darker shades indicate higher values. Grey areas indicate missing values. The figure is descriptive.

---

## 4.6 Event-Study Figures

A good event-study caption should usually state:

- what the points represent
- what the intervals represent
- omitted period
- treatment timing convention
- whether grouped leads/lags are used
- where the specification is reported
- sample if not obvious

### Example structure

> **Figure X. Event-study estimates around [treatment / policy adoption].**  
> Points indicate event-study coefficient estimates, and vertical bars indicate 95% confidence intervals. The omitted period is \( t = -1 \). The vertical line separates pre-treatment and post-treatment periods. See Table X for the corresponding specification and sample definition.

---

## 4.7 Coefficient Plots

A good coefficient-plot caption should usually state:

- what estimates are shown
- what the intervals represent
- whether all estimates come from the same specification family
- where the matching regression table appears

### Example structure

> **Figure X. Estimated effects across outcomes.**  
> Points indicate coefficient estimates for the treatment variable, and horizontal lines indicate 95% confidence intervals. Estimates correspond to the baseline specification reported in Table X.

---

## 4.8 Multi-Panel Figures

A good multi-panel caption should usually state:

- the overall logic of the figure
- what each panel contains
- sample or construction rules where needed
- whether all panels are descriptive or whether some are regression-based

### Example structure

> **Figure X. Descriptive patterns of [topic].**  
> Panel (a) shows [content]. Panel (b) reports [content]. Panel (c) displays [content]. All panels are constructed from Stata-processed analytical datasets and are descriptive unless otherwise noted.

---

## 5. Caption Length Discipline

A caption should be:

- long enough to decode the figure
- short enough to remain readable
- more detailed when the figure is technically constructed
- shorter when the figure is straightforward

Working rule:

- simple descriptive plots usually need a compact caption
- event-study, coefficient, map, and multi-panel figures usually need more detail

Avoid captions that are:

- so short the figure cannot be understood
- so long they repeat the results section paragraph by paragraph

---

## 6. Descriptive vs Regression-Based Captions

This distinction is essential.

### Descriptive caption language

Use phrases such as:

- `The figure reports ...`
- `The figure shows ...`
- `Values are computed as ...`
- `The figure is descriptive.`
- `The figure summarizes ...`

### Regression-based caption language

Use phrases such as:

- `Points indicate coefficient estimates ...`
- `Bars indicate 95% confidence intervals.`
- `The omitted period is ...`
- `Estimates are based on ...`
- `See Table X for the corresponding specification.`

Do not let a descriptive figure caption sound causal.  
Do not let a regression-based caption omit the identifying construction that matters for interpretation.

---

## 7. Claim-Strength Discipline

Captions should not make stronger claims than the design supports.

Prefer:

- `The figure is descriptive.`
- `The graphical pattern is consistent with ...`
- `The figure summarizes ...`
- `The figure reports estimated coefficients ...`

Avoid:

- `The figure proves that ...`
- `The figure demonstrates the causal mechanism ...`
- `The map shows the policy effect ...` when the map is only descriptive
- `The trend confirms ...` when the evidence is only supportive

A caption should clarify interpretation, not inflate it.

---

## 8. Panel Label Discipline

When a figure has multiple panels:

- identify each panel clearly
- use `(a)`, `(b)`, `(c)` or journal-consistent alternatives
- describe each panel in the caption in the same order that the reader sees them
- keep descriptions parallel in wording where possible

Good pattern:

- `Panel (a) shows ...`
- `Panel (b) reports ...`
- `Panel (c) displays ...`

Do not force the reader to guess which panel corresponds to which sentence.

---

## 9. Notes vs Captions

In some papers, the figure may have both a **caption** and a **note**.

A useful division is:

### Caption

Use for:

- what the figure is
- what each panel shows
- the main construction logic

### Note

Use for:

- sample details
- interval type
- omitted period
- weighting
- missing-value treatment
- map shading logic
- technical clarifications

If the journal style uses only captions, incorporate the most essential note content into the caption.

---

## 10. Good Caption Patterns

### General descriptive figure

- `Figure X. [Short title]. The figure reports ...`
- `Figure X. [Short title]. The figure shows ...`

### Trend figure

- `Figure X. Trend in ... from ... to ....`
- `Figure X. Evolution of ... over time.`

### Comparison figure

- `Figure X. Comparison of ... across ....`
- `Figure X. Group differences in ....`

### Map figure

- `Figure X. Geographic distribution of ..., [year].`
- `Figure X. Regional variation in ..., [year].`

### Event-study figure

- `Figure X. Event-study estimates around ....`
- `Figure X. Dynamic treatment effects relative to ....`

### Coefficient plot

- `Figure X. Estimated effects across ....`
- `Figure X. Coefficient estimates by outcome / subgroup / specification.`

### Multi-panel figure

- `Figure X. Descriptive patterns of ....`
- `Figure X. Multi-panel summary of ....`

---

## 11. Common Mistakes

Avoid the following:

- writing captions that are too vague to decode the figure
- omitting sample or year when it matters
- omitting omitted period in event-study captions
- using causal language for descriptive figures
- failing to explain what the intervals represent
- failing to explain panel meanings
- using raw variable names instead of reader-facing labels
- making the caption longer than the surrounding paragraph while still not clarifying the key construction
- letting the caption and figure title imply different things

---

## 12. Caption Consistency Rules

Before finalizing, check that the caption is consistent with:

- figure title
- axis labels
- legend wording
- manuscript terminology
- table terminology
- section narrative
- appendix references

If the manuscript says `animal-based protein share`, the figure caption should not suddenly say `animal protein ratio` unless that difference is intentional and defined.

---

## 13. Working Rule

A good figure caption should let the reader answer quickly:

1. what is this figure showing?
2. what sample or unit does it use?
3. how was it constructed?
4. how should I interpret it?
5. what should I not over-interpret?

If those questions are not easy to answer from the caption, the figure is not yet reader-ready.
