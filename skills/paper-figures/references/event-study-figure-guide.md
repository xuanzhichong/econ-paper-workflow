# Event-Study Figure Guide for Empirical Economics and Agricultural Economics

Use this guide when building **event-study figures in `R`** from `Stata`-processed outputs.

This guide is for empirical economics and agricultural economics workflows in which:

- `Stata` handles data cleaning, sample construction, estimation, and coefficient extraction
- `R` imports the plotting-ready `.dta` file and handles figure production, styling, and export

Event-study figures are a **supported but non-default** figure family in `paper-figures`.  
The default emphasis of the skill remains descriptive figures.  
Use an event-study figure only when it materially improves the reader’s understanding of dynamic treatment effects or identification support.

---

## 1. What an Event-Study Figure Should Do

A good event-study figure should help the reader answer quickly:

1. what is the omitted period?
2. where does treatment begin?
3. are the pre-treatment estimates reassuring, noisy, or trending?
4. how do estimates evolve after treatment?
5. how precise are the estimates at each relative-time period?

The figure should make the dynamic pattern **easier to read than a regression table alone**, not merely repeat the table in graphical form.

---

## 2. When to Use an Event-Study Figure

Event-study figures are most useful when the paper needs to show:

- dynamic treatment effects around policy adoption
- whether pre-treatment estimates are close to zero
- whether treatment effects emerge gradually or immediately
- whether effects persist, fade, or reverse over time
- how alternative event windows compare across specifications

They are less useful when:

- the paper has no meaningful dynamic component
- there is only one post-treatment coefficient of interest
- the figure would duplicate a very simple table without adding interpretive value
- the pre/post timing logic is not central to the design

---

## 3. Default Workflow

```text
Estimate event-study in Stata
    ->
Extract relative-time coefficients and confidence intervals
    ->
Build plotting-ready `.dta`
    ->
Import `.dta` in R
    ->
Define omitted period and treatment boundary visually
    ->
Plot point estimates and intervals
    ->
Export publication-ready figure
```

Default rule:

- `Stata` handles estimation and coefficient extraction
- `R` handles only plotting, styling, and export

Do not rebuild the event-study model in `R` unless the user explicitly asks for that.

---

## 4. Preferred Input Structure

The plotting dataset should usually contain **one row per event-time coefficient**.

Recommended variables include:

| variable | meaning |
|---|---|
| `event_time` | relative time, such as -5, -4, ..., 4, 5 |
| `estimate` | point estimate |
| `ci_low` | lower confidence bound |
| `ci_high` | upper confidence bound |
| `outcome_label` | optional readable outcome label |
| `panel_label` | optional panel grouping |
| `window_label` | optional event-window label |
| `spec_label` | optional specification label |

At minimum, the dataset should contain:

- `event_time`
- `estimate`
- `ci_low`
- `ci_high`

Recommended rule:

- the omitted period should be defined clearly in the manuscript and caption
- the plotting file should not silently omit coefficients without explanation
- if leads or lags are binned, that should already be reflected transparently in the data or caption

---

## 5. Core Design Rules

### 5.1 The omitted period must be explicit

The omitted period is central to interpretation and must be stated clearly.

Preferred practice:

- state it in the caption
- align the x-axis with the manuscript discussion
- if `t = -1` is omitted, say so directly

Do not assume the reader will infer the omitted period from the graph.

---

### 5.2 Treatment timing must be visually clear

A good event-study figure should show where treatment begins.

Preferred options:

- a subtle vertical line separating pre-treatment and post-treatment periods
- clear x-axis labeling with negative and positive relative times
- if `t = 0` is the first treated period, make that evident

Do not leave the treatment boundary visually ambiguous.

---

### 5.3 Always include the zero line

The horizontal zero line is usually essential.

Reason:

- it lets the reader assess sign and interval crossing immediately
- it helps the reader interpret pre-treatment estimates and dynamic responses

The zero line should be visible but subtle.

---

### 5.4 Show uncertainty clearly

Use confidence intervals rather than points alone.

Default expectation:

- 95% confidence intervals unless another convention is clearly stated
- interval type should be disclosed in the caption or note

Do not suppress wide intervals visually.  
Imprecision is part of the result.

---

### 5.5 Avoid visual smoothing

Event-study coefficients are discrete relative-time estimates.

Do not:

- apply smoothing that changes the meaning of the estimates
- use trend-fitting lines that suggest a continuous process unless clearly motivated and separately explained

A simple point-and-line display is usually enough.

---

## 6. Pre-Treatment Interpretation Discipline

Event-study figures often attract overinterpretation.

A disciplined figure should support this logic:

- pre-treatment coefficients close to zero are **consistent with**, not proof of, parallel trends or design validity
- distant leads may be noisy because support is thin
- the figure should make uncertainty visible rather than hiding it

Do not let the visual design imply stronger identification than the underlying design supports.

Preferred manuscript language includes:

- `The pre-treatment coefficients provide no strong evidence of differential pre-trends.`
- `The pre-treatment estimates are imprecise in the distant leads.`
- `The graphical pattern is consistent with the identification assumption, although it cannot fully establish it.`

---

## 7. Post-Treatment Interpretation Discipline

Use the post-treatment portion of the figure to show dynamic evolution clearly.

A good event-study figure can help the reader see whether:

- effects emerge gradually
- effects peak after some delay
- effects persist
- effects dissipate
- effects are noisy throughout the post period

Preferred manuscript language includes:

- `Post-treatment coefficients become positive after ...`
- `The effect grows over the first ... periods after treatment.`
- `The pattern suggests a gradual adjustment rather than an immediate response.`

Do not let the line visually imply a smooth structural process if the estimates are noisy and period-specific.

---

## 8. Nature-Style Defaults

When an event-study figure is styled for a **Nature / Nature-subjournal** standard, default to:

- restrained visual design
- black or dark-grey points and line by default
- subtle interval lines
- minimal clutter
- no unnecessary color
- clean typography
- balanced spacing
- compact, readable labels

Preferred style features:

- one clear zero line
- one clear treatment-boundary marker
- modest point size
- modest line width
- light or minimal grid
- sufficient whitespace around the data region

Avoid:

- heavy shading
- bright colors unless a specific comparison requires them
- oversized points
- thick confidence intervals
- large decorative annotations
- visually aggressive axis styling

---

## 9. Axis and Scale Rules

### 9.1 Use readable relative-time labels

The x-axis should make relative time easy to interpret.

Preferred practice:

- use integer event times
- keep the range substantively meaningful
- avoid crowding the axis with too many ticks

### 9.2 The y-axis label should state units clearly

Examples:

- `Coefficient estimate`
- `Effect on CHEI score`
- `Change in employment rate (percentage points)`

Do not leave the unit implicit when the coefficient scale matters.

### 9.3 Do not crop economically important variation

Avoid truncating the y-axis so aggressively that the reader cannot assess meaningful variation or interval width honestly.

---

## 10. Event Windows and Binning

If the event-study uses grouped leads or lags, disclose that clearly.

Examples:

- `≤ -5`
- `≥ 5`
- `-5 or earlier`
- `5 or later`

The figure should not make grouped endpoints look like ordinary single-period coefficients without explanation.

If multiple event windows are shown across panels or figures, keep labeling logic consistent.

---

## 11. Paneling Rules

Use panels when the event-study figure compares:

- multiple outcomes
- multiple subgroups
- baseline vs alternative windows
- main vs placebo specifications

Panels should only be used when they clarify structure.  
Do not facet automatically when one clean figure would be easier to read.

If panels are intended to be compared directly, use comparable scales when substantive comparison matters.

---

## 12. Caption and Note Discipline

A good event-study caption or note should state, as relevant:

- what is plotted
- what the points represent
- what the intervals represent
- omitted period
- treatment boundary or timing convention
- sample
- estimator or specification reference
- whether grouped leads/lags are used
- where the corresponding regression table appears

Example caption logic:

> Points indicate event-study coefficient estimates, and vertical bars indicate 95% confidence intervals. The omitted period is \( t = -1 \). The vertical line separates pre-treatment and post-treatment periods. See Table X for the corresponding specification and sample definition.

If the figure is placebo or appendix material, say so directly.

---

## 13. Main Text vs Appendix Use

### Main text

Prefer main-text placement when the event-study figure:

- is central to the identification argument
- helps the reader evaluate pre-treatment dynamics
- shows dynamic treatment effects central to the paper’s main claim
- improves interpretation relative to a dense coefficient table

### Appendix

Prefer appendix placement when the figure:

- is a placebo event-study
- shows alternative windows or robustness variants
- is one of many supplementary dynamic checks
- is useful but not central to the main narrative

---

## 14. Writing Around the Figure

Useful manuscript prose includes:

- `Figure X presents the event-study estimates around policy adoption.`
- `The omitted period is t = -1.`
- `The pre-treatment coefficients provide no strong evidence of differential pre-trends.`
- `Post-treatment coefficients become positive and larger over the first three years after treatment.`
- `The graphical pattern is consistent with the regression results reported in Table X.`

Use caution when discussing:

- noisy distant leads
- wide intervals
- dynamic patterns with limited support

Do not write:

- `The figure proves parallel trends.`
- `The graph definitively establishes identification.`

---

## 15. Common Mistakes

Avoid the following:

- omitting the omitted period from the caption
- leaving treatment timing visually ambiguous
- using smoothing that changes the meaning of discrete estimates
- suppressing wide confidence intervals visually
- mixing estimates from incomparable specifications in one panel
- plotting multiple outcomes together without enough labeling structure
- using bright colors without analytical need
- using grouped endpoints without disclosure
- overclaiming what the pre-treatment pattern establishes

---

## 16. Recommended R Logic

A clean `R` workflow should usually include:

1. import the Stata `.dta`
2. convert relative time to numeric
3. define any grouped endpoints clearly
4. build a shared theme
5. add zero line
6. add treatment-boundary marker
7. draw intervals first
8. draw points and connecting line second
9. export to a stable file name

Preferred package set may include:

- `haven`
- `dplyr`
- `ggplot2`
- `patchwork`
- `showtext`
- `scales`

Keep the plotting script lean and transparent.

---

## 17. Working Rule

A good event-study figure should let the reader answer quickly:

1. what is the omitted period?
2. where does treatment begin?
3. are the pre-treatment estimates reassuring or noisy?
4. how do estimates evolve after treatment?
5. does the figure clarify the identification and dynamic interpretation better than the table alone?

If the answer is no, the figure probably needs redesign or belongs in the appendix instead.
