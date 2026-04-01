# Example: Multi-Panel Figure from Stata-Processed `.dta` Files

This example shows how to build a **publication-ready multi-panel figure in R** after `Stata` has already processed the data and exported plotting-ready `.dta` files.

This is one of the most useful figure types in empirical economics and agricultural economics papers because it allows the paper to present several related descriptive patterns in one coherent figure.

Typical use cases include combining:

- a national trend plot
- a group comparison plot
- a structural composition plot
- a map
- a distribution plot
- several related descriptive panels that support one main narrative

The workflow follows the repository default:

- `Stata` handles data cleaning, sample construction, aggregation, and exports processed `.dta` files
- `R` imports the `.dta` files, produces the individual panels, aligns them, and exports the final multi-panel figure

---

## Figure Purpose

A multi-panel figure should not be used just because several graphs exist.  
It should be used when several panels together answer **one larger descriptive question** more clearly than separate figures would.

Examples of good multi-panel logic:

- Panel (a): national time trend  
- Panel (b): regional comparison of the same trend  
- Panel (c): structural decomposition of the same outcome  

or

- Panel (a): spatial distribution  
- Panel (b): trend over time  
- Panel (c): subgroup comparison  

A strong multi-panel figure should feel like **one argument in visual form**, not a collage.

---

## Typical Use Case

Suppose a paper on rural dietary quality wants to show:

- how dietary quality evolved over time
- how the pattern differed across regions
- how the composition of key dietary components changed

A natural multi-panel figure could be:

- **Panel (a)**: national trend in average CHEI
- **Panel (b)**: trend in CHEI by region
- **Panel (c)**: composition of dietary components in the latest year

This kind of figure works well in the main text when the paper needs to establish descriptive context before moving to the econometric results.

---

## Expected Input Data

The recommended workflow is that `Stata` exports one processed `.dta` file per panel, or one harmonized `.dta` file that can generate several panels.

Typical panel-specific `.dta` files may include:

### `fig_panel_a_trend.dta`

| variable | meaning |
|---|---|
| `year` | time variable |
| `chei_mean` | national mean outcome |

### `fig_panel_b_region_trend.dta`

| variable | meaning |
|---|---|
| `year` | time variable |
| `region` | region label |
| `chei_mean` | regional mean outcome |

### `fig_panel_c_structure.dta`

| variable | meaning |
|---|---|
| `component` | dietary component label |
| `share` | share or mean level |
| `year` | year if relevant |

The preferred rule is:

- `Stata` should already have constructed the aggregation and filtering logic
- `R` should only need light reshaping for plotting

---

## Recommended Stata Output Logic

A stylized Stata workflow might look like:

```stata
* ------------------------------------------
* Panel (a): national trend
* ------------------------------------------
use "analysis_data/main_panel.dta", clear
collapse (mean) chei_mean = chei_score, by(year)
save "data/figure_data/fig_panel_a_trend.dta", replace

* ------------------------------------------
* Panel (b): regional trend
* ------------------------------------------
use "analysis_data/main_panel.dta", clear
collapse (mean) chei_mean = chei_score, by(year region)
save "data/figure_data/fig_panel_b_region_trend.dta", replace

* ------------------------------------------
* Panel (c): composition in latest year
* ------------------------------------------
use "analysis_data/main_panel.dta", clear
keep if year == 2015
collapse (mean) cereals vegetables fruits meat dairy, by(year)

reshape long cereals vegetables fruits meat dairy, i(year) j(component) string
rename _j component
rename _value share

save "data/figure_data/fig_panel_c_structure.dta", replace
```

In a real project, variable names and aggregation rules should be adapted to the actual paper.

---

## Complete R Example

```r
# ==========================================================
# Example: Multi-panel figure from Stata-processed .dta files
# ==========================================================

# -------------------------
# 0. Packages
# -------------------------
library(haven)
library(dplyr)
library(tidyr)
library(ggplot2)
library(forcats)
library(patchwork)
library(showtext)
library(scales)

# -------------------------
# 1. Fonts
# -------------------------
# Adjust these paths for your own machine if needed
font_add("Songti", "/System/Library/Fonts/Supplemental/Songti.ttc")
font_add("Roman", "/System/Library/Fonts/Supplemental/Times New Roman.ttf")
font_add("Arial", "/System/Library/Fonts/Supplemental/Arial.ttf")
showtext_auto()

plot_font <- "Arial"

# -------------------------
# 2. Import Stata .dta files
# -------------------------
df_a <- read_dta("data/figure_data/fig_panel_a_trend.dta")
df_b <- read_dta("data/figure_data/fig_panel_b_region_trend.dta")
df_c <- read_dta("data/figure_data/fig_panel_c_structure.dta")

# -------------------------
# 3. Basic data preparation
# -------------------------
df_a <- df_a %>%
  mutate(year = as.numeric(year))

df_b <- df_b %>%
  mutate(
    year = as.numeric(year),
    region = as.character(region)
  )

df_c <- df_c %>%
  mutate(
    component = as.character(component),
    component = fct_reorder(component, share)
  )

# -------------------------
# 4. Shared Nature-style theme
# -------------------------
theme_paper <- function() {
  theme_minimal(base_family = plot_font, base_size = 11) +
    theme(
      panel.grid.minor = element_blank(),
      panel.grid.major = element_line(linewidth = 0.25, colour = "grey88"),
      axis.title = element_text(size = 11),
      axis.text = element_text(size = 10, colour = "black"),
      legend.title = element_text(size = 10, face = "bold"),
      legend.text = element_text(size = 9, colour = "black"),
      strip.text = element_text(size = 11, face = "bold"),
      plot.title = element_text(size = 12, face = "bold"),
      plot.subtitle = element_text(size = 10),
      plot.caption = element_text(size = 8.5, hjust = 0),
      plot.tag = element_text(size = 13, face = "bold"),
      plot.tag.position = c(0.01, 0.99)
    )
}

# -------------------------
# 5. Panel (a): national trend
# -------------------------
p_a <- ggplot(df_a, aes(x = year, y = chei_mean)) +
  geom_line(linewidth = 0.7, colour = "black") +
  geom_point(size = 2.0, colour = "black") +
  scale_x_continuous(breaks = pretty_breaks()) +
  labs(
    x = "Year",
    y = "CHEI score",
    title = "National trend",
    tag = "a"
  ) +
  theme_paper() +
  theme(
    legend.position = "none"
  )

# -------------------------
# 6. Panel (b): regional trend
# -------------------------
p_b <- ggplot(df_b, aes(x = year, y = chei_mean, group = region, linetype = region)) +
  geom_line(linewidth = 0.65, colour = "black") +
  geom_point(size = 1.6, colour = "black") +
  scale_x_continuous(breaks = pretty_breaks()) +
  labs(
    x = "Year",
    y = "CHEI score",
    title = "Regional comparison",
    linetype = "Region",
    tag = "b"
  ) +
  theme_paper() +
  theme(
    legend.position = "bottom",
    legend.box = "horizontal"
  )

# -------------------------
# 7. Panel (c): composition
# -------------------------
p_c <- ggplot(df_c, aes(x = share, y = component)) +
  geom_col(width = 0.65, fill = "grey45") +
  scale_x_continuous(labels = percent_format(accuracy = 1)) +
  labs(
    x = "Share",
    y = NULL,
    title = "Diet structure in 2015",
    tag = "c"
  ) +
  theme_paper() +
  theme(
    legend.position = "none",
    panel.grid.major.y = element_blank()
  )

# -------------------------
# 8. Combine panels
# -------------------------
p_multi <- (p_a | p_b) / p_c +
  plot_annotation(
    title = "Descriptive patterns of dietary quality and composition",
    caption = "Notes: Panel (a) shows the national mean CHEI over time. Panel (b) shows mean CHEI by region. Panel (c) reports the composition shares in 2015. All panels are constructed from Stata-processed `.dta` files."
  )

# -------------------------
# 9. Export
# -------------------------
ggsave(
  filename = "output/figures/fig1_multi_panel_descriptive.pdf",
  plot = p_multi,
  width = 9.2,
  height = 7.0,
  units = "in",
  dpi = 600
)
```

---

## Why This Example Works

This example follows the preferred workflow of the repository.

### 1. `Stata` remains the analytical backend
The aggregation logic is handled in `Stata`, not improvised in `R`.

### 2. `R` focuses on figure production
`R` handles:

- importing `.dta`
- panel-level plotting
- visual consistency
- multi-panel composition
- export

### 3. The panels form one coherent descriptive argument
The three panels are not arbitrary. Together they answer one broader question:

- how the national pattern evolved
- how it differs across regions
- how the structure looks in the most recent year

### 4. The style is restrained and publication-ready
The figure avoids:

- unnecessary colors
- overloaded annotation
- inconsistent panel sizing
- decorative clutter

---

## Nature-Style Design Choices in This Example

This example adopts a restrained style consistent with Nature-like figure expectations:

- consistent typography across all panels
- minimal but readable grids
- black-and-grey primary design for print safety
- compact legend treatment
- balanced whitespace across the multi-panel layout
- panel tags integrated into the layout rather than manually placed outside the plot system

This is preferable to:

- different color systems in each panel
- mismatched fonts
- large legends occupying too much space
- inconsistent line thickness across panels
- panel titles with very different visual weight

---

## Suggested Caption

A manuscript-ready caption could be written as:

> **Figure X. Descriptive patterns of dietary quality and composition.**  
> Panel (a) shows the national average China Healthy Eating Index (CHEI) over time. Panel (b) reports the same measure by region. Panel (c) reports the composition shares of key dietary components in 2015. All panels are descriptive and are constructed from Stata-processed datasets used for figure production in R.

If the figure supports a different topic, revise accordingly:

> **Figure X. Multi-panel descriptive evidence on [topic].**  
> Panel (a) ..., Panel (b) ..., and Panel (c) .... The figure is descriptive and is intended to summarize the main empirical context before the regression analysis.

---

## Suggested Manuscript Language

Useful prose around the figure could be:

- `Figure X summarizes three related descriptive patterns.`
- `Panel (a) shows a gradual increase in ... over time.`
- `Panel (b) indicates that this trend was not uniform across regions.`
- `Panel (c) further shows that the composition of ... in the latest year remained heavily concentrated in ...`
- `Taken together, the panels provide descriptive context for the regression results reported later in Table X.`

If caution is needed:

- `The figure is descriptive and should not be interpreted as causal evidence.`
- `These panels help motivate the subsequent empirical analysis, but they do not identify the source of the observed differences by themselves.`

---

## Common Mistakes to Avoid

Do not:

- combine panels that answer unrelated questions
- use completely different visual styles across panels
- overload the figure with too many groups, panels, or legends
- let one panel dominate visually unless that is analytically intended
- mix descriptive and regression-based panels without making the distinction clear
- use inconsistent axes where cross-panel comparison is intended
- write a caption that fails to decode the role of each panel

---

## When This Figure Belongs in the Main Text

Prefer main-text placement when the multi-panel figure:

- provides a compact descriptive overview
- supports the paper’s central narrative efficiently
- saves space relative to several separate figures
- helps the reader understand the empirical setting before the main results

---

## When This Figure Belongs in the Appendix

Prefer appendix placement when the figure:

- mainly combines supplementary panels
- is useful but not central to the narrative
- repeats information that can already be read easily from tables
- contains robustness or secondary descriptive cuts rather than core context

---

## Working Rule

A good multi-panel figure should let the reader answer quickly:

1. what is the common question linking the panels?
2. what does each panel contribute?
3. why are these panels shown together?
4. does the visual structure improve the narrative relative to separate figures?
5. is the figure analytically coherent rather than just visually compact?

If the panels do not belong to one larger descriptive argument, they probably should not be combined.
