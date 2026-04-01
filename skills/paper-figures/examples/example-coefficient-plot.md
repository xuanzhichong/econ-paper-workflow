# Example: Coefficient Plot from a Stata-Exported `.dta` File

This example shows how to build a **publication-ready coefficient plot in R** after `Stata` has already produced a plotting dataset in `.dta` format.

This is a **supported but non-default** use of `paper-figures`.  
The default workflow of this skill is still descriptive figures and trend figures.  
However, coefficient plots remain very useful when the paper needs to present:

- baseline vs robustness estimates
- subgroup heterogeneity estimates
- mechanism estimates
- multiple outcomes with a common treatment

The example below follows the default workflow:

- `Stata` prepares the coefficient dataset
- `R` imports the `.dta` and produces the final figure

---

## Figure Purpose

This figure is designed to help the reader compare estimated treatment effects across:

- outcomes
- subgroups
- specification families

The plot emphasizes:

- point estimates
- confidence intervals
- easy comparison across rows
- clean layout suitable for economics and agricultural economics papers
- a restrained style consistent with **Nature / Nature-subjournal** expectations

---

## Typical Use Case

Suppose the paper estimates the effect of a policy on several outcomes and wants to show the main coefficient for each outcome in a single figure.

Examples:

- impact on different dietary outcomes
- impact on different sustainability indicators
- heterogeneity by region
- mechanism estimates using several mediating outcomes

---

## Expected Input Data

The recommended approach is that `Stata` exports a `.dta` file with one row per plotted coefficient.

A typical plotting dataset may contain:

| variable | meaning |
|---|---|
| `term` | regression term name |
| `estimate` | coefficient estimate |
| `se` | standard error |
| `ci_low` | lower bound of confidence interval |
| `ci_high` | upper bound of confidence interval |
| `outcome_label` | readable label for the row |
| `panel_label` | optional panel grouping |
| `plot_order` | numeric order for plotting |
| `sample_label` | optional subgroup or sample tag |

At minimum, the plotting file should contain:

- `estimate`
- `ci_low`
- `ci_high`
- one readable label column
- one order column if row order matters

---

## Recommended Stata Output Logic

The preferred workflow is:

1. run the regressions in `Stata`
2. extract the coefficient of interest
3. build a small plotting dataset
4. save the plotting dataset as `.dta`
5. use `R` only for plotting

A stylized Stata workflow might look like:

```stata
* Example idea only
* Build a plotting dataset after estimation

clear
input str30 outcome_label estimate ci_low ci_high plot_order str20 panel_label
"Outcome A"  0.120  0.040  0.200  1 "Main outcomes"
"Outcome B"  0.085  0.010  0.160  2 "Main outcomes"
"Outcome C" -0.060 -0.120  0.000  3 "Main outcomes"
"Outcome D"  0.150  0.070  0.230  4 "Main outcomes"
end

save "data/figure_data/coefplot_main.dta", replace
```

In a real project, the dataset would usually be constructed from stored regression results rather than typed manually.

---

## Complete R Example

```r
# ==========================================
# Example: Coefficient plot from Stata .dta
# ==========================================

# -------------------------
# 0. Packages
# -------------------------
library(haven)
library(dplyr)
library(ggplot2)
library(forcats)
library(stringr)

# -------------------------
# 1. Import Stata .dta
# -------------------------
coef_df <- read_dta("data/figure_data/coefplot_main.dta")

# -------------------------
# 2. Prepare plotting data
# -------------------------
coef_df <- coef_df %>%
  mutate(
    outcome_label = as.character(outcome_label),
    panel_label   = as.character(panel_label),
    outcome_label = fct_reorder(outcome_label, plot_order, .desc = TRUE)
  )

# -------------------------
# 3. Build a restrained Nature-style theme
# -------------------------
theme_paper <- function() {
  theme_minimal(base_family = "Arial", base_size = 11) +
    theme(
      panel.grid.major.y = element_blank(),
      panel.grid.minor = element_blank(),
      panel.grid.major.x = element_line(linewidth = 0.3),
      axis.title.y = element_blank(),
      axis.title.x = element_text(size = 11),
      axis.text = element_text(size = 10, colour = "black"),
      strip.text = element_text(size = 11, face = "bold"),
      panel.spacing = unit(0.9, "lines"),
      plot.title = element_text(size = 12, face = "bold"),
      plot.subtitle = element_text(size = 10),
      plot.caption = element_text(size = 9, hjust = 0),
      axis.line.x = element_line(colour = "black", linewidth = 0.3),
      axis.line.y = element_blank()
    )
}

# -------------------------
# 4. Plot
# -------------------------
p <- ggplot(coef_df, aes(x = estimate, y = outcome_label)) +
  geom_vline(xintercept = 0, linetype = "dashed", linewidth = 0.4, colour = "grey40") +
  geom_errorbarh(
    aes(xmin = ci_low, xmax = ci_high),
    height = 0.16,
    linewidth = 0.5,
    colour = "grey30"
  ) +
  geom_point(
    size = 2.3,
    shape = 16,
    colour = "black"
  ) +
  facet_wrap(~ panel_label, ncol = 1, scales = "free_y") +
  labs(
    x = "Coefficient estimate (95% confidence interval)",
    title = "Estimated policy effects across outcomes",
    subtitle = "Point estimates and 95% confidence intervals",
    caption = "Notes: Each point shows the coefficient estimate for the treatment variable. Horizontal lines indicate 95% confidence intervals. The dashed vertical line marks zero."
  ) +
  coord_cartesian(clip = "off") +
  theme_paper()

# -------------------------
# 5. Export
# -------------------------
ggsave(
  filename = "output/figures/fig3_coefficient_plot.pdf",
  plot = p,
  width = 7.2,
  height = 5.6,
  units = "in"
)
```

---

## Why This Example Works

This example follows the preferred logic of this workflow:

### 1. `Stata` remains the analytical backend
The regression and coefficient extraction are handled in `Stata`, not rebuilt in `R`.

### 2. `R` focuses on figure production
`R` handles:

- importing the `.dta`
- ordering labels
- building the figure
- styling
- exporting

### 3. The figure is easy to read
The plot makes it easy to see:

- whether estimates are positive or negative
- which outcomes are precisely estimated
- whether intervals cross zero
- how large effects are across outcomes

### 4. The design remains disciplined
This is a coefficient plot, not a decorative graphic.  
It is useful only when it helps comparison more clearly than a table alone.

---

## Nature-Style Design Choices in This Example

This example uses a restrained style consistent with Nature-like figure expectations:

- simple black points
- subtle reference line at zero
- light grid only on the x-axis
- minimal panel noise
- consistent typography
- no unnecessary color
- no visual clutter

This is preferable to:

- bright multicolor coefficient markers
- oversized points
- heavy gridlines
- crowded legends
- over-annotated panels

---

## Suggested Caption

A manuscript-ready caption could be written as:

> **Figure X. Estimated effects across outcome variables.**  
> Points indicate coefficient estimates for the treatment variable, and horizontal lines indicate 95% confidence intervals. The dashed vertical line marks zero. Outcomes are grouped by panel according to the manuscript’s empirical structure. See Table X for the corresponding regression specifications and sample definitions.

If this is a subgroup plot, revise accordingly:

> **Figure X. Heterogeneous effects across subgroups.**  
> Points indicate coefficient estimates for the treatment variable within each subgroup, and horizontal lines indicate 95% confidence intervals. The dashed vertical line marks zero. See Table X for specification details.

---

## Suggested Manuscript Language

Useful prose around the figure could be:

- `Figure X summarizes the estimated effects across outcomes.`
- `The plot shows that the point estimates are positive for most outcomes, although precision varies.`
- `The largest and most precisely estimated effects appear for ...`
- `The graphical pattern is consistent with the regression results reported in Table X.`

If the estimates are from supporting evidence rather than the main design:

- `These coefficient patterns should be interpreted as supportive rather than definitive evidence.`

---

## Common Mistakes to Avoid

Do not:

- use raw variable names as row labels
- mix incomparable specifications in one plot without explanation
- change the sample across rows without disclosing it
- omit the zero reference line
- use colors that are unnecessary for interpretation
- overload the plot with too many panels or too many coefficients
- let the plot imply stronger causal interpretation than the underlying estimates support

---

## When This Figure Belongs in the Main Text

Prefer main-text placement when the plot:

- summarizes a central result cleanly
- improves comparison across outcomes or groups
- supports a major argument in the paper
- is easier to read than a dense table alone

---

## When This Figure Belongs in the Appendix

Prefer appendix placement when the plot:

- only repeats a table visually
- is one of many robustness variants
- shows supplementary subgroup results
- is useful but not central to the narrative

---

## Working Rule

A good coefficient plot should let the reader answer quickly:

1. which estimates are being compared?
2. what is the sign of each estimate?
3. how precise are they?
4. do intervals cross zero?
5. does the figure clarify the argument better than the corresponding table?

If the answer is no, the figure probably belongs in a table or appendix instead.
