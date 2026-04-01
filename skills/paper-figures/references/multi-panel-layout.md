# Multi-Panel Layout Guide for Empirical Economics and Agricultural Economics Figures

Use this guide when building **multi-panel figures in `R`** from **Stata-processed `.dta` files**.

This guide is designed for a workflow in which:

- `Stata` handles data cleaning, sample construction, aggregation, variable generation, and exports processed `.dta` files
- `R` handles figure production, layout, styling, panel composition, and export

The purpose of a multi-panel layout is not to save space mechanically.  
Its purpose is to let several related figures work together as **one larger empirical message**.

A good multi-panel figure should feel like one coherent argument, not a collage.

---

## 1. Core Principle

A strong multi-panel figure should help the reader answer quickly:

1. what is the larger question linking these panels?
2. what does each panel contribute?
3. why are these panels shown together?
4. does the combined layout improve interpretation relative to separate figures?

If the panels do not support one larger descriptive or empirical point, they probably should not be combined.

---

## 2. When to Use a Multi-Panel Figure

Multi-panel figures are most useful when the paper needs to present several **closely related** pieces of evidence together.

Common use cases include combining:

- a national trend with subgroup trends
- a descriptive trend with a structural composition panel
- a map with a trend plot and a group comparison plot
- several related descriptive patterns that motivate the same later regression section
- a main panel plus one closely related supplementary panel

Use a multi-panel figure when joint reading improves:

- efficiency
- coherence
- comparison
- narrative flow

Do **not** use a multi-panel layout merely because several graphs exist.

---

## 3. When Not to Use a Multi-Panel Figure

Avoid combining panels when:

- they answer unrelated questions
- they rely on different conceptual units with no clear bridge
- one panel is descriptive and another is technical, but the distinction is not explained
- the combined figure becomes too crowded
- the reader would understand the argument more clearly from separate figures
- one panel dominates and makes the others look incidental

Working rule:

If the panels cannot be introduced together in one clean paragraph, the layout is probably too loose.

---

## 4. The “One Larger Argument” Test

Before creating a multi-panel figure, write one sentence that starts with:

> This figure shows that ...

If you cannot finish that sentence without listing unrelated claims, the figure is not yet coherent enough.

Good examples:

- `This figure shows how dietary quality evolved over time, how the pattern differed across regions, and how diet composition changed in the latest year.`
- `This figure shows the geographic distribution of the outcome and the national and subgroup trends that motivate the later analysis.`

Weak examples:

- `This figure shows several additional results.`
- `This figure combines all the descriptive plots.`

---

## 5. Typical Multi-Panel Structures

## 5.1 Trend + subgroup trend + composition

Useful when the paper needs to establish:

- overall evolution
- subgroup divergence
- structural interpretation

Typical layout:

- Panel (a): national trend
- Panel (b): subgroup trend
- Panel (c): composition or structure

---

## 5.2 Map + trend + comparison

Useful when the paper needs to show:

- spatial variation
- temporal evolution
- cross-group difference

Typical layout:

- Panel (a): map
- Panel (b): national trend
- Panel (c): regional comparison

---

## 5.3 Three closely related descriptive panels

Useful when all three panels belong to the same section and answer one descriptive question from different angles.

Typical layout:

- Panel (a): overall level
- Panel (b): subgroup pattern
- Panel (c): distribution or composition

---

## 5.4 Appendix multi-panel robustness display

Useful when several supplementary figures belong to one technical point.

Typical layout:

- Panel (a): baseline descriptive plot
- Panel (b): alternative sample
- Panel (c): alternative grouping
- Panel (d): placebo or supplementary descriptive cut

This is acceptable only when the appendix layout remains readable.

---

## 6. Panel Order Should Be Analytical

Panel order is part of the argument.

Good ordering principles include:

- broad-to-specific
- national-to-regional
- overall-to-subgroup
- descriptive context-to-structural detail
- map-to-time trend-to-comparison
- main pattern first, supporting pattern second

Avoid:

- arbitrary order based on when code was written
- alphabetical order of panels
- visually balanced order with no analytical logic

Working rule:

The panel order should match the order in which you want the reader to think.

---

## 7. Panel Balance

A good multi-panel figure should feel balanced.

Balance does not always mean equal size.  
It means:

- no panel is unintentionally crowded
- no panel is too visually weak relative to the others
- the layout reflects analytical importance
- whitespace and margins are consistent

When one panel is conceptually central, it may be given more space.  
But that should be intentional, not accidental.

---

## 8. Equal Size vs Unequal Size Panels

### Equal-size panels

Prefer when:

- panels have similar analytical weight
- the panels invite direct visual comparison
- the data density is similar across panels

### Unequal-size panels

Prefer when:

- one panel is clearly the main panel
- a map needs more horizontal or vertical space
- one panel contains more categories or labels
- the layout would otherwise look cramped

Unequal sizing is acceptable when it supports readability and hierarchy.

---

## 9. Shared Styling Across Panels

All panels in a multi-panel figure should share a common visual language.

Keep consistent:

- font family
- font size logic
- axis title style
- gridline logic
- line widths
- point sizes
- legend style
- panel tag style
- whitespace discipline

A multi-panel figure should look like **one figure family**, not like three unrelated charts.

---

## 10. Shared vs Panel-Specific Scales

### Use shared scales when:

- cross-panel comparison is substantively important
- the same variable is shown in each panel
- different scales would distort interpretation

### Use panel-specific scales when:

- variables differ in unit or range
- forcing one common scale would hide meaningful patterns
- the panels are related conceptually but not directly comparable numerically

If scales differ, make that clear through:

- axis labels
- panel titles
- caption wording

Do not let differing scales silently create misleading visual comparison.

---

## 11. Titles, Panel Labels, and Subtitles

A good multi-panel figure usually needs:

- one overall figure title or caption logic
- panel labels such as `(a)`, `(b)`, `(c)`
- optional short panel titles when helpful

### Panel label rules

- use a consistent format, such as `(a)`, `(b)`, `(c)`
- place them consistently
- keep them visible but not oversized
- ensure manuscript references match them exactly

### Panel title rules

- use short, functional titles
- avoid repeating the same wording unnecessarily
- keep titles parallel in structure if panels are related

Good example:

- `(a) National trend`
- `(b) Regional comparison`
- `(c) Diet structure in 2015`

---

## 12. Caption Logic for Multi-Panel Figures

A strong multi-panel caption should do two things:

1. state the larger point of the figure
2. decode each panel clearly

A useful structure is:

- one opening sentence describing the overall figure
- one sentence listing panel contents in order
- one short sentence clarifying sample or evidence type if needed

Example:

> **Figure X. Descriptive patterns of dietary quality and composition.**  
> Panel (a) shows the national average CHEI over time. Panel (b) reports average CHEI by region. Panel (c) reports the composition shares of key dietary components in 2015. All panels are descriptive and are constructed from Stata-processed analytical datasets.

Do not force the reader to guess which sentence refers to which panel.

---

## 13. Nature-Style Defaults

When the target is **Nature / Nature-subjournal** style, multi-panel layouts should default to:

- clean alignment
- consistent typography
- restrained annotation
- balanced spacing
- limited but meaningful color use
- no panel crowding
- enough whitespace to preserve readability
- simple overall layout that guides the eye naturally

This means:

- polished but restrained
- compact but not cramped
- visually coherent without being flashy

Nature-style multi-panel figures should look carefully composed, not merely tightly packed.

---

## 14. Typical Layout Patterns

## 14.1 Side-by-side layout

Best when:

- two panels form a direct comparison
- both panels have similar analytical weight
- horizontal comparison is intuitive

Example:

- `(a)` national trend | `(b)` subgroup trend

---

## 14.2 Top row + bottom row layout

Best when:

- two small related panels sit above one wider summary panel
- one panel needs more width
- one panel serves as a synthesis or structure panel

Example:

- top row: `(a)` and `(b)`
- bottom row: `(c)` full-width panel

---

## 14.3 Grid layout

Best when:

- 4 panels or more belong to one coherent family
- each panel has similar structure
- direct comparison across many related panels matters

Use carefully.  
Do not create a dense grid unless the paper really benefits from it.

---

## 14.4 One large panel + one or two supporting panels

Best when:

- one panel is clearly central
- the others provide context or decomposition
- one map or trend panel needs more space

This often works well for main-text figures.

---

## 15. Legend Management in Multi-Panel Figures

Legends should be handled at the figure level whenever possible.

Good practice:

- use one shared legend for several compatible panels
- remove repeated legends from individual panels
- place the combined legend where it does not dominate the layout

Avoid:

- repeating the same legend in every panel
- inconsistent legend wording across panels
- large legends that distort panel spacing

If the panels use different encodings, consider whether they truly belong together.

---

## 16. Alignment Rules

Panels should align in a way that helps reading.

Check:

- vertical edges line up
- horizontal edges line up
- titles and panel tags are positioned consistently
- plots do not appear to float unevenly
- axis titles do not create unnecessary asymmetry

Even strong individual panels can look weak if alignment is poor.

---

## 17. Whitespace Rules

Whitespace is functional in multi-panel design.

Use whitespace to:

- separate panels
- prevent crowding
- clarify grouping
- keep panel labels readable
- prevent the caption or legend from colliding with the data region

Avoid trying to fill every empty space.  
A cramped multi-panel figure is harder to interpret than a slightly larger or simpler one.

---

## 18. Combining Different Figure Types

Combining different figure types is acceptable when they support one larger descriptive or empirical point.

Good combinations:

- map + trend
- trend + composition
- comparison plot + distribution plot

Risky combinations:

- map + coefficient plot + dense distribution plot with no clear common narrative
- highly technical regression panel + simple descriptive bar plot without explanation
- panels with completely different visual logic and no unifying purpose

Working rule:

Different geometries are acceptable, but different **arguments** are not.

---

## 19. Main Text vs Appendix Multi-Panel Figures

### Main text

Prefer main-text multi-panel figures when they:

- present a central descriptive narrative efficiently
- save space without sacrificing clarity
- unify several closely related panels
- help the reader understand the paper before the regression results

### Appendix

Prefer appendix multi-panel figures when they:

- collect supplementary descriptive patterns
- present several robustness-related visual checks
- support transparency without being central
- would otherwise clutter the main text

Not every multi-panel figure deserves main-text placement.

---

## 20. Common Mistakes

Avoid the following:

- combining unrelated panels
- using inconsistent themes across panels
- crowding too many panels into one page
- letting one panel be unreadably small
- using different color logic panel by panel without reason
- failing to explain each panel in the caption
- repeating legends unnecessarily
- using inconsistent panel labels or title styles
- relying on tight packing instead of clear structure
- creating a visually compact figure that is conceptually incoherent

---

## 21. Recommended R Workflow

A clean multi-panel workflow in `R` usually includes:

1. import each processed `.dta`
2. build each panel separately
3. apply a shared theme
4. remove redundant legends
5. combine panels with `patchwork` or `cowplot`
6. add figure-level title or annotation if needed
7. export with explicit width and height

Preferred packages may include:

- `ggplot2`
- `patchwork`
- `cowplot`
- `haven`
- `dplyr`
- `showtext`
- `scales`
- `sf` if maps are included

Keep the panel construction modular rather than writing one giant plotting block.

---

## 22. Working Rule

A good multi-panel layout should let the reader answer quickly:

1. what larger question links these panels?
2. what does each panel show?
3. why is the order what it is?
4. does the combined layout improve interpretation?
5. does the figure feel like one coherent argument rather than a collage?

If the layout is compact but not conceptually unified, it is not yet a good multi-panel figure.
