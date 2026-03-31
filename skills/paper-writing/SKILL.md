---
name: paper-writing
description: Use when the user needs to draft or revise an empirical economics or agricultural economics paper, write sections such as Introduction, Data, Empirical Strategy, Main Results, Mechanisms, Robustness, or prepare journal-ready appendices, JEL codes, and data/code disclosure notes. Handles Chinese prompts such as "实证论文", "识别策略", "主结果", "附录表", and "投稿修改".
version: 1.2.0
---

# Empirical Economics and Agricultural Economics Paper Writing

This is the default writing workflow for empirical economics and agricultural economics papers.

Use this skill for manuscript drafting and revision.  
If the user asks for a strict adversarial audit, submission-readiness gate, score-based verdict, or multi-round critic/fixer review, route to `../qa-paper/SKILL.md` instead.  
If the main task is citation checking, route to `../citation-verification/SKILL.md`.

## Default Paper Structure

Use this section order unless the user specifies a journal template or the paper logic clearly requires a different arrangement:

1. `Introduction`
2. `Institutional background / context`
3. `Data`
4. `Empirical strategy / identification`
5. `Main results`
6. `Mechanisms / heterogeneity`
7. `Robustness`
8. `Conclusion`
9. `Appendix`

If the paper is short, combine sections carefully.  
Do not collapse identification into vague `methods` language.

Keep the structure flexible when journal style or paper logic requires combining or reordering background and data sections.

The default template path is:

- `templates/econ/`

## Writing Priorities

Always keep these aligned:

- research question
- source of identification
- sample construction
- coefficient interpretation
- claim strength relative to design
- consistency across text, tables, appendix, and notes
- table and appendix references

The default standard is economics-journal clarity, not conference-style hype.

## What to Draft

When the user gives enough context, proactively draft:

- contribution framing
- paragraph-level transitions
- Data and Empirical Strategy sections
- Main Results prose tied to specific tables
- mechanism and heterogeneity framing
- robustness roadmap
- appendix roadmap
- data and code availability statements
- JEL code block if relevant

Flag uncertainty when it affects identification, sample definition, interpretation, or citation fidelity.  
Do not block on small wording choices.

## Introduction Standard

The introduction should establish:

- what question the paper answers
- why it matters economically or for policy
- what the existing literature already knows
- what remains unresolved or weakly identified
- what variation identifies the effect
- how the paper relates to the literature
- what the headline findings are
- what the paper contributes
- how the rest of the paper is organized

Avoid ML-style framing such as benchmark leadership, ablation summaries, or model novelty claims unless the paper is actually about that.

## Institutional Background / Context Standard

This section should:

- describe the relevant policy, market, or institutional setting
- explain timing, eligibility, assignment, or rollout rules
- show how the setting creates useful empirical variation
- provide only the background needed for the design
- separate institutional facts from interpretation

Do not overload this section with background that does not matter for identification or interpretation.

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
- important measurement limits or coding choices

## Empirical Strategy Standard

This section should make the identification argument explicit.

Include:

- estimating equation or design description
- treatment, outcome, and estimating sample
- source of identifying variation
- key identifying assumption
- controls, fixed effects, and weights if relevant
- standard error choice and clustering level
- threats to validity
- key diagnostic or falsification exercises

If the identifying assumption is fragile, say so and connect robustness checks to that fragility.

## Design-Specific Writing Prompts

Use the prompts relevant to the paper’s design.

### DID / Event Study

Emphasize:

- treatment timing
- comparison group
- staggered adoption issues when relevant
- pre-trends and dynamic effects
- anticipation concerns
- cautious interpretation of post-treatment effects

### IV

Emphasize:

- instrument definition
- relevance and first stage
- exclusion-restriction logic
- reduced form / first stage / second stage distinction
- what the IV estimate does and does not identify

### RDD

Emphasize:

- running variable and cutoff
- sharp vs fuzzy design
- local nature of identification
- bandwidth and continuity logic
- manipulation concerns when relevant

### Matching / PSM

Emphasize:

- why matching is used
- balance and common support
- limitations of selection-on-observables logic
- cautious interpretation of matched estimates

### Control Function / Selection Correction

Emphasize:

- source of endogeneity or selection
- first-stage logic
- correction term role
- relationship between baseline and corrected estimates
- cautious interpretation of the corrected results

## Results Standard

Write around tables, not around vague claims.

For each core result:

- state which table or figure carries the evidence
- interpret magnitudes economically
- distinguish levels, logs, elasticities, and percentages
- explain how the estimate changes across specifications
- distinguish headline findings from supporting checks
- separate main results from mechanisms and robustness

Do not overstate mechanism evidence or treat heterogeneous correlations as structural proof.  
Do not let robustness become a second main-results section.

## Table Layout Standard

Default to economics-journal table design:

- one dependent variable or one specification family per column
- `Controls`, `FE`, and clustering disclosed with `Yes/No` rows
- `IV` results shown as `Panel A/B/C` or across separate reduced-form / first-stage / second-stage tables
- adjusted columns should use a harmonized sample rule rather than silently changing `N`
- if adjusted controls are substantively discussed, include a separate control-coefficient table in the main text or appendix

## Appendix and Disclosure

Default appendix content:

- extra tables
- variable definitions
- alternative samples
- placebo tests
- robustness variants
- additional institutional detail
- additional figures or diagnostics
- data appendix or replication appendix if needed

Also prepare:

- `JEL` codes if the user targets economics journals
- data and code availability text
- notes on confidential or restricted-access data
- the appropriate outline from `templates/econ/`

Move supporting detail to the appendix, but do not hide indispensable identification logic or core sample definitions there.

## Citation Rule

Never invent citations or BibTeX.

Verify papers before citing, especially when discussing classic economics references, agricultural economics references, or working-paper versus published-paper versions.

When citation fidelity matters, use:

- `../citation-verification/SKILL.md`

## References to Load On Demand

- `references/knowledge/structure.md`
- `references/econ-writing-patterns.md`
- `references/journal-submission-notes.md`
- `references/data-code-disclosure.md`
- `references/citation-workflow.md`

Use conference-template material only if the user explicitly targets a non-economics venue.
