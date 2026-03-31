---
name: paper-figures
description: Use when the user wants to turn Stata-processed empirical economics or agricultural economics data into publication-ready descriptive figures using R. Default workflow assumes Stata handles data cleaning, sample construction, and variable generation, then exports `.dta` files; R imports the processed `.dta` files and focuses on figure production, multi-panel layout, styling, and export. Handles Chinese prompts such as "画图", "描述性图片", "发展趋势图", "拼图", "结构变化图", "空间分布图", and "Nature 风格图片".
version: 0.2.0
---

# Paper Figures for Empirical Economics and Agricultural Economics

Use this skill when the user wants to produce **journal-ready descriptive figures** from empirical economics or agricultural economics data using `R`.

Default workflow:

- `Stata` handles raw-data cleaning, merging, sample construction, variable generation, and exports processed `.dta` files
- `R` imports the processed `.dta` files and handles figure construction, panel composition, styling, annotation, and export

This skill is for **paper figures**, especially **descriptive and trend-oriented figures**, not for general-purpose R programming, dashboard building, or ML experiment visualization.

It also does **not** default to regression-result visualization.  
If the user explicitly wants coefficient plots or event-study figures, that can still be done, but it is not the primary default of this skill.

---

## Core Principle

Figures should serve one or more of the following functions:

1. show descriptive patterns clearly
2. present development trends over time
3. compare groups, regions, or categories
4. reveal structural shifts in outcomes, composition, or distributions
5. summarize sample patterns that support the paper’s empirical narrative
6. provide publication-ready visual evidence that complements, but does not replace, regression tables

A figure should make the empirical narrative **clearer than text or a raw table alone could**, not merely more decorative.

---

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
- captions and notes that make the figure interpretable without exaggeration

---

## Default Workflow

```text
Clarify figure purpose
    ->
Import processed `.dta` from Stata
    ->
Audit figure-ready variables and labels
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

---

## What This Skill Should Produce

Typical outputs include:

- complete runnable `R` code for the figure
- `figure-plan.md`
- `figure-spec-sheet.md`
- `figure-caption-sheet.md`
- publication-ready outputs such as `.pdf`, `.svg`, or high-resolution `.png` when requested

Generate only what is needed for the user’s task.  
If the user asks only for plotting code, prioritize a **complete runnable R script**.

---

## Default Inputs

This skill expects inputs such as:

- processed `.dta` files exported from `Stata`
- descriptive summary tables
- grouped or collapsed data already prepared in `Stata`
- region-year, household-year, county-year, or other analysis-ready descriptive datasets
- figure sketches or screenshots from the user
- journal target or style preference if available

Preferred input style:

- `Stata` prepares the processed data
- `R` imports the `.dta` file and focuses on plotting

Do **not** assume that `R` will do the main cleaning.  
If the input dataset is still not plotting-ready, the default recommendation is:

- finalize the dataset structure in `Stata`
- then use `R` for figure production

---

## Default Figure Families

Prioritize these figure families for empirical economics and agricultural economics papers.

### 1. Development trend plots

Use when the paper needs to show:

- trends over time
- pre/post evolution of descriptive outcomes
- long-run development trajectories
- group-based temporal comparisons

Typical requirements:

- year or period on the x-axis
- clear units on the y-axis
- readable group differentiation
- no misleading smoothing
- trend lines or point-line combinations chosen for clarity

---

### 2. Group comparison plots

Use when comparing:

- regions
- treatment vs control descriptive means
- rural vs urban groups
- income groups
- household types
- sectoral or category differences

Typical requirements:

- labels with economic meaning
- comparable scales
- clear legend or direct labeling
- avoid overloaded grouped bars when line or dot plots would be clearer

---

### 3. Composition or structure plots

Use when the paper needs to show:

- expenditure or intake structure
- composition shares
- category contribution
- structural change over time
- source breakdowns

Typical requirements:

- categories ordered meaningfully
- shares or levels clearly labeled
- color used sparingly and consistently
- stacked figures used only when the comparison remains readable

---

### 4. Distribution and density figures

Use when showing:

- sample distributions
- support
- skewness
- cross-group distribution differences
- trimmed or restricted descriptive patterns

Typical requirements:

- axis scales that remain interpretable
- no visually misleading bandwidth choices
- subgroup definitions stated clearly
- distribution plots used only when they help answer a descriptive question

---

### 5. Maps and spatial descriptive figures

Use when spatial allocation, regional disparity, clustering, or geographic patterns matter.

Typical requirements:

- clean projection and region boundaries
- readable labels
- restrained color use
- region names or codes consistent with the manuscript
- avoid decorative mapping without analytical purpose

---

### 6. Multi-panel composite figures

Use when several related descriptive figures belong together.

Typical requirements:

- consistent theme across panels
- aligned axes when comparison matters
- panel labels such as `(a)`, `(b)`, `(c)`
- balanced spacing
- one coherent caption structure

---

### 7. Sample flow or descriptive pipeline figures

Use when the paper benefits from showing:

- sample reductions
- subgroup construction
- analytic sample derivation
- data coverage by stage

Typical requirements:

- simple and readable structure
- one-direction visual logic
- counts clearly stated
- no unnecessary decoration

---

## Stata-to-R Division of Labor

Default rule:

- `Stata` should produce the **processed `.dta` file**
- `R` should produce the **publication-ready graphic**

### Stata should usually handle

- raw-data cleaning
- merge / append / reshape for analysis
- sample selection
- variable construction
- aggregation or collapsing when needed
- label preparation when useful
- exporting the processed `.dta`

### R should usually handle

- importing `.dta`
- light reshaping for plotting
- ordering factors and labels
- plotting
- styling
- faceting and multi-panel composition
- legend handling
- export

Do not silently rebuild the analytical sample in `R` unless the user explicitly wants that.

---

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
- descriptive categories should use consistent color logic across related figures

### Lines and points

- line widths should be readable but not heavy
- point sizes should be visible but not bulky
- emphasis should come from structure, not visual noise
- reference lines should be subtle but visible

### Axes and scales

- axis titles must include units where relevant
- tick marks should be readable and not too dense
- avoid truncated axes unless clearly justified
- avoid hidden scale choices that exaggerate or mute economically important variation

### Legends and labels

- direct labeling is preferred when it improves readability
- legends should be concise and harmonized with text terminology
- group names should match the manuscript exactly

### Export

Preferred formats by default:

- vector output: `.pdf` or `.svg`
- high-resolution raster only when required
- stable figure dimensions for one-column or two-column layouts
- reproducible export code in the R script

---

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
- whether the figure is purely descriptive or supports a broader empirical narrative

A figure is not ready to code until its descriptive and narrative purpose is clear.

---

## Caption and Note Discipline

A good figure caption or note should state, as relevant:

- what is plotted
- sample
- unit of observation
- construction or aggregation rule
- subgroup or panel meanings
- time window if relevant
- whether the figure is descriptive
- any transformation or normalization if used

Do not let captions overclaim causal interpretation for descriptive figures.

---

## Writing Discipline for Figures

Figures should be described in manuscript prose using disciplined language.

Preferred patterns include:

- `Figure X shows the evolution of ... over time.`
- `Figure X compares ... across regions / groups / categories.`
- `The figure reveals a clear upward / downward / diverging pattern in ...`
- `The descriptive pattern is consistent with the broader empirical discussion in Section X.`
- `These descriptive differences should be interpreted as contextual rather than causal evidence.`

Avoid:

- benchmark language
- decorative interpretation
- stronger causal claims in the figure caption than in the text
- treating a descriptive figure as if it identified an effect by itself

---

## Common Figure Risks

Watch for the following:

- overloading a figure with too many groups
- incomparable axis scales across supposedly comparable panels
- overloaded legends
- colors that fail in grayscale
- stacked figures that obscure meaningful comparison
- map figures with weak analytical purpose
- multi-panel figures with inconsistent themes
- captions too vague to decode the figure
- figure titles that overstate interpretation
- `R` code that silently changes the sample or variable definitions relative to `Stata`

---

## Recommended R Ecosystem

Default packages may include, as needed:

- `ggplot2`
- `dplyr`
- `tidyr`
- `haven`
- `patchwork`
- `cowplot`
- `sf`
- `showtext`
- `scales`
- `grid`
- `forcats`
- `stringr`
- `ggrepel`
- `ggtext`
- `viridisLite`
- `RColorBrewer`
- `magick` for panel composition when needed

Do not load many packages without purpose.  
Prefer a lean, transparent figure script.

---

## Default Output Discipline

When generating R scripts or figure plans, default to:

- one script per major figure, or one script per tightly related figure family
- stable file names that match manuscript figure numbering when possible
- explicit import path for the `.dta` file
- explicit export path
- clearly separated:
  - setup
  - data import
  - label preparation
  - plotting
  - export

---

## Example Output Naming

Preferred examples:

- `fig1_trend_plot.R`
- `fig2_group_comparison.R`
- `fig3_structure_change.R`
- `fig4_spatial_map.R`
- `figA1_sample_distribution.R`

Exported outputs:

- `fig1_trend_plot.pdf`
- `fig2_group_comparison.pdf`
- `fig3_structure_change.pdf`
- `fig4_spatial_map.pdf`
- `figA1_sample_distribution.pdf`

---

## What This Skill Should Not Default To

Do not default to:

- raw-data cleaning in `R`
- regression-result visualization
- coefficient plotting as the main use case
- benchmark-style ML figures
- TensorBoard-like plots
- decorative infographics
- gratuitous 3D charts
- flashy styling inconsistent with journal norms
- unexplained smoothing or arbitrary transformations
- Nature styling as mere color mimicry without analytical clarity

---

## When To Recommend Appendix Placement

Prefer appendix placement when:

- the figure is a supplementary descriptive check
- the figure duplicates a table too closely
- the figure is informative but not central to the main narrative
- the figure is useful for transparency but not essential to the paper’s core descriptive or empirical story

---

## References to Load On Demand

Suggested supporting references for this skill may include:

- `references/stata-to-r-handoff.md`
- `references/figure-design-principles.md`
- `references/color-font-export-guide.md`
- `references/multi-panel-layout.md`
- `references/descriptive-trend-figure-guide.md`
- `references/group-comparison-figure-guide.md`
- `references/map-visualization-guide.md`
- `references/figure-caption-guide.md`

---

## Working Rule

A successful paper figure should let a careful reader answer quickly:

1. what is being shown?
2. why is this figure here?
3. what part of the empirical narrative does it support?
4. how should the pattern be interpreted?
5. is the visual interpretation appropriately narrower than or equal to the underlying evidence?

If the figure is beautiful but does not improve analytical clarity, it is not yet good enough.
