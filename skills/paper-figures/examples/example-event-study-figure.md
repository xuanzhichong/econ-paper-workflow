# Example: Event-Study Figure from a Stata-Exported `.dta` File

This example shows how to build a **publication-ready event-study figure in R** after `Stata` has already produced a plotting dataset in `.dta` format.

This is a **supported but non-default** use of `paper-figures`.  
The default workflow of this skill is still descriptive figures, development-trend figures, and other non-regression-centered paper figures.  
However, event-study figures remain essential in many empirical economics and agricultural economics papers when the design relies on:

- dynamic treatment effects
- pre-trend assessment
- policy timing visualization
- post-treatment adjustment patterns

The example below follows the default division of labor:

- `Stata` handles data cleaning, estimation, and figure-data export
- `R` imports the `.dta` file and handles plotting, layout, styling, and export

---

## Figure Purpose

This figure is designed to help the reader see:

- the pattern of estimates before treatment
- the evolution of estimates after treatment
- whether the omitted period and treatment timing are clear
- whether confidence intervals are readable
- whether the dynamic pattern is consistent with the paper’s identification narrative

The figure should make the event-study evidence **easier to read than the regression table alone**.

---

## Typical Use Case

Suppose the paper estimates a staggered or non-staggered event-study specification and wants to visualize the coefficient path around treatment.

Examples:

- policy impact before and after rollout
- dynamic household response to a reform
- pre/post evolution of dietary or environmental outcomes
- labor or production response around program adoption

Typical manuscript use:

- main-text figure supporting identification and dynamic interpretation
- appendix figure for placebo or alternative-window checks

---

## Expected Input Data

The recommended workflow is that `Stata` exports a `.dta` file with one row per relative-time coefficient.

A typical plotting dataset may contain:

| variable | meaning |
|---|---|
| `event_time` | relative time, such as -5, -4, ..., 4, 5 |
| `estimate` | coefficient estimate |
| `se` | standard error |
| `ci_low` | lower 95% confidence bound |
| `ci_high` | upper 95% confidence bound |
| `is_pre` | indicator for pre-treatment period |
| `is_post` | indicator for post-treatment period |
| `panel_label` | optional panel grouping if multiple outcomes are plotted |
| `outcome_label` | optional readable outcome name |

At minimum, the plotting file should contain:

- `event_time`
- `estimate`
- `ci_low`
- `ci_high`

---

## Recommended Stata Output Logic

The preferred workflow is:

1. estimate the event-study model in `Stata`
2. extract the coefficients for each relative-time period
3. build a compact plotting dataset
4. save it as `.dta`
5. use `R` only for figure production

A stylized Stata workflow might look like:

```stata
* Example idea only
clear
input event_time estimate ci_low ci_high
-5 -0.012 -0.045  0.021
-4 -0.008 -0.038  0.022
-3 -0.004 -0.030  0.022
-2  0.006 -0.018  0.030
 0  0.028  0.006  0.050
 1  0.041  0.017  0.065
 2  0.054  0.026  0.082
 3  0.061  0.029  0.093
 4  0.049  0.012  0.086
 5  0.038 -0.004  0.080
end

save "data/figure_data/event_study_main.dta", replace
```

In a real project, this dataset would typically be created from regression output rather than typed manually.

---

## Complete R Example

```r
# ==========================================
# Example: Event-study figure from Stata .dta
# ==========================================

# -------------------------
# 0. Packages
# -------------------------
library(haven)
library(dplyr)
library(ggplot2)
library(stringr)

# -------------------------
# 1. Import Stata .dta
# -------------------------
es_df <- read_dta("data/figure_data/event_study_main.dta")

# -------------------------
# 2. Prepare plotting data
# -------------------------
es_df <- es_df %>%
  mutate(
    event_time = as.numeric(event_time),
    estimate   = as.numeric(estimate),
    ci_low     = as.numeric(ci_low),
    ci_high    = as.numeric(ci_high)
  )

# -------------------------
# 3. Build a restrained Nature-style theme
# -------------------------
theme_paper <- function() {
  theme_minimal(base_family = "Arial", base_size = 11) +
    theme(
      panel.grid.minor = element_blank(),
      panel.grid.major.x = element_blank(),
      panel.grid.major.y = element_line(linewidth = 0.3),
      axis.title = element_text(size = 11),
      axis.text = element_text(size = 10, colour = "black"),
      plot.title = element_text(size = 12, face = "bold"),
      plot.subtitle = element_text(size = 10),
      plot.caption = element_text(size = 9, hjust = 0),
      axis.line.x = element_line(colour = "black", linewidth = 0.3),
      axis.line.y = element_line(colour = "black", linewidth = 0.3),
      panel.border = element_blank()
    )
}

# -------------------------
# 4. Plot
# -------------------------
p <- ggplot(es_df, aes(x = event_time, y = estimate)) +
  geom_hline(yintercept = 0, linetype = "dashed", linewidth = 0.4, colour = "grey40") +
  geom_vline(xintercept = -0.5, linetype = "solid", linewidth = 0.4, colour = "grey55") +
  geom_errorbar(
    aes(ymin = ci_low, ymax = ci_high),
    width = 0.12,
    linewidth = 0.5,
    colour = "grey30"
  ) +
  geom_line(linewidth = 0.55, colour = "black") +
  geom_point(size = 2.2, colour = "black") +
  scale_x_continuous(
    breaks = seq(min(es_df$event_time), max(es_df$event_time), by = 1)
  ) +
  labs(
    x = "Event time",
    y = "Coefficient estimate",
    title = "Dynamic treatment effects around policy adoption",
    subtitle = "Points show event-study estimates; bars indicate 95% confidence intervals",
    caption = "Notes: The omitted period is t = -1. The vertical line separates pre-treatment and post-treatment periods. The horizontal dashed line marks zero."
  ) +
  coord_cartesian(clip = "off") +
  theme_paper()

# -------------------------
# 5. Export
# -------------------------
ggsave(
  filename = "output/figures/fig2_event_study.pdf",
  plot = p,
  width = 7.0,
  height = 4.8,
  units = "in"
)
```

---

## Why This Example Works

This example follows the preferred workflow of the repository:

### 1. `Stata` remains the analytical backend
The sample construction, estimation, and coefficient extraction are done in `Stata`, not rebuilt in `R`.

### 2. `R` focuses on figure production
`R` handles:

- importing the `.dta`
- building the event-study plot
- controlling visual hierarchy
- exporting a publication-ready figure

### 3. The figure is analytically legible
The plot makes it easy to see:

- whether pre-treatment estimates are close to zero
- how effects evolve after treatment
- where the omitted period sits
- whether uncertainty is substantial in each period

### 4. The design remains disciplined
The figure is not decorative.  
It is useful only if it helps the reader interpret the dynamic pattern more clearly than the table alone.

---

## Nature-Style Design Choices in This Example

This example uses a restrained style consistent with Nature-like figure expectations:

- black points and line for the main estimate path
- subtle dashed horizontal reference at zero
- subtle vertical reference separating pre and post periods
- light horizontal grid only
- no unnecessary color
- no visual clutter
- balanced use of points, line, and intervals

This is preferable to:

- bright multicolor lines
- oversized points
- heavy shading
- crowded annotations
- ambiguous treatment markers

---

## Suggested Caption

A manuscript-ready caption could be written as:

> **Figure X. Event-study estimates around policy adoption.**  
> Points indicate coefficient estimates for each event-time period, and vertical bars indicate 95% confidence intervals. The omitted period is \( t = -1 \). The vertical line separates pre-treatment and post-treatment periods, and the horizontal dashed line marks zero. See Table X for the corresponding regression specification, sample definition, and inference details.

If the figure is in the appendix:

> **Figure A.X. Alternative event-study window.**  
> Points indicate event-study coefficient estimates, and vertical bars indicate 95% confidence intervals. The omitted period is \( t = -1 \). See Appendix Table A.X for the matching regression specification.

---

## Suggested Manuscript Language

Useful prose around the figure could be:

- `Figure X presents the event-study estimates around policy adoption.`
- `The pre-treatment coefficients provide no strong evidence of differential pre-trends.`
- `Post-treatment estimates become positive and larger over the first three years after adoption.`
- `The graphical pattern is consistent with the regression results reported in Table X.`

If the pattern is noisier:

- `Although some post-treatment coefficients are imprecisely estimated, the overall pattern suggests a positive dynamic response after treatment.`

If caution is needed:

- `The pre-treatment pattern is broadly reassuring, although distant leads are estimated with limited precision.`

---

## Common Mistakes to Avoid

Do not:

- omit the omitted period from the caption or note
- leave treatment timing visually ambiguous
- use smoothing that changes the meaning of point estimates
- present grouped or binned leads/lags without disclosure
- mix estimates from incomparable specifications in one plot
- let the figure imply stronger identification than the design supports
- use raw relative-time labels that are unreadable
- suppress wide confidence intervals visually

---

## When This Figure Belongs in the Main Text

Prefer main-text placement when the plot:

- is central to the identification argument
- helps assess pre-trends
- shows dynamic treatment effects relevant to the paper’s main claim
- is easier to interpret than a dense table of coefficients

---

## When This Figure Belongs in the Appendix

Prefer appendix placement when the plot:

- is a placebo event-study
- shows alternative windows or bandwidth-like choices
- is one of many robustness variants
- is useful but not central to the main narrative

---

## Working Rule

A good event-study figure should let the reader answer quickly:

1. what is the omitted period?
2. where does treatment begin?
3. are the pre-treatment estimates reassuring or noisy?
4. how do estimates evolve after treatment?
5. does the graphical pattern clarify the identification and dynamic interpretation better than the table alone?

If the answer is no, the figure probably needs redesign or belongs in the appendix instead.
