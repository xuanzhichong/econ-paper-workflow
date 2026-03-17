---
name: research-ideation
description: Use when the user asks to brainstorm economics research ideas, design an empirical strategy, plan a policy evaluation, map identification assumptions, assess data availability, or build a literature review for empirical microeconomics. Handles Chinese prompts such as "研究问题", "识别策略", "政策评估", "文献综述", and "数据来源".
version: 0.2.0
---

# Research Ideation for Empirical Economics

Use this skill for the front end of an empirical economics project. Default to `实证微观/政策评估`, not ML ideation.

## Core Workflow

```text
Question framing -> Literature map -> Identification strategy -> Data feasibility -> Research design
```

## What This Skill Should Produce

- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `research-design.md`
- `references.bib` when verified sources are available

## Step 1: Frame the Research Question

Turn vague ideas into a question that is empirically answerable.

Check these dimensions:

- what policy, institution, shock, or market mechanism matters
- who is treated, exposed, affected, or compared
- what outcome is economically meaningful
- why the question matters for policy, welfare, or market design
- what margin of variation could identify the effect

Good outputs are narrow and testable:

- treatment, outcome, comparison group
- unit of observation
- time horizon
- expected identifying variation

## Step 2: Build an Economics Literature Map

Default search sources:

- Google Scholar
- RePEc / IDEAS
- NBER Working Papers
- AEA journals
- field journals and leading working papers

Organize the review by:

- research question
- identification strategy
- data source
- main findings
- unresolved disagreements

Do not default to AI conference venues, arXiv-only surveys, or benchmark-style comparisons.

## Step 3: Draft the Identification Map

For each candidate design, make the identifying variation explicit.

Include:

- empirical design: RCT, DID, event study, IV, RDD, matching, panel FE, shift-share, synthetic control, or structural estimation
- assumptions required
- likely threats to identification
- minimum diagnostic tests
- alternative specifications if the main design is weak

The key question is not just "Is this interesting?" but "What variation makes the claim credible?"

## Step 4: Evaluate Data Feasibility

Before proposing analysis, assess the data pipeline.

Cover:

- source and access restrictions
- unit of observation
- sample coverage
- merge keys
- time dimension
- variable construction burden
- likely missingness and measurement error
- whether replication can be packaged cleanly

Prefer concrete datasets and administrative or survey sources over vague "we will collect data somehow" statements.

## Step 5: Produce a Research Design

The design should align the question, data, and identification logic.

Include:

- question and contribution
- core literature buckets
- preferred empirical strategy
- data source and sample plan
- baseline regression or design equation
- main threats and robustness priorities
- likely tables, figures, and appendices

## Zotero Integration

Use Zotero as the citation backbone when available.

- import verified papers by DOI, arXiv ID, or URL
- group collections by topic, design, or paper status
- avoid duplicates before adding sources
- use Zotero metadata for BibTeX export

Do not create fabricated citations or placeholder BibTeX from memory.

## Economics Defaults

- recent work matters, but always include seminal papers
- working papers can matter before journal publication
- policy relevance does not replace identification credibility
- novelty can come from new data, cleaner identification, new setting, or resolving conflicting evidence

## References to Load On Demand

- `references/econ-literature-sources.md`
- `references/identification-strategy-guide.md`
- `references/data-source-evaluation.md`
- `references/literature-search-strategies.md`
- `references/zotero-integration-guide.md`

Use the existing generic references only when they help. Prefer the economics-specific references first.
