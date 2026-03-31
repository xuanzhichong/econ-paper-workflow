# Paper Figures Usage

This skill now defaults to empirical economics and agricultural economics figure workflows built around a **Stata -> R** division of labor.

Use it when the goal is to turn **Stata-processed `.dta` files** into **publication-ready descriptive figures in R**, while keeping:

- `Stata` responsible for data cleaning, sample construction, variable generation, and exporting processed `.dta` files
- `R` responsible for importing the processed `.dta` files and producing journal-ready figures

This skill is primarily for:

- descriptive figures
- development trend figures
- structure or composition figures
- group comparison figures
- spatial descriptive figures
- multi-panel paper figures

It is **not** primarily for regression-result visualization such as coefficient plots or event-study plots, unless the user explicitly asks for those.

---

## Typical Use Cases

This skill is best suited for tasks such as:

- turning `Stata`-processed `.dta` files into publication-ready `R` figures
- drawing descriptive trend plots in `R`
- drawing development-path or evolution-over-time figures
- drawing regional, group, or category comparison figures
- drawing composition or structure-change figures
- drawing maps and spatial descriptive figures
- building multi-panel figures for the main text or appendix
- refining an existing `R` figure to better match **Nature / Nature-subjournal** style
- designing figure layouts, captions, and export rules for submission-ready papers

It is especially appropriate when the user wants figures that are:

- descriptive rather than regression-based
- clean
- readable
- publication-ready
- visually disciplined
- stylistically consistent across the paper

---

## Typical Prompts

### 中文场景

- 我已经用 `Stata` 处理好了数据并生成了 `.dta` 文件，请帮我写 `R` 画图代码
- 帮我根据这个 `.dta` 文件画一张描述性发展趋势图
- 帮我做一个分组对比图，展示不同地区的变化趋势
- 帮我画一个结构变化图，展示不同类别占比的变化
- 帮我把几张描述性图片拼成一张主文 multi-panel 图
- 帮我根据 `Stata` 导出的 `.dta` 文件做一张符合 `Nature` 风格的图片
- 帮我修改这张 `R` 图的字体、配色、坐标轴和排版
- 帮我写图注和 caption
- 帮我判断这张图应该放主文还是 appendix
- 帮我把 `Stata` 和 `R` 的画图工作流接起来

### English-style prompts

- Help me turn this Stata-processed `.dta` file into a publication-ready `R` figure
- Build a descriptive trend figure from this `.dta` file
- Create a multi-panel figure for the main paper using `R`
- Rewrite this plotting code so the figure matches a **Nature-style** standard
- Draft a caption and figure note for this descriptive empirical figure
- Help me decide whether this figure belongs in the main text or appendix

---

## Expected Inputs

Typical inputs may include:

- processed `.dta` files exported from `Stata`
- grouped or collapsed `.dta` files prepared for plotting
- `.xlsx` or `.csv` files only if the user already has figure-ready data in those formats
- descriptive summary tables
- figure sketches or screenshots
- existing `R` plotting code
- journal target or stated style preference
- instructions on whether the figure is for:
  - main text
  - appendix
  - slides
  - advisor circulation

Preferred input style:

- `Stata` prepares the processed `.dta`
- `R` imports the `.dta` and handles plotting, layout, and export

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
- import the `.dta` file directly in `R`
- include clear sectioning and comments
- use stable filenames and export paths

When the user asks for design guidance, the default should be:

- clarify the descriptive purpose of the figure
- recommend the right figure family
- explain how the figure supports the paper’s narrative

---

## Default Workflow Expectations

The skill should usually proceed as follows:

1. identify what the figure is supposed to show
2. confirm that the input is a processed `.dta` or other figure-ready file
3. determine whether the figure is descriptive, trend-based, structural, spatial, or multi-panel
4. inspect the structure of the input data
5. decide the appropriate figure family
6. map variables to visual elements
7. generate or revise the `R` code
8. recommend a journal-ready export format
9. provide caption or note language when useful

The skill should prioritize **analytical clarity** over decoration.

---

## Preferred Figure Families

Default figure families include:

- descriptive trend plots
- development-path figures
- group comparison plots
- composition or structure-change figures
- distribution or density figures
- maps and spatial descriptive figures
- sample flow or descriptive pipeline figures
- multi-panel figures

The skill should recommend the figure family that best matches the descriptive purpose, rather than defaulting to regression-result plots or generic bar charts.

---

## Nature-Style Default

When the user asks for figures that match **Nature** or **Nature-subjournal** style, the skill should default to:

- clean and minimal layout
- strong typographic consistency
- restrained, publication-safe color use
- good grayscale readability
- precise axis labeling
- balanced panel spacing
- careful legend control
- export-ready formatting

The skill should **not** interpret “Nature style” as permission for flashy or overly stylized graphics.

The intended standard is:

- elegant but restrained
- polished but not decorative
- visually modern but analytically disciplined

---

## Usage Discipline

This skill should default to the following division of labor:

### `Stata`

- raw-data cleaning
- merges
- sample construction
- variable generation
- aggregation, collapsing, or reshaping for analysis
- exporting processed `.dta` files for plotting

### `R`

- importing processed `.dta`
- light reshaping for plotting
- ordering labels and factors
- visualization
- layout
- styling
- faceting
- caption support
- export

If the figure data are not yet plotting-ready, the skill should normally recommend preparing them in `Stata` first.

---

## What This Skill Should Not Assume

This skill should **not** assume:

- coefficient plots as the default
- event-study plots as the default
- regression-result visualization as the main workflow
- TensorBoard
- benchmark comparison workflows
- ML ablation plots
- training curves by default
- raw-data cleaning in `R`
- decorative infographic design
- arbitrary color-heavy styling
- unexplained smoothing or transformations

Only move toward regression-result visualization if the user explicitly asks for it.

---

## Main Text vs Appendix Guidance

The skill should help the user decide whether a figure belongs in the main text or appendix.

### Main text figures should usually:

- show a central descriptive pattern
- clarify the empirical context
- present key development trends
- communicate a main structural or comparative pattern
- support the narrative of the paper clearly and efficiently

### Appendix figures should usually:

- provide supplementary descriptive detail
- show alternative descriptive cuts of the same pattern
- add transparency without crowding the main narrative
- include additional supporting figures that are useful but not central

---

## Good Usage Signals

This skill is especially appropriate when the user says things like:

- “帮我画图”
- “帮我用 R 出图”
- “我已经用 Stata 处理好了数据并生成了 dta 文件”
- “帮我根据这个 dta 文件画一张描述性图”
- “帮我画发展趋势图”
- “帮我画分组对比图”
- “帮我画结构变化图”
- “帮我拼图”
- “帮我把图改成 Nature 风格”
- “帮我写图注”
- “帮我把 Stata 和 R 的 workflow 接起来”

---

## Working Rule

Use this skill when the user needs help transforming **Stata-processed `.dta` files** into figures that are:

- descriptive rather than primarily regression-visualization-based
- analytically clear
- aesthetically disciplined
- consistent with economics and agricultural economics paper norms
- produced in `R`
- ready for journal submission or serious manuscript drafting
