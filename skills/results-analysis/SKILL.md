---
name: results-analysis
description: Use when the user asks to analyze empirical economics or agricultural economics results, inspect Stata outputs, design regressions, build robustness checks, interpret regression tables, or connect `.dta`, `.do`, `.log`, `.tex`, `.csv`, or `.xlsx` files to paper writing. Handles Chinese prompts such as "主回归", "稳健性", "异质性", "机制分析", and "回归表".
version: 0.3.0
---

# Results Analysis for Empirical Economics and Agricultural Economics

Use this skill for empirical analysis after the research design is in place.  
Default to `Stata-first` workflows and economics-journal paper outputs.

This skill is for results analysis, specification control, robustness planning, regression-table interpretation, and replication-aware output organization.

It is **not** the default skill for:

- front-end project formation or topic design -> use `research-ideation`
- full manuscript drafting -> use `paper-writing`
- strict adversarial critic/fixer/verifier review -> use `qa-paper`

---

## Default Inputs

- `.dta`
- `.csv`
- `.xlsx`
- `.xls`
- `.do`
- Stata `.log`
- regression table `.tex`
- codebook or variable notes

Do not default to TensorBoard, training curves, benchmark leaderboards, or repeated-seed ML result summaries.

---

## Core Workflow

```text
Raw data audit
    ->
Cleaning and merge review
    ->
Sample construction
    ->
Variable definitions
    ->
Main regression
    ->
Identification check
    ->
Robustness
    ->
Heterogeneity / mechanisms
    ->
Table and figure export
    ->
Paper-facing interpretation
    ->
Replication check
```

---

## Required Outputs

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`
- `results-notes.md` when paper-facing interpretation is needed

Generate additional notes only when they clarify identification, sample construction, interpretation, or replication.

---

## Step 1: Audit the Data Pipeline

Before discussing results, establish:

- where the raw data come from
- what each file contributes
- whether merges are one-to-one, many-to-one, or risk duplicate inflation
- how the estimation sample is formed
- what gets dropped and why
- whether the main-text and appendix results rely on the same sample definition

Flag missing documentation early.  
A weak sample construction story usually becomes a weak paper.

---

## Step 2: Specify Cleaning and Variable Construction

Write the data logic in plain language before touching the regression story.

Cover:

- key identifiers and time variables
- treatment construction
- outcome construction
- winsorization or trimming
- missing-value rules
- deflation, normalization, or aggregation
- panel balance assumptions where relevant
- whether adjusted specifications silently change the sample
- whether a harmonized adjusted sample rule is needed

If the project uses `Stata`, prefer a clear do-file order and note which steps are destructive versus reversible.

---

## Step 3: Build the Regression Specification Matrix

For each table, define:

- dependent variable
- treatment or key regressor
- controls
- fixed effects
- sample restrictions
- standard error clustering level
- weighting scheme
- source do-file or output table

This prevents drifting specifications, helps control sample comparability, and makes appendices easier to manage.

---

## Step 4: Evaluate Main Identification Choices

Diagnostics must follow the empirical design, not a generic statistics checklist.

Default checks should be economics-specific:

- `robust` or clustered SE choices
- fixed effects structure
- IV first stage and exclusion concerns
- DID timing and pre-trends
- event study normalization and omitted period
- RD bandwidth and polynomial choices
- matching or reweighting diagnostics
- whether the interpretation is stronger than the design supports

Do not impose `pre-test -> ANOVA -> effect size` as a universal template.  
Use the design-appropriate checks instead.

---

## Step 5: Plan Robustness, Heterogeneity, and Mechanisms

Typical robustness layers:

- alternative samples
- alternative variable definitions
- alternative clustering levels
- placebo outcomes or placebo treatments
- alternative bandwidths, bins, or windows
- differential trends checks
- sensitivity to outliers or winsorization

Keep the purpose of each check explicit.  
Avoid robustness for its own sake.

Heterogeneity and mechanism analyses should be theory-motivated and interpreted more cautiously than the main effect.

---

## Step 6: Translate Results into Tables and Paper Prose

The paper-facing output should center on:

- what the coefficient means economically
- what identifying variation supports the claim
- how much the estimate moves across specifications
- whether changes reflect specification differences or sample drift
- which appendices absorb detail versus core text

Preferred table families:

- summary statistics
- balance table
- baseline results
- mechanism or heterogeneity tables
- robustness appendix tables

When writing results notes, keep these distinctions clear:

- baseline finding vs supporting evidence
- main result vs mechanism
- main result vs robustness
- statistically precise result vs economically meaningful result

Do not turn robustness into a second main-results section.  
Do not present mechanism evidence as structural proof unless separately identified.

---

## Regression Table Conventions

Default to economics-journal table layout:

- one dependent variable or one specification family per column
- use `Yes/No` bottom rows for `Controls`, `FE`, `Clustered SE`, and weights when relevant
- do not silently change adjusted samples across columns; harmonize the adjusted sample rule and disclose it
- if controls are used, disclose the baseline control-coefficient specification in the main text or appendix
- table notes should state sample, unit of observation, FE, clustering, weights, and any sample exceptions

For `IV` tables, prefer one of these structures:

- `Panel A: Reduced form`, `Panel B: First stage`, `Panel C: Second stage`
- or separate tables for reduced form, first stage, and second stage

Avoid hybrid layouts that stack multiple stages and multiple outcomes into one hard-to-read row block.

---

## Visualization and Output Discipline

Figures should support identification and interpretation, not decorate the paper.

Prioritize:

- event-study plots
- coefficient plots
- RD plots
- descriptive trend plots
- sample flow diagrams when attrition is material

Always ensure:

- axis labels include units
- omitted period or normalization is labeled
- captions state sample, estimator, and interval type when relevant
- figure construction choices such as bandwidth, bins, or smoothing are transparent

---

## Replication Standard

Always leave a reproducible trail:

- ordered do-files
- logs for major steps
- explicit paths or path placeholders
- README for execution order
- table and figure provenance
- clear mapping from manuscript tables to scripts and outputs

If the current project is not reproducible, say so directly and list what is missing.

---

## References to Load On Demand

- `references/stata-workflow.md`
- `references/empirical-checklist.md`
- `references/regression-table-conventions.md`
- `references/robustness-patterns.md`
- `references/results-writing-guide.md`
- `references/statistical-methods.md`
- `references/visualization-best-practices.md`
- `references/common-pitfalls.md`

Use generic statistics references only when the design truly needs them.
