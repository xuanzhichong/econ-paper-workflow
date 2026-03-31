# Results Analysis Usage

This skill now defaults to empirical economics and agricultural economics workflows.

Use it for post-design empirical analysis, regression interpretation, robustness planning, table organization, and paper-facing results translation.

It is best suited for:

- `Stata-first` empirical workflows
- regression-table interpretation
- robustness / heterogeneity / mechanism planning
- linking `.dta`, `.do`, `.log`, `.tex`, `.csv`, `.xls`, or `.xlsx` artifacts to paper writing
- replication-aware organization of results

It is **not** the default skill for:

- front-end project design or idea generation → use `research-ideation`
- full manuscript drafting → use `paper-writing`
- strict adversarial review loops → use `qa-paper`

---

## Typical Prompts

- 帮我根据这套 `Stata do-file` 设计主回归和稳健性
- 我有 `.dta` 和一张回归表，帮我整理成 Results section
- 看看这个 DID 设计还需要哪些 pre-trend 和 placebo 检查
- 帮我做一个 `regression-spec-matrix.md`
- 帮我检查这几列回归是否存在 sample drift
- 帮我把异质性和机制分析整理成附录与正文的结构
- 根据 `.log` 和 `.tex` 输出，帮我解释主结果的经济意义
- 帮我规划主回归、稳健性、异质性、机制和 appendix tables 的关系
- 检查这套回归表的 FE、clustering、sample note 是否披露完整
- 帮我把现有结果整理成 `results-notes.md`

---

## Expected Inputs

- `.dta`
- `.do`
- `.log`
- regression table `.tex`
- `.csv`
- `.xlsx`
- `.xls`
- data dictionaries or variable notes
- appendix table drafts or note files when available

---

## Expected Outputs

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`
- `results-notes.md` when paper-facing interpretation is needed

Additional outputs should only be generated when they clarify:

- identification
- sample construction
- interpretation
- replication
- appendix organization

---

## Usage Discipline

The skill should default to:

- design-aware empirical analysis
- economics-journal regression conventions
- `Stata-first` workflow logic
- cautious interpretation of coefficients
- robustness checks tied to specific identification threats
- clear mapping from outputs to paper tables and figures

The skill should **not** assume:

- TensorBoard
- benchmark comparison
- ablation studies
- repeated-seed ML summaries
- `t-test -> ANOVA -> effect size` as a default pipeline

Only use ML-style experiment logic if the user explicitly asks for an ML workflow.
