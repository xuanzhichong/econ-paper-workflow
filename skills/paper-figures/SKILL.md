---
name: paper-figures
description: Use when the user wants to turn empirical economics or agricultural economics results into publication-ready figures using R. Default workflow assumes Stata handles data cleaning, sample construction, and econometric estimation, while R handles figure data import, visualization, multi-panel layout, styling, and export. Handles Chinese prompts such as "画图", "可视化", "event study 图", "系数图", "拼图", and "Nature 风格图片".
version: 0.1.0
---

# Paper Figures for Empirical Economics and Agricultural Economics

Use this skill when the user wants to produce **journal-ready figures** from empirical economics or agricultural economics results.

Default workflow:

- `Stata` handles raw-data cleaning, merging, sample construction, variable generation, and econometric estimation
- `R` handles figure data intake, reshaping for plotting, visualization, panel composition, annotation, and export

This skill is for **paper figures**, not for general-purpose R programming, dashboard building, or ML experiment visualization.

## Core Principle

Figures should serve one or more of the following functions:

1. clarify the identifying design
2. summarize a main empirical result
3. reveal dynamic treatment effects
4. present heterogeneity or mechanism evidence clearly
5. show descriptive patterns that support, but do not replace, the regression evidence

A figure should make the argument **clearer than a table alone could**, not merely more decorative.

## Default Figure Standard

Unless the user specifies otherwise, default to a style that is:

- clean
- publication-ready
- restrained
- readable in grayscale
- consistent with **Nature / Nature-subjournal visual expectations**

This means:

- minimalist visual design
- strong typographic hierarchy
- no unnecessary chartjunk
- careful use of color
- precise axis labeling
- balanced whitespace
- consistent line widths, point sizes, and font sizes
- polished multi-panel alignment
- captions and notes that make the figure interpretable without overselling the result

## Default Workflow

```text
Clarify figure purpose
    ->
Audit Stata output and identify plot-ready data
    ->
Define figure type and panel logic
    ->
Map variables to visual elements
    ->
Write R plotting plan
    ->
Generate publication-ready figure
    ->
Export with stable filename and journal-ready dimensions
    ->
Draft caption and figure note
```

## What This Skill Should Produce

Typical outputs include:

- `figure-plan.md`
- `figure-spec-sheet.md`
- `figure-caption-sheet.md`
- complete runnable `R` code for the figure
- publication-ready outputs such as `.pdf`, `.svg`, or high-resolution `.png` when requested

Generate only what is needed for the user's task.  
If the user asks only for plotting code, prioritize a complete runnable R script.

## Default Inputs

This skill expects inputs such as:

- `Stata` regression outputs
- plot-ready `.dta`, `.csv`, or `.xlsx` exported from `Stata`
- coefficient tables
- event-study output tables
- descriptive summary tables
- map shapefiles or spatial data if needed
- user-provided figure sketches or screenshots
- journal target or style preference if available

Do **not** assume that `R` will do the main cleaning.  
If data are not yet plot-ready, the default recommendation is:

- prepare the plot-ready dataset in `Stata`
- then use `R` for visualization

## Default Figure Families

Prioritize these figure families for empirical economics and agricultural economics papers.

### 1. Event-study figures

Use when the paper estimates dynamic treatment effects.

Typical requirements:

- coefficient by relative time
- 95% confidence intervals
- omitted period clearly labeled
- treatment timing or policy year visually marked where relevant
- grouped leads/lags disclosed if used
- y-axis units clearly stated
- no misleading smoothing

### 2. Coefficient plots

Use when the paper needs to compare:

- baseline vs robustness estimates
- subgroup effects
- mechanism estimates
- multiple outcomes with the same treatment

Typical requirements:

- point estimate plus confidence interval
- stable ordering across panels
- comparable axis scales when substantive comparison matters
- labels with economic meaning, not raw variable names

### 3. Descriptive trend plots

Use when showing:

- treated vs control raw trends
- pre-policy evolution
- stylized facts that motivate the design
- outcome evolution over time

Typical requirements:

- clear distinction between descriptive and causal evidence
- sample and aggregation level disclosed
- raw vs adjusted series labeled clearly

### 4. Heterogeneity forest / interval plots

Use when subgroup comparison is central.

Typical requirements:

- subgroup labels with theoretical meaning
- point estimate plus interval
- no overloaded legend
- avoid implying significance differences where only point differences are shown

### 5. Mechanism figures

Use sparingly.

Typical requirements:

- should support interpretation, not substitute for identification
- visual logic should match the mechanism specification
- wording and caption should remain cautious

### 6. Maps and spatial figures

Use when spatial allocation, rollout, clustering, or geographic heterogeneity matters.

Typical requirements:

- clean projection and region boundaries
- readable labels
- restrained color use
- spatial meaning explained clearly
- avoid decorative mapping without analytical purpose

### 7. Multi-panel composite figures

Use when several related figures belong together.

Typical requirements:

- consistent theme and scales where appropriate
- panel labels such as `(a)`, `(b)`, `(c)`
- balanced spacing
- one coherent caption structure

## Stata-to-R Division of Labor

Default rule:

- `Stata` should produce the **figure-ready dataset**
- `R` should produce the **figure-ready graphic**

### Stata should usually handle

- raw-data cleaning
- merge / append / reshape for analysis
- sample selection
- variable construction
- estimation
- exporting regression results or plot data
- collapsing or reshaping into a plot-ready table when needed

### R should usually handle

- importing figure-ready data
- light reshaping for plotting
- ordering factors and labels
- plotting
- styling
- faceting and multi-panel composition
- legend handling
- export

Do not silently rebuild the analytical sample in `R` unless the user explicitly wants that.

## Nature-Style Figure Defaults

When the user asks for figures that match **Nature** or **Nature-subjournal** style, default to the following principles.

### Visual hierarchy

- clean and compact overall structure
- moderate font size with consistent scaling across text elements
- panel labels clear but not oversized
- enough whitespace to avoid crowding
- legend placement chosen to minimize eye movement

### Color

- use restrained, publication-safe palettes
- avoid overly saturated colors
- ensure the figure remains interpretable in grayscale
- use color to distinguish analytically meaningful groups, not decoration
- for event-study and coefficient plots, let intervals remain legible and secondary to the point estimate

### Lines and points

- line widths should be readable but not heavy
- point sizes should be visible but not bulky
- confidence intervals should be easy to read and not overpower the figure
- reference lines should be subtle but visible

### Axes and scales

- axis titles must include units where relevant
- tick marks should be readable and not too dense
- avoid truncated axes unless clearly justified
- avoid hidden scale choices that exaggerate or mute economically important variation

### Legends and labels

- direct labeling is preferred when it improves readability
- legends should be concise and harmonized with text terminology
- subgroup names should match the manuscript exactly

### Export

Preferred formats by default:

- vector output: `.pdf` or `.svg`
- high-resolution raster only when required
- stable figure dimensions for one-column or two-column layouts
- reproducible export code in the R script

## Figure Planning Rules

Before writing code, define:

- the exact purpose of the figure
- which section of the paper it supports
- whether it belongs in the main text or appendix
- what the reader should learn from it in one sentence
- which variables map to:
  - x-axis
  - y-axis
  - color
  - linetype
  - point shape
  - facet / panel
- whether the figure is descriptive or tied directly to an estimating result

A figure is not ready to code until its analytical purpose is clear.

## Caption and Note Discipline

A good figure caption or note should state, as relevant:

- what is plotted
- sample
- unit of observation
- estimator or construction
- confidence interval or standard error type
- omitted period / cutoff / normalization
- whether the figure is descriptive or regression-based
- panel meanings if multi-panel

Do not let captions overclaim causality relative to the design.

## Writing Discipline for Figures

Figures should be described in manuscript prose using disciplined language.

Preferred patterns include:

- `Figure X presents the event-study estimates around ...`
- `The pre-treatment coefficients provide no strong evidence of ...`
- `The graphical pattern is consistent with the regression results in Table X.`
- `These subgroup patterns should be interpreted as supportive rather than definitive evidence.`

Avoid:

- benchmark language
- decorative interpretation
- stronger causal claims in the figure caption than in the text
- using the figure to imply a claim the regression design does not support

## Common Figure Risks

Watch for the following:

- omitted period not labeled in event-study figures
- incomparable axis scales across supposedly comparable panels
- overloaded legends
- colors that fail in grayscale
- coefficient plots combining fundamentally different specifications
- map figures with weak analytical purpose
- multi-panel figures with inconsistent themes
- captions too vague to decode the figure
- figure titles that overstate causality
- `R` code that silently reconstructs the sample differently from `Stata`

## Recommended R Ecosystem

Default packages may include, as needed:

- `ggplot2`
- `dplyr`
- `tidyr`
- `readr`
- `haven`
- `patchwork`
- `cowplot`
- `sf`
- `showtext`
- `scales`
- `grid`
- `gridExtra`
- `forcats`
- `stringr`
- `ggrepel`
- `ggtext`
- `viridisLite`
- `RColorBrewer`
- `magick` for panel composition when needed

Do not load many packages without purpose.  
Prefer a lean, transparent figure script.

## Default Output Discipline

When generating R scripts or figure plans, default to:

- one script per major figure, or one script per tightly related figure family
- stable file names that match manuscript figure numbering when possible
- explicit import path for plot-ready data
- explicit export path
- clearly separated:
  - setup
  - data import
  - label preparation
  - plotting
  - export

## Example Output Naming

Preferred examples:

- `fig1_descriptive_trends.R`
- `fig2_event_study.R`
- `fig3_heterogeneity_plot.R`
- `figA1_placebo_event_study.R`

Exported outputs:

- `fig1_descriptive_trends.pdf`
- `fig2_event_study.pdf`
- `fig3_heterogeneity_plot.pdf`
- `figA1_placebo_event_study.pdf`

## What This Skill Should Not Default To

Do not default to:

- raw-data cleaning in `R`
- benchmark-style ML figures
- TensorBoard-like plots
- decorative infographics
- gratuitous 3D charts
- flashy styling inconsistent with journal norms
- unexplained smoothing or arbitrary transformations
- Nature styling as mere color mimicry without analytical clarity

## When To Recommend Appendix Placement

Prefer appendix placement when:

- the figure is mainly a robustness supplement
- the figure duplicates a table too closely
- the figure is informative but not central to identification or interpretation
- the figure is useful for transparency but not essential to the main narrative

## References to Load On Demand

Suggested supporting references for this skill may include:

- `references/stata-to-r-handoff.md`
- `references/figure-design-principles.md`
- `references/color-font-export-guide.md`
- `references/multi-panel-layout.md`
- `references/event-study-figure-guide.md`
- `references/coefficient-plot-guide.md`
- `references/map-visualization-guide.md`
- `references/figure-caption-guide.md`

## Working Rule

A successful paper figure should let a careful reader answer quickly:

1. what is being shown?
2. why is this figure here?
3. what part of the empirical argument does it support?
4. how should the pattern be interpreted?
5. is the visual claim appropriately narrower than or equal to the underlying design?

If the figure is beautiful but does not improve analytical clarity, it is not yet good enough.
