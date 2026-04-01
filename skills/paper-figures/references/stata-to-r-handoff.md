# Stata-to-R Handoff Guide for Empirical Economics and Agricultural Economics Figures

Use this guide when preparing a figure workflow in which:

- `Stata` handles data cleaning, sample construction, aggregation, variable generation, and estimation
- `R` imports the processed `.dta` file and handles figure production, styling, panel composition, and export

This guide is built for empirical economics and agricultural economics papers where the user’s default workflow is:

> **Stata for data work, R for figures**

The goal is to make the handoff from `Stata` to `R`:

- clean
- reproducible
- low-friction
- easy to audit
- easy to revise later

A good handoff means `R` can focus on plotting, not on rebuilding the dataset logic.

---

## 1. Core Principle

The handoff from `Stata` to `R` should preserve a simple division of labor:

### `Stata` should answer

- what is the sample?
- how are variables constructed?
- how are observations aggregated?
- what year, region, group, or category is included?
- what dataset should be plotted?

### `R` should answer

- how should this dataset be visualized?
- how should groups, labels, and panels be arranged?
- how should the figure look?
- how should the figure be exported?

Working rule:

If the figure would change substantively because of a hidden `R` data step, the handoff is not yet clean enough.

---

## 2. Default Workflow

A clean handoff usually follows this order:

```text
Raw data and analytical dataset in Stata
    ->
Sample restriction and variable construction in Stata
    ->
Aggregation / collapse / reshape in Stata
    ->
Save plotting-ready `.dta`
    ->
Read `.dta` in R
    ->
Do only light plotting preparation in R
    ->
Build and export figure
```

The default expectation is:

- `Stata` creates the **figure-ready data**
- `R` creates the **figure-ready graphic**

---

## 3. What Should Be Done in Stata

`Stata` should usually handle all steps that affect the substantive content of the figure.

These include:

- raw-data cleaning
- merge / append / reshape for analysis
- sample selection
- variable generation
- missing-value handling
- winsorization or trimming when relevant
- collapsing or aggregation
- region, year, or subgroup filtering
- constructing plot-ready statistics
- preparing one dataset per figure or per figure family

Examples of tasks that usually belong in `Stata`:

- computing province-level mean CHEI by year
- constructing dietary composition shares
- collapsing household data to region-year averages
- filtering to one survey year for a choropleth map
- constructing grouped summary series for trend figures
- exporting event-study coefficients if needed

Working rule:

If the step affects **who is in the figure** or **what the values mean**, it usually belongs in `Stata`.

---

## 4. What Should Be Done in R

`R` should usually handle only **plotting-oriented** tasks.

These include:

- importing the processed `.dta`
- converting labels to readable character values
- factor ordering for plotting
- light reshaping from wide to long when needed for plotting layout
- defining panel labels
- setting color, font, and theme logic
- building the figure
- arranging multi-panel layout
- exporting the final file

Examples of tasks that usually belong in `R`:

- reordering regions in a dot plot
- turning a grouping variable into a factor with panel order
- defining line type or fill mapping
- setting a clean legend title
- combining three finished panels into one multi-panel figure

Working rule:

If the step changes the analytical meaning of the values, it probably belongs in `Stata`, not `R`.

---

## 5. The Handoff Dataset Should Be Figure-Ready

A good handoff dataset should already be ready to plot.

That means it should already contain:

- the right sample
- the right time window
- the right level of aggregation
- the final variable(s) to plot
- the geographic, temporal, or subgroup identifier needed for the figure

`R` should not need to guess:

- which year to keep
- which regions to drop
- which sample restriction to use
- whether values are raw, weighted, averaged, or normalized

That logic should already be settled in `Stata`.

---

## 6. Recommended `.dta` Design

A plotting-ready `.dta` should be as simple as possible.

### Good characteristics

- one row equals one plotted unit or one plotted summary observation
- variable names are interpretable
- identifiers are preserved clearly
- unnecessary analytical variables are removed
- the file is small enough to inspect quickly

### Example structures

#### Trend plot

| year | value |
|---|---|
| 2003 | 48.2 |
| 2004 | 48.9 |
| 2005 | 49.6 |

#### Grouped trend plot

| year | region | value |
|---|---|---|
| 2003 | East | 50.1 |
| 2003 | Central | 47.8 |
| 2003 | West | 45.9 |

#### Structure/composition plot

| component | share |
|---|---|
| Cereals | 0.34 |
| Vegetables | 0.19 |
| Meat | 0.16 |

#### Map plot

| province_name | value |
|---|---|
| 北京市 | 33.0 |
| 天津市 | 33.1 |
| 河北省 | 31.2 |

Good plotting data are small, explicit, and easy to inspect.

---

## 7. Naming Rules for Handoff Files

The handoff file name should make clear:

- which figure it belongs to
- what level of aggregation it uses
- whether it is main text or appendix
- what substantive content it contains

Preferred examples:

- `fig1_national_trend.dta`
- `fig2_region_trend.dta`
- `fig3_diet_structure_2015.dta`
- `fig4_provincial_map_chei.dta`
- `figA1_distribution_check.dta`

Avoid vague names such as:

- `temp1.dta`
- `plotdata.dta`
- `new_final_use.dta`
- `figure_data_latest2.dta`

A good file name reduces later confusion.

---

## 8. Variable Naming Rules

Handoff variables should be named for interpretability, not only for internal convenience.

Prefer names such as:

- `year`
- `region`
- `province_name`
- `chei_mean`
- `protein_share`
- `component`
- `value`
- `group_label`

Avoid handoff names such as:

- `x1`
- `v2`
- `temp_mean`
- `group_new`
- `ratio_a`

If internal variable names are messy in the analytical dataset, rename them before exporting the plotting `.dta`.

Working rule:

The R plotting script should not need a paragraph of comments just to explain what each variable means.

---

## 9. Label Preparation in Stata vs R

A useful division is:

### In Stata, prepare

- the core variable meanings
- stable group identifiers
- merge keys
- sample-defining categories

### In R, prepare

- display labels
- panel labels
- factor order
- shortened reader-facing labels for plotting

For example:

- `Stata`: keep `region = 1/2/3`
- `R`: map it to `"Eastern region"`, `"Central region"`, `"Western region"`

or

- `Stata`: keep province names standardized
- `R`: use them directly for plotting

Working rule:

Substantive classification belongs in `Stata`; presentational relabeling can happen in `R`.

---

## 10. Aggregation Rules Should Be Explicit

A handoff file should not leave aggregation ambiguous.

For example, the file should make it possible to know whether `value` is:

- a raw mean
- a weighted mean
- a total
- a share
- a per-capita value
- a province-level average of household values
- a year-specific cross-sectional average

This can be conveyed by:

- file naming
- variable naming
- comments in the Stata export script
- comments in the R import block
- caption language later on

Do not force the reader or future self to infer aggregation rules from memory.

---

## 11. Sample Rules Should Be Frozen Before Export

The handoff file should reflect a **finalized plotting sample**.

Before export in `Stata`, decide:

- which years are included
- which observations are excluded
- which subgroup definitions are used
- whether missing observations are dropped or retained
- whether the figure is national, regional, or subgroup-specific

Avoid pushing those decisions into `R` unless the figure is exploratory rather than paper-ready.

Working rule:

Paper figures should not depend on undocumented ad hoc filtering in the R script.

---

## 12. One Figure Family, One Data Logic

Try to keep each figure or tightly related figure family tied to one clear data logic.

Examples:

- all national trend figures come from one consistent region-year or year-level aggregation logic
- all province maps come from one province-level cross-section logic
- all diet composition figures come from one component-share logic

This makes the paper easier to audit and the code easier to maintain.

---

## 13. Export Discipline in Stata

A clean Stata handoff block should usually do the following:

1. start from the analysis dataset
2. apply figure-specific restriction
3. collapse or reshape if needed
4. keep only plotting-relevant variables
5. save the `.dta` with a stable name

A stylized example:

```stata
use "analysis_data/main_panel.dta", clear

keep if year >= 2003 & year <= 2015
collapse (mean) chei_mean = chei_score, by(year region)

keep year region chei_mean
save "data/figure_data/fig2_region_trend.dta", replace
```

This is cleaner than exporting a very large file and asking `R` to discover what matters.

---

## 14. Import Discipline in R

A clean R import block should be simple and explicit.

Example:

```r
library(haven)
library(dplyr)

df <- read_dta("data/figure_data/fig2_region_trend.dta") %>%
  mutate(
    region = factor(region, levels = c("East", "Central", "West"))
  )
```

The import block should make it easy to see:

- which file is being used
- what minimal plotting preparation is being done
- whether factor ordering or relabeling is applied

Avoid import blocks that immediately contain complicated filtering, merging, or analytical reconstruction.

---

## 15. Handoff Notes for Different Figure Types

## 15.1 Trend figures

Stata should export:

- time variable
- value
- optional group variable

R should handle:

- ordering
- line styling
- legend
- export

---

## 15.2 Group comparison figures

Stata should export:

- group variable
- compared value
- optional year or subgroup

R should handle:

- factor order
- geometry choice
- label refinement

---

## 15.3 Composition figures

Stata should export:

- component label
- share or level
- optional year or subgroup

R should handle:

- plotting order
- bars/dots/stack design
- color logic

---

## 15.4 Maps

Stata should export:

- geographic merge key
- mapped value
- optional year or subgroup

R should handle:

- shapefile import
- spatial merge
- map styling
- legend
- annotations

---

## 15.5 Multi-panel figures

Stata should export either:

- one `.dta` per panel
- or one harmonized `.dta` with clear panel logic

R should handle:

- panel-specific plotting
- shared style
- layout composition
- export

---

## 16. Common Handoff Mistakes

Avoid the following:

- exporting a file that is still analytically unfinished
- making R decide the sample silently
- using vague file names
- using raw internal variable names
- exporting too many unnecessary variables
- failing to standardize merge keys for maps
- relying on memory for what `value` means
- changing aggregation logic figure by figure without documentation
- mixing descriptive and regression-ready values in one unlabeled plotting file

---

## 17. Reproducibility Rule

A future reader, coauthor, or future you should be able to answer quickly:

1. which Stata script created the plotting `.dta`?
2. what sample does the `.dta` represent?
3. what does each variable mean?
4. which R script reads it?
5. which figure does it produce?

If those questions are hard to answer, the handoff is not yet reproducible enough.

---

## 18. Minimal Handoff Checklist

Before sending a `.dta` from `Stata` to `R`, check:

- [ ] the sample is final for this figure
- [ ] aggregation is complete
- [ ] only plotting-relevant variables remain
- [ ] merge keys are standardized if a map is involved
- [ ] variable names are interpretable
- [ ] the file name matches the figure purpose
- [ ] the R script will not need substantive data reconstruction
- [ ] the handoff can be explained in one sentence

---

## 19. Working Rule

A good Stata-to-R handoff should let `R` focus on **how to show the pattern**, not on **what the pattern should be**.

If the R script has to reconstruct the sample, redefine the variable, or guess the aggregation logic, the handoff is not yet clean enough.
