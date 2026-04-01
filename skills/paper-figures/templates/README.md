# Paper Figures Templates

This folder contains **optional template materials** for the `paper-figures` workflow.

The default logic of this workflow is:

- `Stata` handles data cleaning, sample construction, variable generation, aggregation, and exports processed `.dta` files
- `R` imports the processed `.dta` files and produces publication-ready figures

---

## Purpose of This Folder

The purpose of this folder is **not** to force a rigid script architecture.

Instead, it provides optional figure-production templates that can help with:

- planning a figure before coding
- keeping figure logic clear
- standardizing captions and notes
- organizing figure specifications for manuscript writing
- improving consistency across figures in the same paper

This folder is useful when the user wants lightweight structure without adopting an overengineered R-script system.

---

## Default Workflow Assumed Here

The current workflow should be understood as:

```text
Stata prepares processed `.dta`
    ->
R directly imports the relevant `.dta`
    ->
R writes figure-specific code
    ->
R exports a publication-ready figure
```

In other words:

- `Stata` is the analytical backend
- `R` is the figure-production tool
- each figure can be written as its own standalone plotting script if needed
- no global `R/00_setup.R`-style infrastructure is required

---

## What This Folder Should Contain

This folder should contain only **lightweight templates** that help organize figure work.

Appropriate contents include:

- `figure-plan.md`
- `figure-spec-sheet.md`
- `figure-caption-sheet.md`

These files are optional aids, not mandatory workflow components.

---

## What This Folder Should Not Assume

This folder should **not** assume:

- a fixed `R/` script hierarchy
- a shared `00_setup.R`
- a shared theme file
- a shared plot-data loader
- one-script-per-figure naming conventions as a hard rule

Those structures may be useful for some users, but they are **not part of the current default workflow**.

---

## Recommended Use in the Current Workflow

For the current workflow, a typical process looks like this:

1. prepare the figure-ready dataset in `Stata`
2. export the processed `.dta`
3. decide what the figure is supposed to show
4. optionally write a short figure plan or caption note using a template in this folder
5. write the `R` plotting code directly for that specific figure
6. export the final figure

This approach is especially suitable when:

- the number of figures is limited
- the user prefers direct control over each figure script
- the workflow is centered on `Stata -> .dta -> R`
- the user wants structure in planning, but not a heavy code framework

---

## Example Role of Each Template

### `figure-plan.md`

Useful for deciding:

- what the figure is for
- whether it belongs in the main text or appendix
- what variables are mapped to axes, color, or panels
- what the reader should learn from the figure

### `figure-spec-sheet.md`

Useful for recording:

- input `.dta` file
- sample or year shown
- plotting variable definitions
- intended figure type
- export filename

### `figure-caption-sheet.md`

Useful for drafting:

- manuscript-ready caption
- figure notes
- panel descriptions
- interpretation boundaries such as “descriptive” vs “regression-based”

---

## Minimal Working Style

Under the current workflow, a figure can be produced in a very simple way:

```text
processed `.dta` from Stata
    ->
one figure-specific R script
    ->
one exported figure file
```

This is fully acceptable.

A paper-ready workflow does **not** require a separate `00_setup.R` or `02_load_plot_data.R` as long as:

- the code is readable
- the `.dta` input is clear
- the export path is explicit
- the figure is reproducible

---

## Relation to the Overall Repository

This templates folder should support the larger `paper-figures` skill, whose main logic is:

- descriptive and trend-oriented figures are primary
- `R` is used mainly for plotting, not for main cleaning
- figures should match economics and agricultural economics paper norms
- visual style should remain clean, restrained, and suitable for **Nature / Nature-subjournal** standards

The templates should therefore support:

- clarity
- discipline
- reproducibility
- manuscript integration

They should not impose unnecessary technical structure.

---

## Working Rule

Use this folder as a **light planning and documentation aid**, not as a mandatory coding framework.

A good template system in the current workflow should make it easier to answer:

1. what is this figure supposed to show?
2. which `.dta` file is used?
3. how should the figure be described in the manuscript?
4. what should the caption say?
5. does the figure belong in the main text or appendix?

If the folder helps answer those questions without making the workflow heavier than necessary, it is doing its job.
