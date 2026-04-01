# Figure Design Principles for Empirical Economics and Agricultural Economics

Use this guide when designing publication-ready figures in `R` from `Stata`-processed `.dta` files.

This guide is built for a workflow in which:

- `Stata` handles data cleaning, sample construction, aggregation, variable generation, and estimation
- `R` handles figure production, layout, styling, and export

The purpose of figure design is not to make a paper look modern.  
Its purpose is to make the empirical argument:

- easier to understand
- easier to verify
- easier to remember
- harder to misread

A well-designed figure should improve analytical clarity, not compete with it.

---

## 1. Core Principle

A good figure should help the reader answer at least one important question more quickly than text or a raw table alone could.

Typical questions include:

1. what is the main descriptive pattern?
2. how does an outcome evolve over time?
3. how do groups differ?
4. how is a variable distributed across space or categories?
5. how do several related descriptive patterns fit together?

If the figure does not improve the reader’s understanding of one of these questions, it probably does not belong in the paper.

---

## 2. Design Before Styling

Figure design comes before figure styling.

Before choosing:

- colors
- fonts
- line widths
- panel spacing
- legend placement

first decide:

- what the figure is for
- what exact pattern it should communicate
- what the reader should learn from it in one sentence
- whether a figure is better than a table for that purpose

A weak analytical figure does not become a strong figure by adding polish.

---

## 3. One Figure, One Main Job

A strong paper figure should usually do **one main job**.

Examples:

- show a national trend
- compare regional means
- summarize a structure or composition
- show a map of geographic variation
- combine several related descriptive panels into one coherent narrative figure

Avoid figures that try to do too many jobs at once, such as:

- showing trends, subgroup comparisons, and composition shifts all in one crowded panel
- combining unrelated descriptive patterns because they fit on one page
- using one figure to summarize the entire paper

Working rule:

If you need a long paragraph just to explain what the figure is doing, the design is probably overloaded.

---

## 4. Analytical Priority Over Decoration

The figure should prioritize:

- readable scales
- meaningful grouping
- informative ordering
- visible comparison structure
- clean labeling

The figure should not prioritize:

- novelty of appearance
- decorative icons
- excessive gradients
- crowded annotation
- visual flourishes that do not improve interpretation

A paper figure is not an infographic.

---

## 5. The Figure Must Match the Evidence Type

The design should reflect what kind of evidence the figure shows.

### Descriptive figures

Design should emphasize:

- pattern
- level
- trend
- comparison
- distribution

Captions and titles should remain descriptive.

### Regression-based figures

Design should emphasize:

- estimate
- uncertainty
- comparison of coefficients or dynamic effects
- identifying structure if relevant

Do not use a descriptive design to imply a regression result.  
Do not use a regression-style design for a purely descriptive figure unless the logic is made explicit.

---

## 6. Clarity of Comparison

A figure should make the intended comparison obvious.

Common comparison structures include:

- across time
- across groups
- across regions
- across categories
- across panels

A well-designed figure should make clear:

- what is being compared
- on what scale
- with what ordering
- using which visual distinction

If the comparison structure is hidden, the figure will feel harder than the table it was supposed to improve upon.

---

## 7. Ordering Is Analytical, Not Cosmetic

Ordering choices should be substantive.

Good ordering principles include:

- time order
- geographic order
- theoretical order
- policy relevance order
- rank order when ranking itself is meaningful

Avoid:

- arbitrary alphabetical order when it obscures the empirical pattern
- random ordering from the input data
- letting software defaults determine category order

A reader should not have to mentally reorder the plot to understand it.

---

## 8. Visual Hierarchy

Good figure design uses hierarchy so the reader sees the data first and the supporting structure second.

The visual hierarchy should usually be:

1. main data layer
2. reference structure
3. labels and legends
4. decorative or contextual elements

This means:

- the main line or points should be visually primary
- gridlines should be secondary
- legends should not dominate the page
- annotations should support, not overwhelm

If gridlines, fills, or legends are more noticeable than the data, the hierarchy is wrong.

---

## 9. Use the Simplest Effective Geometry

Choose the simplest graphical form that communicates the pattern well.

Examples:

### Good matches

- line plot for a time trend
- dot-and-interval plot for comparisons with uncertainty
- choropleth map for spatial intensity
- bar plot only when levels or shares are the real object of interest
- multi-panel layout when several related plots need to be read together

### Poor matches

- grouped bars when a dot plot would be clearer
- stacked bars when subgroup comparison is the real goal
- pie charts for complex composition patterns
- heatmaps when the scale and ordering are not meaningful
- 3D charts under any normal paper-writing circumstance

Working rule:

Use the geometry that makes comparison easiest, not the one that looks most varied.

---

## 10. Labels Must Carry Meaning

Every major label should use reader-facing language.

This includes:

- axis titles
- legend labels
- panel titles
- caption wording
- map legend titles

Prefer:

- `CHEI score`
- `Animal-based protein share`
- `Eastern region`
- `Year`
- `Share of total expenditure (%)`

Avoid:

- `var1`
- `ratio_a`
- `g2`
- `y`
- raw internal Stata or R variable names

The figure should be legible without requiring the reader to decode your variable naming system.

---

## 11. Units Must Be Explicit

The reader should not have to guess whether the figure shows:

- levels
- shares
- percentages
- percentage points
- index values
- log values
- standardized values

Units should be explicit in:

- axis labels
- legends
- captions
- notes where relevant

A figure without unit clarity invites misinterpretation.

---

## 12. Scales Should Be Honest

Scale choices strongly shape interpretation.

A good figure design should:

- make scale choices legible
- avoid truncation that exaggerates small differences
- avoid compression that hides substantive differences
- keep panel scales comparable when comparison matters

If panel scales differ, that should be intentional and clearly justified by readability.

Working rule:

Do not let the design create drama that is not in the data.

---

## 13. Whitespace Is Functional

Whitespace is not wasted space.

It helps:

- separate panels
- reduce crowding
- clarify grouping
- improve reading order
- keep titles and legends from competing with the data

A crowded figure is often harder to understand than two simpler figures.

---

## 14. Legends Should Be Secondary

A strong figure minimizes legend dependence.

Preferred approaches:

- direct labeling when feasible
- concise legends
- stable color or linetype meaning across figures
- placing legends near the data without obstructing them

Avoid:

- long legends with many categories
- legend titles that repeat the axis title
- legends that dominate the bottom or right side of the figure
- forcing the reader to move constantly between plot and legend

If a legend is necessary, it should be compact and easy to decode.

---

## 15. Panel Design Should Create One Larger Figure

A multi-panel figure should feel like one larger argument, not several unrelated charts placed together.

A good multi-panel figure should:

- have a shared theme
- use consistent fonts and spacing
- use aligned panel labels
- support one broader descriptive point
- keep panel order analytically meaningful

Do not combine panels just to save space.  
Combine them only when joint reading improves interpretation.

---

## 16. Nature-Style Means Refined Restraint

When the user wants **Nature / Nature-subjournal** style, interpret that as:

- clean
- balanced
- typographically controlled
- low-clutter
- high-clarity
- visually restrained

It does **not** mean:

- hyper-stylized
- aggressively colorful
- crowded with annotations
- designed to impress before it informs

A Nature-style figure should look polished because the structure is strong, not because the styling is loud.

---

## 17. Consistency Across the Paper Matters

Figures should work as a family, not as isolated objects.

Across the paper, keep consistent:

- font system
- color logic
- panel label style
- axis wording conventions
- legend placement logic
- export sizes
- caption discipline

If one figure uses `Province` and another uses `Region`, or one uses sentence-case titles while another uses title-case headings, the paper will feel less coherent.

---

## 18. Main Text vs Appendix Design

Main-text figures should usually be:

- cleaner
- more focused
- more central to the paper’s narrative
- easier to read quickly

Appendix figures can be:

- more detailed
- more diagnostic
- more supplementary
- less visually central

But appendix figures should still be readable and disciplined.  
“Appendix” is not a license for poor design.

---

## 19. Common Design Mistakes

Avoid the following:

- trying to show too many messages in one figure
- using categories or panels with no clear analytical ordering
- overusing color
- using bars when dots or lines would make comparison easier
- crowding the plot with labels, arrows, and notes
- letting legends dominate the layout
- mixing inconsistent styles across panels
- allowing axis labels to remain vague or unit-free
- making the figure visually attractive but analytically unhelpful
- using map figures or multi-panel layouts when they do not add substantive clarity

---

## 20. A Good Design Workflow

Before finalizing a figure, ask:

### Analytical questions

- what exact question does this figure answer?
- is a figure better than a table here?
- what should the reader learn in one sentence?
- what is the primary comparison?

### Structural questions

- is the ordering meaningful?
- are the labels reader-facing?
- are the scales honest?
- is the main data layer visually primary?

### Paper-level questions

- does the figure fit the manuscript narrative?
- does it belong in the main text or appendix?
- is its style consistent with the rest of the paper?

---

## 21. Working Rule

A well-designed figure should let a careful reader answer quickly:

1. what is being shown?
2. what should I compare?
3. what is the main pattern?
4. how should I interpret it?
5. why is this figure in the paper?

If the figure looks polished but makes those questions harder rather than easier to answer, the design is not yet good enough.
