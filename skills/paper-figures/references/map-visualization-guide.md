# Map Visualization Guide for Empirical Economics and Agricultural Economics

Use this guide when producing **publication-ready map figures in `R`** from **Stata-processed `.dta` files**.

This guide is designed for a workflow in which:

- `Stata` handles data cleaning, sample construction, aggregation, variable generation, and exports a processed `.dta`
- `R` handles map production, spatial merging, styling, annotation, panel composition, and export

The goal is to make map figures:

- analytically useful
- visually disciplined
- reproducible
- consistent with **Nature / Nature-subjournal** figure expectations

A map should be used because geography matters for the argument, not because maps look attractive.

---

## 1. Core Principle

A good map figure should help the reader answer quickly:

1. what variable is being mapped?
2. at what geographic level?
3. for what sample or year?
4. where are values relatively high or low?
5. why is the geographic pattern relevant to the paper?

If the map does not improve the reader’s understanding of a meaningful spatial pattern, it probably does not belong in the paper.

---

## 2. When to Use a Map

Maps are most useful when the paper needs to show:

- regional distribution of an outcome or index
- spatial inequality or clustering
- province-level or county-level variation
- policy rollout or geographic coverage
- descriptive spatial patterns that motivate later heterogeneity or spatial analysis
- spatial context for the empirical setting

Maps are less useful when:

- geography is not central to interpretation
- the same point could be made more clearly with a dot plot or ranked bar plot
- the variable has weak spatial meaning
- the map is only decorative

Working rule:

Use a map when the **location of values** matters, not just their rank.

---

## 3. Default Workflow

```text
Prepare aggregated or processed data in Stata
    ->
Export plotting-ready `.dta`
    ->
Read shapefile in R
    ->
Import `.dta` in R
    ->
Merge shapefile and analytical data
    ->
Define scale and missing-value treatment
    ->
Plot the map
    ->
Add map annotations only if useful
    ->
Export publication-ready figure
```

Default rule:

- `Stata` handles the analytical data preparation
- `R` handles the spatial visualization

Do not do the main data cleaning in `R` unless the user explicitly asks for that.

---

## 4. Preferred Input Structure

The plotting-ready `.dta` should usually contain:

| variable | meaning |
|---|---|
| `geo_name` | geographic unit name used for merging |
| `geo_code` | optional geographic code |
| `value` | variable to be mapped |
| `year` | year if relevant |
| `group_label` | optional grouping label for faceted maps |

At minimum, the file should contain:

- one geographic merge key
- one mapped variable

Recommended rule:

- if the map is for one year, filter to that year in `Stata`
- if values are averages, rates, or shares, construct them in `Stata`
- keep the R-side merge simple and transparent

---

## 5. Geographic Merge Discipline

A map is only as reliable as the geographic merge.

Good practice:

- choose one stable merge key
- harmonize names or codes before plotting
- check unmatched areas explicitly
- define how missing values will appear on the map

Common merge choices:

- province name
- county code
- prefecture code
- standardized official geographic names

Avoid:

- merging on inconsistent name spellings
- silently dropping unmatched units
- assuming shapefile names and dataset names match automatically

Working rule:

If the merge is fragile, fix it upstream in `Stata` or in a clearly documented R merge-preparation step.

---

## 6. Choose the Right Map Type

### 6.1 Choropleth map

Best for:

- province-level or county-level averages
- rates, shares, or index values
- continuous regional variation

Most common and usually the right default.

### 6.2 Faceted choropleth maps

Best for:

- comparing several years
- comparing subgroups
- comparing several related variables

Use only when the panels remain readable.

### 6.3 Point or symbol maps

Best for:

- spatial locations of sampled units
- site-specific observations
- clustered intervention points

Use when polygon fill is not the right geometry.

### 6.4 Flow or link maps

Use only rarely.

Only use if movement or directional connection is central to the argument and can be shown clearly without clutter.

Working rule:

Default to the **simplest spatial geometry** that communicates the pattern well.

---

## 7. Variable Choice and Interpretation

A map variable should be:

- substantively meaningful
- interpretable at the mapped geography
- constructed consistently with the paper’s narrative

Examples:

- province-level average CHEI
- county-level agricultural carbon intensity
- prefecture-level adoption rate
- regional mean protein share
- village-level participation rate

Avoid mapping variables that are:

- poorly measured at the geography shown
- not interpretable spatially
- only weakly related to the paper’s argument
- likely to invite causal interpretation when only descriptive meaning is intended

If the map is descriptive, say so clearly in the caption and text.

---

## 8. Color Scale Discipline

Color choice is central in map design.

### 8.1 Continuous variables

For continuous variables, prefer a **sequential** or restrained **diverging** scale.

Use sequential scales when:

- the variable moves from lower to higher values
- no meaningful midpoint needs emphasis

Use diverging scales when:

- a meaningful midpoint exists
- positive and negative deviations are substantively important
- the variable is centered around a reference value

### 8.2 Missing values

Missing values should appear in a neutral color such as light grey.

The reader should be able to distinguish:

- low value
- high value
- missing value

without confusion.

### 8.3 Nature-style color logic

When a Nature-like style is requested, use:

- restrained gradients
- low-saturation palettes
- grayscale-safe logic
- no rainbow fill scales

Avoid:

- bright rainbow choropleths
- very saturated red-green contrasts
- arbitrary categorical colors for continuous variables

Working rule:

The map should remain interpretable if printed or viewed under poor color conditions.

---

## 9. Border and Layer Discipline

Map layering should support interpretation.

A common structure is:

1. filled polygons for the main variable
2. light boundary lines for readable separation
3. selected additional line layers if needed
4. subtle map furniture
5. no unnecessary decorative overlays

Preferred border logic:

- outer or administrative boundaries should be visible but not dominant
- internal borders should be light
- line widths should remain secondary to the fill layer

Avoid:

- thick black borders on every unit
- too many overlapping line layers
- decorative outlines that dominate the map

---

## 10. Annotation Discipline

Maps may include:

- title
- subtitle
- legend
- north arrow
- scale bar
- inset map
- region labels in limited cases

Use these only if they help interpretation.

### North arrow and scale bar

Useful when:

- the map is spatially central
- the audience benefits from orientation
- the figure is otherwise clean enough to absorb them

Not always necessary.

### Inset map

Useful when:

- a special region needs separate display
- offshore or remote territories would otherwise be hard to see
- the journal norm or national map convention expects it

### Text labels

Use sparingly.

Labels can help when:

- a few highlighted regions matter
- direct annotation improves interpretation
- the number of labels remains small

Avoid labeling every polygon unless absolutely necessary.

---

## 11. Nature-Style Map Defaults

When the user asks for a **Nature / Nature-subjournal** style map, default to:

- white or very clean background
- restrained boundary lines
- compact legend
- subtle map annotations
- careful use of whitespace
- muted but informative fill scales
- minimal visual clutter

This means:

- the data layer is primary
- cartographic furniture is secondary
- the legend is readable but compact
- the map looks refined rather than decorative

A Nature-style map should look polished because it is **analytically clear**, not because it is heavily stylized.

---

## 12. Title and Legend Discipline

A map title should be:

- short
- informative
- non-causal unless the map truly shows estimated effects

Good title patterns:

- `Provincial distribution of dietary quality, 2015`
- `County-level variation in agricultural carbon intensity`
- `Regional pattern of [variable], [year]`

Avoid titles such as:

- `Policy effect across China` when the map is only descriptive
- `Spatial mechanism of ...` when the map does not identify a mechanism

Legend rules:

- legend title should use reader-facing variable language
- legend scale should match the variable’s substantive meaning
- if values are indices, shares, or rates, make that clear
- legend should not dominate the figure

---

## 13. Multi-Panel Map Logic

Use multi-panel maps when comparing:

- different years
- different groups
- different variables with comparable meaning

A good faceted map design should:

- keep map extents identical across panels
- keep legend logic consistent
- keep panel ordering meaningful
- use shared or comparable scales when substantive comparison matters

Do not facet maps when:

- panels become too small to read
- each panel uses a different meaning or scale without clear justification
- one map alone would communicate the point more clearly

---

## 14. Caption Discipline

A good map caption should state:

- what variable is mapped
- at what geographic level
- for what year or sample
- whether values are averages, rates, totals, or index values
- how missing values are shown
- whether the figure is descriptive
- any relevant construction rule if not obvious

Example caption logic:

> **Figure X. Provincial distribution of dietary quality in rural China, 2015.**  
> The map reports province-level average CHEI scores constructed from the analytical dataset. Darker shades indicate higher dietary quality. Grey areas indicate missing values. The figure is descriptive.

If the map is regression-based, the caption should say so directly.  
Do not leave the evidence type ambiguous.

---

## 15. Main Text vs Appendix Use

### Main text

Prefer main-text placement when the map:

- shows a central descriptive fact
- motivates later spatial or regional analysis
- helps the reader understand the empirical setting
- conveys information more clearly than a table

### Appendix

Prefer appendix placement when the map:

- is supplementary
- provides an additional descriptive cut
- is useful for transparency but not central
- would otherwise distract from the main narrative

Not every spatial pattern needs a main-text map.

---

## 16. Common Mistakes

Avoid the following:

- mapping a variable with weak geographic meaning
- using highly saturated colors
- letting boundaries overpower the fill layer
- failing to document missing values
- merging shapefile and data with fragile keys
- leaving the legend title vague
- overloading the map with labels and annotations
- using a map where a ranked comparison plot would be clearer
- implying causal interpretation in the title or caption when the map is descriptive
- using multiple inconsistent map styles across the paper

---

## 17. Recommended R Logic

A clean map workflow in `R` usually includes:

1. load required packages
2. set fonts and shared theme logic
3. read shapefile
4. read Stata-processed `.dta`
5. merge spatial and analytical data
6. define color scale and missing-value treatment
7. plot the map
8. add only necessary annotations
9. export to a stable file name

Preferred packages may include:

- `sf`
- `haven`
- `dplyr`
- `ggplot2`
- `showtext`
- `ggspatial`
- `patchwork` if multi-panel composition is needed
- `RColorBrewer` or `viridisLite` if appropriate

Keep the plotting script lean and explicit.

---

## 18. Working Rule

A good map figure should let the reader answer quickly:

1. what variable is mapped?
2. where are values relatively high or low?
3. what geography and year are shown?
4. why is the spatial pattern relevant?
5. is the map descriptive or model-based?

If the map is visually attractive but does not improve the reader’s understanding of a meaningful spatial pattern, it probably should not be in the paper.
