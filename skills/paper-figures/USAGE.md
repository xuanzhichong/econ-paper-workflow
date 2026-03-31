# Paper Figures Usage

This skill now defaults to empirical economics and agricultural economics figure workflows.

Use it when the goal is to turn empirical results into **publication-ready figures in R**, while keeping `Stata` responsible for data cleaning, sample construction, and econometric estimation.

---

## Typical Use Cases

This skill is best suited for tasks such as:

- turning `Stata` regression results into journal-ready figures
- drawing event-study plots in `R`
- drawing coefficient plots for baseline, robustness, heterogeneity, or mechanism results
- building multi-panel figures for the main text or appendix
- refining an existing `R` figure to better match **Nature / Nature-subjournal** style
- designing figure layouts, captions, and export rules for submission-ready papers

It is especially appropriate when the user wants figures that are:

- clean
- readable
- publication-ready
- identification-oriented
- visually consistent across the paper

---

## Typical Prompts

### 中文场景

- 帮我根据 `Stata` 导出的 event study 结果画一张 `R` 图
- 我已经有回归结果表，帮我做一个系数图
- 帮我把这几张图拼成一张主文 multi-panel 图
- 根据我的数据和期刊目标，帮我设计一张符合 `Nature` 风格的图片
- 我用 `Stata` 导出了 `.csv`，请你帮我写完整的 `R` 画图代码
- 帮我改进这张图的字体、配色、坐标轴和排版
- 帮我写图注和 caption
- 帮我判断这张图应该放主文还是 appendix
- 我想画异质性 forest plot，请帮我整理结构并给出 `R` 代码
- 帮我把 `Stata` 和 `R` 的画图工作流接起来

### English-style prompts

- Help me turn this `Stata` event-study output into a publication-ready `R` figure
- Build a coefficient plot from these regression estimates
- Create a multi-panel figure for the main paper using `R`
- Rewrite this plotting code so the figure matches a **Nature-style** standard
- Draft a caption and figure note for this empirical figure
- Help me decide whether this figure belongs in the main text or appendix

---

## Expected Inputs

Typical inputs may include:

- plot-ready `.csv`
- plot-ready `.dta`
- `.xlsx` files prepared for figure use
- `Stata` output tables
- event-study coefficient tables
- regression result tables
- figure sketches or screenshots
- existing `R` plotting code
- journal target or stated style preference
- instructions on whether the figure is for:
  - main text
  - appendix
  - slides
  - advisor circulation

Preferred input style:

- `Stata` prepares the plot-ready dataset
- `R` handles visualization, layout, and export

This skill should **not** assume that `R` is doing the main cleaning unless the user explicitly asks for that.

---

## Expected Outputs

Typical outputs may include:

- complete runnable `R` plotting code
- `figure-plan.md`
- `figure-spec-sheet.md`
- `figure-caption-sheet.md`
- figure revision suggestions
- export recommendations
- publication-ready outputs such as:
  - `.pdf`
  - `.svg`
  - high-resolution `.png` when requested

When the user asks for code, the default should be:

- provide a **complete runnable version**
- include clear sectioning and comments
- use stable filenames and export paths

When the user asks for design guidance, the default should be:

- clarify the figure purpose
- recommend the right figure family
- explain how the figure supports the paper’s empirical logic

---

## Default Workflow Expectations

The skill should usually proceed as follows:

1. identify what the figure is supposed to show
2. determine whether the figure is descriptive, design-oriented, or regression-based
3. inspect the structure of the input data
4. decide the appropriate figure family
5. map variables to visual elements
6. generate or revise the `R` code
7. recommend a journal-ready export format
8. provide caption or note language when useful

The skill should prioritize **analytical clarity** over decoration.

---

## Preferred Figure Families

Default figure families include:

- event-study plots
- coefficient plots
- descriptive trend plots
- heterogeneity forest plots
- mechanism-support figures
- maps and spatial figures
- multi-panel figures
- appendix robustness figures

The skill should recommend the figure family that best matches the empirical purpose, rather than defaulting to generic bar charts or decorative visuals.

---

## Nature-Style Default

When the user asks for figures that match **Nature** or **Nature-subjournal** style, the skill should default to:

- clean and minimal layout
- strong typographic consistency
- moderate, restrained color use
- good grayscale readability
- precise axis labeling
- balanced panel spacing
- careful legend control
- export-ready formatting

The skill should **not** interpret “Nature style” as permission for flashy or overly stylized graphics.

---

## Usage Discipline

This skill should default to the following division of labor:

### `Stata`

- raw-data cleaning
- merges
- sample construction
- variable generation
- econometric estimation
- exporting plot-ready figure data

### `R`

- importing plot-ready data
- light plotting reshaping
- visualization
- layout
- styling
- faceting
- caption support
- export

If the figure data are not yet plot-ready, the skill should normally recommend preparing them in `Stata` first.

---

## What This Skill Should Not Assume

This skill should **not** assume:

- TensorBoard
- benchmark comparison workflows
- ML ablation plots
- training curves by default
- raw-data cleaning in `R`
- decorative infographic design
- arbitrary color-heavy styling
- unexplained smoothing or transformations

Only move toward ML-style visualization if the user explicitly asks for that workflow.

---

## Main Text vs Appendix Guidance

The skill should help the user decide whether a figure belongs in the main text or appendix.

### Main text figures should usually:

- support identification
- summarize a main result
- show dynamic treatment effects
- communicate a central empirical pattern

### Appendix figures should usually:

- support robustness
- document supplementary checks
- provide extended diagnostics
- add transparency without crowding the main narrative

---

## Good Usage Signals

This skill is especially appropriate when the user says things like:

- “帮我画图”
- “帮我用 R 出图”
- “帮我把回归结果变成图”
- “帮我做 event study 图”
- “帮我做系数图”
- “帮我拼图”
- “帮我把图改成 Nature 风格”
- “帮我写图注”
- “帮我把 Stata 和 R 的 workflow 接起来”

---

## Working Rule

Use this skill when the user needs help transforming empirical results into figures that are:

- analytically clear
- aesthetically disciplined
- consistent with economics and agricultural economics paper norms
- produced in `R`
- ready for journal submission or serious manuscript drafting
