---
name: results-analysis
description: Use when the user asks to analyze empirical economics results, inspect Stata outputs, design regressions, build robustness checks, interpret regression tables, or connect `.dta`, `.do`, `.log`, `.tex`, `.csv`, or `.xlsx` files to paper writing. Handles Chinese prompts such as "主回归", "稳健性", "异质性", "机制分析", and "回归表".
version: 0.2.0
---

# Results Analysis for Empirical Economics

Use this skill for empirical analysis after the research design is in place. Default to `Stata-first` workflows and economics paper outputs.

## Default Inputs

- `.dta`
- `.csv`
- `.xlsx`
- `.do`
- Stata `.log`
- regression table `.tex`
- codebook or variable notes

Do not default to TensorBoard, training curves, or benchmark leaderboards.

## Core Workflow

```text
Raw data audit -> Cleaning and merge -> Sample construction -> Variable definitions -> Main regression -> Robustness -> Heterogeneity/mechanisms -> Table and figure export -> Replication check
```

## Required Outputs

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`

Generate additional notes only when they clarify identification or replication.

## Step 1: Audit the Data Pipeline

Before discussing results, establish:

- where the raw data come from
- what each file contributes
- whether merges are one-to-one, many-to-one, or risk duplicate inflation
- how the estimation sample is formed
- what gets dropped and why

Flag missing documentation early. A weak sample construction story usually becomes a weak paper.

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

If the project uses `Stata`, prefer a clear do-file order and note which steps are destructive versus reversible.

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

This prevents drifting specifications and makes appendices easier to manage.

## Step 4: Evaluate Main Identification Choices

Default checks should be economics-specific:

- `robust` or clustered SE choices
- fixed effects structure
- IV first stage and exclusion concerns
- DID timing and pre-trends
- event study normalization and omitted period
- RD bandwidth and polynomial choices
- matching or reweighting diagnostics

Do not impose `pre-test -> ANOVA -> effect size` as a universal template. Use the design-appropriate checks instead.

## Step 5: Plan Robustness, Heterogeneity, and Mechanisms

Typical robustness layers:

- alternative samples
- alternative variable definitions
- alternative clustering levels
- placebo outcomes or placebo treatments
- alternative bandwidths, bins, or windows
- differential trends checks
- sensitivity to outliers or winsorization

Keep the purpose of each check explicit. Avoid robustness for its own sake.

## Step 6: Translate Results into Tables and Paper Prose

The paper-facing output should center on:

- what the coefficient means economically
- what identifying variation supports the claim
- how much the estimate moves across specifications
- which appendices absorb detail versus core text

Preferred table families:

- summary statistics
- balance table
- baseline results
- mechanism or heterogeneity tables
- robustness appendix tables

## Regression Table Conventions

Default to economics-journal table layout:

- one dependent variable or one specification family per column
- use `Yes/No` bottom rows for `Controls`, `FE`, `Clustered SE`, and weights when relevant
- do not silently change adjusted samples across columns; harmonize the adjusted sample rule and disclose it
- if controls are used, disclose the baseline control-coefficient specification in the main text or appendix

For `IV` tables, prefer one of these structures:

- `Panel A: Reduced form`, `Panel B: First stage`, `Panel C: Second stage`
- or separate tables for reduced form, first stage, and second stage

Avoid hybrid layouts that stack multiple stages and multiple outcomes into one hard-to-read row block.

## Replication Standard

Always leave a reproducible trail:

- ordered do-files
- logs for major steps
- explicit paths or path placeholders
- README for execution order
- table and figure provenance

If the current project is not reproducible, say so directly and list what is missing.

## References to Load On Demand

- `references/stata-workflow.md`
- `references/empirical-checklist.md`
- `references/regression-table-conventions.md`
- `references/robustness-patterns.md`
- `references/results-writing-guide.md`

Use the generic statistics references only when the design truly needs them.
