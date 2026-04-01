# Coefficient Plot Guide for Empirical Economics and Agricultural Economics

Use this guide when building coefficient plots in `R` from `Stata`-processed outputs.

This guide is for empirical economics and agricultural economics papers in which `Stata` handles estimation and exports a plotting-ready dataset, while `R` handles:

- importing the plotting dataset
- figure construction
- styling
- panel composition
- export

Coefficient plots are a **supported but non-default** figure family in this workflow.  
The default emphasis of `paper-figures` remains descriptive figures, development trends, composition figures, maps, and multi-panel descriptive figures.

Use coefficient plots only when they make the empirical comparison **clearer than a table alone could**.

---

## 1. What a Coefficient Plot Should Do

A good coefficient plot should help the reader answer quickly:

1. which estimates are being compared?
2. what is the sign of each estimate?
3. how large are the estimates?
4. how precise are they?
5. what is the comparison structure across rows, panels, or specifications?

A coefficient plot is useful when visual comparison is the main goal.  
If the figure does not improve comparison, a table may be better.

---

## 2. When to Use a Coefficient Plot

Coefficient plots are most useful when the paper needs to show:

- baseline estimates across several outcomes
- heterogeneity estimates across subgroups
- mechanism estimates across several mediators or channels
- robustness sweeps across alternative specifications
- effects across several related dependent variables
- side-by-side comparisons of specifications that share the same estimand

They are less useful when:

- there is only one core estimate
- the table is already very easy to read
- specifications are too different to compare visually
- the figure would duplicate the table without adding interpretive value

---

## 3. Default Workflow

```text
Estimate in Stata
    ->
Extract coefficient(s) of interest
    ->
Build plotting-ready `.dta`
    ->
Import `.dta` in R
    ->
Order labels and define panels
    ->
Plot point estimates and intervals
    ->
Export publication-ready figure
```

Default rule:

- `Stata` handles regression estimation and coefficient extraction
- `R` handles only plotting and layout

Do not rebuild the regressions in `R` unless the user explicitly asks for that.

---

## 4. Preferred Input Structure

The plotting dataset should usually contain one row per plotted estimate.

Recommended variables include:

| variable | meaning |
|---|---|
| `estimate` | point estimate |
| `ci_low` | lower confidence bound |
| `ci_high` | upper confidence bound |
| `label` | readable row label |
| `plot_order` | row order |
| `panel_label` | optional panel grouping |
| `sample_label` | optional sample or subgroup tag |
| `spec_label` | optional specification label |
| `outcome_label` | optional outcome label |

At minimum, the dataset should include:

- `estimate`
- `ci_low`
- `ci_high`
- one readable label field
- one order field if order matters

Recommended rule:

- labels should already have economic meaning before plotting
- do not use raw variable names as plot labels

---

## 5. What Counts as a Good Comparison

Coefficient plots work best when the plotted estimates are **comparable in meaning**.

Good comparisons include:

- same treatment, different outcomes
- same treatment, different subgroups
- same estimand, different robustness specifications
- same outcome, different samples with clear interpretation

Weak comparisons include:

- mixing reduced form, first stage, and second stage estimates in one undifferentiated panel
- mixing coefficients from substantively different models without explanation
- mixing estimates with different units without making that explicit
- plotting coefficients from different samples as if they were directly comparable when the sample changed silently

Working rule:

If the estimates are not comparable enough to discuss in one paragraph, they probably should not be in one coefficient plot.

---

## 6. Core Design Rules

### 6.1 Always include the zero line

A coefficient plot should normally include a visible reference line at zero.

Reason:

- it lets the reader assess sign and interval crossing immediately
- it reduces the need to decode each interval manually

### 6.2 Show uncertainty clearly

Use confidence intervals rather than point estimates alone.

Default expectation:

- 95% confidence intervals unless the paper clearly uses another convention
- interval type should be stated in the caption or note

### 6.3 Use readable labels

Labels should have economic meaning, such as:

- `Dietary diversity`
- `Animal-based protein share`
- `Eastern region`
- `Mechanism: market access`

Avoid labels such as:

- `y1`
- `var_3`
- `treat_post`
- `coef_2`

### 6.4 Control row order deliberately

Order should reflect one of the following:

- theoretical grouping
- magnitude
- empirical sequence used in the paper
- outcome family

Do not leave order accidental.

### 6.5 Use panels when comparisons belong to families

Facet or panel the plot when the rows naturally divide into groups, such as:

- main outcomes vs mechanism outcomes
- baseline outcomes vs heterogeneity outcomes
- food categories vs nutrient categories

Panels should clarify structure, not fragment the figure unnecessarily.

---

## 7. Nature-Style Defaults

When a coefficient plot is styled for a **Nature / Nature-subjournal** standard, default to:

- restrained visual design
- black or dark-grey points as the default
- subtle interval lines
- minimal clutter
- no unnecessary color
- clean typography
- balanced spacing
- legible labels even in grayscale

Preferred style features:

- one clear zero line
- no heavy background grid
- modest point size
- modest line width
- enough whitespace between rows
- compact but readable panel titles

Avoid:

- overly saturated colors
- thick, heavy interval bars
- oversized dots
- visually noisy legends
- decorative icons or arrows
- inconsistent styling across panels

---

## 8. Axis and Scale Rules

### 8.1 Be explicit about units

If coefficients are in:

- percentage points
- log points
- standard deviations
- elasticity units
- index units

the x-axis label or caption should say so clearly.

### 8.2 Keep scales comparable when comparison matters

If two panels are intended to be compared directly, they should usually share the same x-axis scale.

If scales differ, make that explicit and use the difference only when necessary for readability.

### 8.3 Do not crop economically important variation

Avoid truncating the x-axis in a way that exaggerates or compresses substantive differences.

---

## 9. Caption and Note Discipline

A good coefficient-plot caption or note should state, as relevant:

- what estimates are plotted
- what the points represent
- what the intervals represent
- sample
- specification family
- whether estimates come from the same or different models
- where the matching regression table appears
- any important sample or specification differences

Example caption logic:

> Points indicate coefficient estimates, and horizontal lines indicate 95% confidence intervals. The dashed vertical line marks zero. Estimates are taken from the baseline specification reported in Table X.

If multiple models are shown, say so directly.

---

## 10. Main Text vs Appendix Use

### Main text

Prefer main-text placement when the coefficient plot:

- summarizes a central result efficiently
- improves comparison across outcomes or groups
- is easier to interpret than a dense table
- supports a main paper argument

### Appendix

Prefer appendix placement when the coefficient plot:

- only visualizes supplementary robustness checks
- duplicates a table too closely
- shows secondary subgroup analyses
- is useful but not essential to the main narrative

---

## 11. Writing Around the Plot

Useful manuscript prose includes:

- `Figure X summarizes the estimated effects across outcomes.`
- `The plot shows that the estimates are positive for most outcomes, although precision varies.`
- `The largest and most precisely estimated effects appear for ...`
- `The graphical pattern is consistent with the regression results reported in Table X.`
- `These subgroup patterns should be interpreted as supportive rather than definitive evidence.`

Avoid:

- stronger causal language in the figure prose than in the table discussion
- implying that visual separation of intervals is itself proof of subgroup differences
- treating supportive evidence as a second main result

---

## 12. Common Use Cases

### 12.1 Baseline outcomes

Use when comparing a treatment effect across several related dependent variables.

Best for:

- dietary outcomes
- sustainability outcomes
- labor outcomes
- expenditure categories

### 12.2 Heterogeneity

Use when comparing subgroup estimates across:

- region
- income group
- gender
- farm size
- policy exposure intensity

Be careful not to imply that differences across subgroups are statistically different unless that has actually been tested.

### 12.3 Mechanism evidence

Use when comparing treatment effects on possible mediators or channels.

Use especially cautious language in captions and text.

### 12.4 Robustness sweeps

Use when comparing one treatment estimate across:

- alternative samples
- alternative treatment definitions
- alternative FE structures
- alternative inference choices

Only plot checks that address meaningful design threats.

---

## 13. Common Mistakes

Avoid the following:

- plotting incomparable specifications together
- using raw variable names as labels
- omitting the zero line
- plotting point estimates without intervals
- silently mixing different samples
- using visually heavy styling that obscures the estimates
- allowing panel scales to differ without disclosure
- using too many colors when none are needed
- overloading one figure with too many rows or panels
- treating a robustness sweep as if every estimate had identical interpretation

---

## 14. Recommended R Logic

A clean `R` workflow should usually include:

1. import the Stata `.dta`
2. convert labels to readable character variables
3. set row order explicitly
4. define a shared theme
5. add zero line
6. draw intervals first
7. draw points second
8. facet if needed
9. export to stable file name

Preferred package set may include:

- `haven`
- `dplyr`
- `ggplot2`
- `forcats`
- `patchwork`
- `showtext`
- `scales`

Keep the plotting script lean and transparent.

---

## 15. Working Rule

A good coefficient plot should let the reader answer quickly:

1. what is being estimated?
2. what is the sign and approximate magnitude?
3. how precise is the estimate?
4. what are the relevant comparisons across rows or panels?
5. does the figure clarify the empirical argument better than the corresponding table?

If the figure does not improve comparison, it probably belongs in a table or appendix instead.
