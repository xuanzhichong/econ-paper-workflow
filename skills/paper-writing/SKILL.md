---
name: paper-writing
description: Use when the user needs to draft or revise an empirical economics paper, write sections such as Introduction, Data, Empirical Strategy, Main Results, Mechanisms, Robustness, or prepare journal-ready appendices, JEL codes, and data/code disclosure notes. Handles Chinese prompts such as "实证论文", "识别策略", "主结果", "附录表", and "投稿修改".
version: 1.1.0
---

# Empirical Economics Paper Writing

This is the default writing workflow for empirical economics papers.

## Default Paper Structure

Use this section order unless the user specifies a journal template:

1. `Introduction`
2. `Institutional background / context`
3. `Data`
4. `Empirical strategy / identification`
5. `Main results`
6. `Mechanisms / heterogeneity`
7. `Robustness`
8. `Conclusion`
9. `Appendix`

If the paper is short, combine sections carefully. Do not collapse identification into vague "methods" language.

## Writing Priorities

Always keep these aligned:

- research question
- source of identification
- sample construction
- coefficient interpretation
- table and appendix references

The default standard is economics-journal clarity, not conference-style hype.

## What to Draft

When the user gives enough context, proactively draft:

- contribution framing
- paragraph-level transitions
- Data and Empirical Strategy sections
- Main Results prose tied to specific tables
- appendix roadmap
- data and code availability statements

Flag uncertainty when it affects identification, sample definition, or interpretation. Do not block on small wording choices.

## Introduction Standard

The introduction should establish:

- what question the paper answers
- why it matters economically or for policy
- what variation identifies the effect
- how the paper relates to the literature
- what the headline findings are

Avoid ML-style framing such as benchmark leadership, ablation summaries, or model novelty claims unless the paper is actually about that.

## Data Section Standard

The Data section should make replication possible.

Include:

- source and access path
- unit of observation
- sample window
- sample restrictions
- matching or merge logic
- construction of treatment, outcomes, and controls
- summary statistics and missingness notes

## Empirical Strategy Standard

This section should make the identification argument explicit.

Include:

- estimating equation or design description
- key identifying assumption
- fixed effects and controls
- standard error choice and clustering level
- threats to validity
- key diagnostic or falsification exercises

If the identifying assumption is fragile, say so and connect robustness checks to that fragility.

## Results Standard

Write around tables, not around vague claims.

For each core result:

- state which table or figure carries the evidence
- interpret magnitudes economically
- distinguish levels, logs, elasticities, and percentages
- explain how the estimate changes across specifications
- separate main results from mechanisms and robustness

Do not overstate mechanism evidence or treat heterogeneous correlations as structural proof.

## Appendix and Disclosure

Default appendix content:

- extra tables
- variable definitions
- alternative samples
- placebo tests
- robustness variants
- additional institutional detail
- data appendix or replication appendix if needed

Also prepare:

- `JEL` codes if the user targets economics journals
- data and code availability text
- notes on confidential or restricted-access data
- the appropriate outline from `templates/econ/`

## Citation Rule

Never invent citations or BibTeX. Verify papers before citing, especially when discussing classic economics references or working-paper versions.

## References to Load On Demand

- `references/econ-paper-structure.md`
- `references/econ-writing-patterns.md`
- `references/journal-submission-notes.md`
- `references/data-code-disclosure.md`
- `references/citation-workflow.md`

Use the conference-template material only if the user explicitly targets a non-economics venue.
