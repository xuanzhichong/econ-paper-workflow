# Color, Font, and Export Guide for Empirical Economics and Agricultural Economics Figures

Use this guide when producing publication-ready figures in `R` from `Stata`-processed `.dta` files.

This guide is designed for empirical economics and agricultural economics papers in which:

- `Stata` handles data cleaning, sample construction, and variable generation
- `R` handles figure production, layout, styling, and export

The goal is to produce figures that are:

- clean
- readable
- journal-ready
- reproducible
- visually consistent with **Nature / Nature-subjournal** expectations

This guide focuses on three areas:

1. **color discipline**
2. **font discipline**
3. **export discipline**

---

## 1. Core Principle

A publication-ready figure should not rely on styling to create a sense of importance.

Color, font, and export choices should:

- improve readability
- clarify structure
- support interpretation
- remain robust in grayscale, PDF print, and manuscript layout

A good figure should still work when:

- printed in black and white
- reduced to one-column width
- viewed on a projector
- embedded in a PDF with other figures

---

## 2. Color Discipline

## 2.1 Default Color Philosophy

Default to a **restrained palette**.

Color should be used to:

- distinguish analytically meaningful groups
- highlight one important contrast
- separate panels or figure families when needed

Color should **not** be used to:

- decorate the figure
- make the figure look more “modern”
- replace missing structure in labeling or layout

Working rule:

If the figure would still be clear in grayscale, the color design is probably disciplined enough.

---

## 2.2 When to Use Color

Color is most useful when the figure compares:

- regions
- groups
- categories
- time series by subgroup
- composition categories
- map intensity levels

Color is less necessary when the figure shows:

- a single national trend
- a single distribution
- a one-series descriptive plot
- a simple interval or coefficient display

In those cases, black, dark grey, and light grey are often sufficient.

---

## 2.3 Preferred Palette Logic

For economics and agricultural economics paper figures, default to one of the following strategies:

### A. Black / grey / one accent color

Best for:

- trend plots
- coefficient plots
- single-focus descriptive figures
- appendix figures

Use when you want:

- maximum print safety
- visual restraint
- one emphasized group against a neutral baseline

### B. Two- to four-color restrained palette

Best for:

- regional comparisons
- grouped trend plots
- composition figures with few categories
- multi-panel figures with repeated group identities

Use when:

- multiple groups must be separated clearly
- direct labeling alone is not enough

### C. Sequential gradient palette

Best for:

- choropleth maps
- ranked intensity plots
- distribution heat-style figures

Use when:

- the variable is continuous
- the reader needs to see ordered intensity rather than discrete categories

---

## 2.4 Recommended Color Behavior by Figure Type

### Descriptive trend plots

- use black for the main line if there is only one series
- use restrained contrasting colors only for substantively important groups
- avoid rainbow-style trend differentiation

### Group comparison plots

- use a small number of clearly distinguishable colors
- keep color identity consistent across related figures
- if the same region appears in multiple figures, keep the same color

### Composition plots

- use stable category colors across related figures
- avoid too many categories in one panel
- if categories exceed a readable palette, reconsider the figure design

### Maps

- use restrained sequential gradients for continuous variables
- avoid saturated red-green contrasts
- choose palettes that remain interpretable for color-deficient readers
- let missing values appear in a neutral light grey

### Multi-panel figures

- use the same color logic across all panels
- avoid reassigning colors between panels unless the variables truly differ
- the reader should not need to relearn color meaning panel by panel

---

## 2.5 What to Avoid in Color Design

Avoid:

- rainbow palettes
- highly saturated neon colors
- red/green as the only distinction
- too many categories in one legend
- one palette in panel (a) and a different logic in panel (b)
- using color to imply causal importance
- map palettes that create artificial breaks in continuous variation

---

## 2.6 Grayscale Check

Before finalizing a figure, ask:

- can the figure still be read if printed in grayscale?
- do line types, point shapes, or direct labels support interpretation if color is lost?
- is one series still identifiable without relying only on hue?

If the answer is no, revise the design.

---

## 3. Font Discipline

## 3.1 Font Principle

Fonts should support:

- legibility
- consistency
- journal compatibility
- clean visual hierarchy

The font system should never become the most noticeable part of the figure.

Default preference:

- a clean sans-serif font for most figure text
- a consistent font family across axes, legends, strip labels, and captions

---

## 3.2 Default Font Style

For most paper figures, default to a **clean sans-serif** look.

Good general choices include fonts in the style of:

- Arial
- Helvetica
- other clean journal-safe sans-serif families

For bilingual or Chinese-compatible figures, use a font strategy that preserves:

- English readability
- Chinese character support where needed
- visual consistency across scripts

Working rule:

Choose fonts that are widely readable and stable across export formats.

---

## 3.3 Font Hierarchy

A good figure should have a clear text hierarchy.

Typical order:

1. panel label
2. figure title
3. axis titles
4. legend title
5. axis text and legend text
6. note or caption text

This hierarchy should be visible through:

- size
- weight
- placement

not through decorative typography.

---

## 3.4 Font Weight Rules

Use bold sparingly.

Good uses of bold:

- panel tags such as `(a)`, `(b)`, `(c)`
- figure title when needed
- legend title when it helps structure

Avoid bold for:

- all axis text
- all legend entries
- entire captions
- too many labels at once

If everything is emphasized, nothing is emphasized.

---

## 3.5 Font Size Discipline

Font sizes should remain readable at manuscript scale.

A useful working rule:

- axis text should remain readable after the figure is reduced to journal column width
- panel labels should be visible but not oversized
- legend text should not be smaller than the axis text unless necessary
- titles should not dominate the data region

Do not create figures that only look readable at full-screen size.

---

## 3.6 Font Consistency

Keep fonts consistent across:

- axes
- legends
- strip labels
- panel tags
- captions embedded in the figure, if any

Do not mix multiple font families in one figure unless there is a compelling multilingual reason.

A figure that mixes unrelated font systems usually looks less professional.

---

## 3.7 What to Avoid in Font Use

Avoid:

- decorative fonts
- inconsistent font families across panels
- very thin fonts that disappear in print
- oversized titles
- undersized axis text
- heavy bold everywhere
- fonts that export unreliably into PDF

---

## 4. Export Discipline

## 4.1 Export Principle

Export is part of figure design, not an afterthought.

A figure is not ready until:

- the file format is appropriate
- the dimensions match likely manuscript use
- the text remains readable
- the output is reproducible

---

## 4.2 Preferred Export Formats

Default preference:

### Vector formats

Prefer for most journal figures:

- `.pdf`
- `.svg`

Best for:

- line plots
- maps
- coefficient plots
- trend plots
- multi-panel figures
- most non-photo figures

Reason:

- sharp text
- scalable output
- better print quality
- easier manuscript integration

### Raster formats

Use only when needed:

- `.png`
- `.tiff`

Appropriate when:

- the journal explicitly requires raster
- the figure uses raster-heavy elements
- a slide or web version is needed

Working rule:

Default to vector output unless there is a clear reason not to.

---

## 4.3 Dimension Discipline

Export dimensions should match intended use.

Typical use cases:

- one-column figure
- two-column figure
- full-page appendix figure
- slide figure

A figure should not be designed at one size and exported at a very different size without checking readability.

Before finalizing, ask:

- will the text still be readable at target width?
- will the legend still fit?
- will panel spacing still look balanced?

---

## 4.4 Resolution

For vector output, resolution is less central.  
For raster output, use journal-safe resolution.

Typical rule:

- use high resolution for final raster export
- avoid low-resolution screenshots as final outputs
- do not rely on copying plots manually from the R viewer

All final figures should be exported from code.

---

## 4.5 Stable Export Paths and Filenames

Use stable and manuscript-aligned names.

Preferred examples:

- `fig1_trend_plot.pdf`
- `fig2_map_provincial_distribution.pdf`
- `fig3_multi_panel_descriptive.pdf`
- `figA1_appendix_distribution_check.pdf`

Filenames should make it easy to trace:

- which script produced the figure
- whether it is a main-text or appendix figure
- where it belongs in the paper

---

## 4.6 Reproducible Export Code

Export should always be part of the script.

A good figure script should make clear:

- input file path
- output file path
- width
- height
- units
- output format

Do not rely on manual export clicks for final paper figures.

---

## 4.7 Caption and Export Consistency

Before exporting a final figure, verify that:

- panel labels match manuscript references
- legend wording matches the manuscript
- axis wording matches table terminology
- variable names are in reader-facing language
- the title, if used, does not overstate interpretation

Export discipline is partly a consistency discipline.

---

## 5. Nature-Style Defaults

When the user asks for a figure that matches **Nature / Nature-subjournal** style, default to:

- restrained, not flashy
- polished, not decorative
- clean typographic hierarchy
- consistent spacing
- subtle grid or no grid
- restrained color use
- grayscale-safe interpretation
- figure-first clarity, not stylistic excess

This means:

- moderate title size
- compact legend
- simple line weights
- careful whitespace
- clean margins
- no unnecessary visual effects

“Nature style” should mean **clarity plus refinement**, not aggressive styling.

---

## 6. Suggested R Workflow for Styling and Export

A clean R plotting workflow usually includes:

1. import processed `.dta`
2. prepare labels and factor order
3. define shared theme
4. define shared palette logic
5. build plot
6. check grayscale readability
7. export with explicit dimensions
8. save to stable file name

If multiple figures belong to one paper, try to share:

- one theme function
- one font setup block
- one palette logic
- one export naming convention

This improves consistency across the paper.

---

## 7. Common Mistakes

Avoid:

- using many bright colors without analytical need
- switching color logic across related figures
- mixing font families across panels
- exporting final figures from screenshots
- using low-resolution PNG as the only final version
- making titles too large relative to the panel
- shrinking axis labels until they disappear at journal size
- relying only on color when line type or direct labels are needed
- exporting figures whose final size has never been checked

---

## 8. Working Rule

A good color-font-export system should let a careful reader feel that the figure is:

- easy to read
- visually disciplined
- internally consistent
- professionally prepared
- appropriate for journal submission

If the styling is the most noticeable thing about the figure, the design is probably too aggressive.
