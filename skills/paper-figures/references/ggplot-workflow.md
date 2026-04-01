# ggplot Workflow for Empirical Economics and Agricultural Economics Figures

Use this guide when producing publication-ready figures in `R` with `ggplot2` from **Stata-processed `.dta` files**.

This workflow is designed for a division of labor in which:

- `Stata` handles data cleaning, sample construction, aggregation, variable generation, and estimation
- `R` handles figure production, styling, panel composition, and export

The purpose of this guide is to make `ggplot2` use **systematic, reproducible, and journal-ready**, especially for empirical economics and agricultural economics papers targeting **Nature / Nature-subjournal**-style visual standards.

---

## 1. Core Principle

A good `ggplot2` workflow should make it easy to answer:

1. where the figure data came from
2. what each variable does in the plot
3. what the figure is supposed to show
4. how the styling is controlled
5. how the final output is exported reproducibly

The goal is not just to make a figure that looks good once.  
The goal is to make a figure that is:

- readable
- reproducible
- easy to revise
- easy to scale across multiple figures in one paper

---

## 2. Default Workflow

A clean `ggplot2` workflow should usually follow this sequence:

```text
Import processed `.dta`
    ->
Inspect variables and confirm plotting purpose
    ->
Light data preparation for plotting
    ->
Define labels, factor order, and grouping logic
    ->
Build the ggplot object
    ->
Apply shared theme and styling
    ->
Add panel layout if needed
    ->
Export with explicit dimensions and file name
```

The workflow should be **structured and modular**, not one long uncontrolled script.

---

## 3. Default Division of Labor

### Stata should usually handle

- raw-data cleaning
- merge / append / reshape for analysis
- sample construction
- variable generation
- descriptive aggregation
- regression estimation
- exporting figure-ready `.dta`

### R should usually handle

- importing the processed `.dta`
- light reshaping for plotting
- relabeling
- ordering
- grouping
- plotting
- styling
- faceting
- panel composition
- export

Do **not** silently reconstruct the full analytical sample in `R` unless the user explicitly asks for that.

---

## 4. Recommended Script Structure

A clean figure script should usually have the following sections:

### 0. Packages
Load only the packages actually needed.

### 1. Fonts and global settings
Set font system, theme objects, and shared options.

### 2. Data import
Read the processed `.dta` file.

### 3. Plot data preparation
Do only light plotting preparation such as:

- factor reordering
- label cleanup
- panel grouping
- date conversion for plotting
- plotting-specific reshaping

### 4. Plot construction
Build the `ggplot` object step by step.

### 5. Styling
Apply shared theme, labels, legend placement, scales, and panel logic.

### 6. Export
Export the figure with explicit filename, width, height, units, and format.

A good script should make each of these blocks visually distinct.

---

## 5. Minimal Example Script Skeleton

```r
# ==========================================
# Figure X: [short descriptive name]
# ==========================================

# -------------------------
# 0. Packages
# -------------------------
library(haven)
library(dplyr)
library(ggplot2)
library(forcats)
library(showtext)

# -------------------------
# 1. Fonts and settings
# -------------------------
font_add("Arial", "/System/Library/Fonts/Supplemental/Arial.ttf")
showtext_auto()

plot_font <- "Arial"

theme_paper <- function() {
  theme_minimal(base_family = plot_font, base_size = 11) +
    theme(
      panel.grid.minor = element_blank(),
      axis.text = element_text(colour = "black"),
      plot.title = element_text(face = "bold")
    )
}

# -------------------------
# 2. Data import
# -------------------------
df <- read_dta("data/figure_data/figX_input.dta")

# -------------------------
# 3. Plot data preparation
# -------------------------
df <- df %>%
  mutate(group = as.character(group))

# -------------------------
# 4. Plot construction
# -------------------------
p <- ggplot(df, aes(x = year, y = value, group = group)) +
  geom_line() +
  geom_point()

# -------------------------
# 5. Styling
# -------------------------
p <- p +
  labs(
    x = "Year",
    y = "Value",
    title = "Figure title"
  ) +
  theme_paper()

# -------------------------
# 6. Export
# -------------------------
ggsave(
  filename = "output/figures/figX_output.pdf",
  plot = p,
  width = 7.0,
  height = 4.8,
  units = "in"
)
```

This basic structure is preferred over ad hoc plotting code pasted into an interactive session.

---

## 6. Data Import Discipline

Because the default workflow assumes `Stata` exports processed `.dta` files, the recommended import method is:

```r
library(haven)
df <- read_dta("path/to/file.dta")
```

### Good practice

- import only the figure-ready `.dta`
- keep file paths explicit
- avoid relying on manually opened RStudio objects
- avoid reading from temporary local session states

### Avoid

- rebuilding the sample in `R`
- mixing multiple unsynchronized files without documentation
- importing `.csv` by default when the intended workflow is `.dta`

If multiple panels need separate `.dta` files, import them in separate blocks with clear names.

---

## 7. Plot Data Preparation Discipline

Plot preparation in `R` should be **light and transparent**.

Appropriate tasks include:

- converting labelled variables to readable character values
- reordering categories with `forcats`
- defining panel labels
- creating short readable labels
- converting dates or years into plotting-ready formats
- pivoting from wide to long when needed for plotting
- creating plotting-only helper variables

Avoid:

- major sample filtering not already documented in `Stata`
- hidden variable construction that changes substantive meaning
- silent exclusion of observations without explanation
- complicated data engineering inside the plotting script

Working rule:

If the plot would change substantively because of the `R` preparation step, that step probably belongs in `Stata` instead.

---

## 8. Building the Plot Step by Step

A good `ggplot2` workflow builds the figure in layers.

Typical sequence:

1. define `ggplot(...)`
2. add main geometry
3. add reference structures such as zero lines or smooth axis guides
4. add labels
5. add scales
6. add theme
7. add faceting if needed

Example:

```r
p <- ggplot(df, aes(x = year, y = value)) +
  geom_line() +
  geom_point() +
  labs(x = "Year", y = "Value") +
  theme_paper()
```

This is usually clearer than writing one very long block without structure.

---

## 9. Aesthetic Mapping Rules

Use aesthetic mappings only when they encode analytically meaningful differences.

Common mappings include:

- `x`
- `y`
- `group`
- `colour`
- `linetype`
- `shape`
- `fill`
- `facet`

### Good practice

- map only what matters
- keep mappings stable across related figures
- use labels with reader-facing language

### Avoid

- mapping too many variables at once
- using color where grouping is unnecessary
- letting default variable names appear in legends

Working rule:

If the figure needs a long legend to be readable, the mapping logic may be too complex.

---

## 10. Label and Factor Workflow

A strong `ggplot2` workflow usually includes explicit label preparation.

Useful tools include:

- `mutate()` for relabeling
- `forcats::fct_reorder()` for meaningful ordering
- `case_when()` for readable category names
- `stringr` for controlled text cleaning

Example:

```r
df <- df %>%
  mutate(
    region = case_when(
      region == "east"  ~ "Eastern region",
      region == "west"  ~ "Western region",
      region == "central" ~ "Central region",
      TRUE ~ region
    ),
    region = factor(region, levels = c("Eastern region", "Central region", "Western region"))
  )
```

Do not rely on software default ordering when order is substantively meaningful.

---

## 11. Theme Workflow

A paper workflow should usually define one reusable theme function.

Example logic:

```r
theme_paper <- function() {
  theme_minimal(base_family = plot_font, base_size = 11) +
    theme(
      panel.grid.minor = element_blank(),
      panel.grid.major = element_line(linewidth = 0.25, colour = "grey88"),
      axis.text = element_text(colour = "black"),
      legend.title = element_text(face = "bold"),
      plot.title = element_text(face = "bold", hjust = 0.5)
    )
}
```

This is better than manually rewriting theme settings for every figure.

A shared theme improves:

- consistency
- speed of revision
- paper-wide visual coherence

---

## 12. Nature-Style Default Workflow

When the target is **Nature / Nature-subjournal** style, the `ggplot2` workflow should default to:

- restrained and clean theme
- limited use of color
- readable grayscale performance
- moderate font size
- modest line widths
- balanced whitespace
- careful legend control
- minimal clutter

Working rule:

Nature-style in this workflow means **refined restraint**, not aggressive styling.

In practice, that usually implies:

- one shared theme
- one restrained palette logic
- one consistent font system
- no over-annotation
- one clear main visual message per figure

---

## 13. Common Figure Families and ggplot Logic

## 13.1 Trend plots

Typical `ggplot2` building blocks:

- `geom_line()`
- `geom_point()`
- `scale_x_continuous()`
- optional `facet_wrap()` for groups

## 13.2 Group comparisons

Typical building blocks:

- `geom_point()`
- `geom_line()`
- `geom_col()` only when bars are truly the best comparison device
- `position_dodge()` when needed, used sparingly

## 13.3 Composition figures

Typical building blocks:

- `geom_col()`
- reordered categories
- explicit share or unit labels

## 13.4 Maps

Typical building blocks:

- `sf`
- `geom_sf()`
- restrained fill scale
- annotation tools such as scale bar and north arrow only when needed

## 13.5 Multi-panel figures

Typical building blocks:

- `patchwork`
- `cowplot`
- shared theme objects
- aligned caption logic

Each figure family should use the simplest effective geometry.

---

## 14. Faceting Workflow

Use faceting only when it clarifies the comparison.

Good uses:

- region-specific panels
- subgroup panels
- panel families with the same variable logic
- multi-outcome comparisons that share scale or structure

Avoid faceting when:

- panels have no common logic
- the resulting figure becomes too small to read
- one panel is much more important than the others and gets visually buried

Common faceting tools:

- `facet_wrap()`
- `facet_grid()`

If faceting is used, panel order should be controlled explicitly.

---

## 15. Legend Workflow

A good `ggplot2` workflow treats legends as secondary.

Preferred logic:

- direct labeling when feasible
- concise legends
- consistent group naming across figures
- legend placement that does not dominate the panel

Typical tools:

- `guides()`
- `theme(legend.position = ...)`
- `scale_*_manual()`

Avoid:

- long unreadable legends
- legends that restate the axis title
- legend placement that compresses the data region unnecessarily

---

## 16. Scale Workflow

Scales are part of analytical design, not just formatting.

Typical tools include:

- `scale_x_continuous()`
- `scale_y_continuous()`
- `scale_fill_gradientn()`
- `scale_colour_manual()`
- `scale_y_continuous(labels = percent_format())`

Use scales to make:

- units explicit
- comparisons readable
- category ordering coherent
- gradients interpretable

Avoid:

- arbitrary truncation
- overcomplicated axis breaks
- misleading transformations without explanation

---

## 17. Export Workflow

Export should always be part of the script.

Typical export logic:

```r
ggsave(
  filename = "output/figures/fig1_trend_plot.pdf",
  plot = p,
  width = 7.2,
  height = 5.0,
  units = "in",
  dpi = 600
)
```

Good practice:

- use stable output filenames
- match manuscript figure numbering when possible
- use vector formats by default
- keep width and height explicit
- export directly from code, not manually from the plotting window

Preferred formats:

- `.pdf`
- `.svg`

Use raster output only when needed.

---

## 18. Paper-Wide Consistency Workflow

When a paper has multiple figures, the `ggplot2` workflow should aim for shared components:

- one font setup block
- one theme function
- one palette logic
- one file naming convention
- one caption discipline
- one export style

This makes the paper feel coherent and reduces revision time later.

---

## 19. Common Workflow Mistakes

Avoid the following:

- doing major data reconstruction in `R`
- writing one long plot script with no sections
- letting software defaults determine order and labels
- using raw variable names in legends or axes
- styling each figure from scratch with no shared theme
- exporting figures manually instead of through code
- overloading one figure with too many aesthetics
- mixing incompatible color or font logic across figures
- producing a figure that looks polished but is hard to revise

---

## 20. Recommended Package Set

A lean paper-figure workflow may include:

- `haven`
- `dplyr`
- `tidyr`
- `ggplot2`
- `forcats`
- `showtext`
- `patchwork`
- `cowplot`
- `scales`
- `stringr`
- `sf` for maps
- `ggspatial` for map annotation
- `ggrepel` only when necessary
- `ggtext` only when necessary

Do not load many packages without purpose.  
Prefer the smallest set that keeps the workflow clear.

---

## 21. Working Rule

A good `ggplot2` workflow should let a future reader, coauthor, or future you answer quickly:

1. what file was imported?
2. what transformations were done only for plotting?
3. how was the figure built?
4. what controls the style?
5. how was the final output exported?

If those five questions are hard to answer, the workflow is not yet clean enough.
