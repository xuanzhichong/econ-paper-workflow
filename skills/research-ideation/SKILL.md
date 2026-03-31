---
name: research-ideation
description: Use when the user asks to brainstorm empirical economics or agricultural economics research ideas, design an empirical strategy, plan a policy evaluation, map identification assumptions, assess data availability, or build a literature review for empirical microeconomics. Handles Chinese prompts such as "研究问题", "识别策略", "政策评估", "文献综述", and "数据来源".
version: 0.3.0
---

# Research Ideation for Empirical Economics and Agricultural Economics

Use this skill for the front end of an empirical economics or agricultural economics project.

Default to `实证微观 / 政策评估`, not ML ideation.

This skill is for project formation, identification planning, data-feasibility assessment, and literature mapping.  
It is not the default skill for full manuscript drafting or adversarial QA.

- use `paper-writing` for manuscript drafting
- use `qa-paper` for strict critic/fixer/verifier review
- use `citation-verification` when literature or policy-source verification becomes central

## Core Workflow

```text
Question framing
    ->
Literature map
    ->
Identification strategy
    ->
Data feasibility
    ->
Research design
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

- treatment
- outcome
- comparison group
- unit of observation
- time horizon
- expected identifying variation

A strong ideation output should narrow a broad topic into one estimand, one treatment margin, one outcome family, and one feasible comparison structure.

## Step 2: Build an Economics Literature Map

Default search sources:

- Google Scholar
- RePEc / IDEAS
- National Bureau of Economic Research Working Papers
- top economics journals
- leading agricultural economics and field journals
- strong working papers when relevant

Organize the review by:

- research question
- identification strategy
- data source
- main findings
- unresolved disagreements
- direct evidence vs indirect support

Do not default to AI conference venues, arXiv-only surveys, or benchmark-style comparisons.

The literature map should clarify:

- what the literature already establishes
- what remains unresolved
- which papers provide direct evidence
- which papers are mainly background or methodological precedent

## Step 3: Draft the Identification Map

For each candidate design, make the identifying variation explicit.

Include:

- empirical design: RCT, DID, event study, IV, RDD, matching, panel FE, shift-share, synthetic control, or structural estimation
- assumptions required
- likely threats to identification
- minimum diagnostic tests
- alternative specifications if the main design is weak
- what claim strength would be justified if the design succeeds

The key question is not just `Is this interesting?` but `What variation makes the claim credible?`

Each proposed diagnostic or robustness exercise should map to a specific identification threat.

## Step 4: Evaluate Data Feasibility

Before proposing analysis, assess the data pipeline.

Cover:

- source and access restrictions
- unit of observation
- sample coverage
- merge keys
- time dimension
- treatment timing or exposure measurement
- variable construction burden
- likely missingness and measurement error
- whether replication can be packaged cleanly

Also ask:

- can the treatment or policy timing be measured credibly?
- can the comparison group be observed consistently?
- can the design-supporting panel or repeated cross section actually be built?
- are the key mechanisms observable or only indirectly inferable?

Prefer concrete datasets and administrative or survey sources over vague `we will collect data somehow` statements.

## Step 5: Produce a Research Design

The design should align the question, data, and identification logic.

Include:

- question and contribution
- core literature buckets
- preferred empirical strategy
- fallback empirical strategy if the preferred design is weak
- data source and sample plan
- baseline regression or design equation
- main threats and robustness priorities
- likely tables, figures, and appendices
- realistic claim strength given the available variation and data

A strong research design should make clear not only what the ideal design is, but also what can still be learned if the main design turns out to be weaker than expected.

## Zotero Integration

Use Zotero as the citation backbone when available.

- import verified papers by DOI, arXiv ID, or URL
- group collections by topic, design, or paper status
- avoid duplicates before adding sources
- use Zotero metadata for BibTeX export

Do not create fabricated citations or placeholder BibTeX from memory.

## Economics and Agricultural Economics Defaults

- recent work matters, but always include seminal papers
- working papers can matter before journal publication
- policy relevance does not replace identification credibility
- novelty can come from new data, cleaner identification, new setting, or resolving conflicting evidence
- agricultural, food, nutrition, sustainability, and rural-development questions should still be framed through credible empirical variation rather than topic importance alone

## References to Load On Demand

- `references/econ-literature-sources.md`
- `references/identification-strategy-guide.md`
- `references/data-source-evaluation.md`
- `references/literature-search-strategies.md`
- `references/zotero-integration-guide.md`
- `examples/example-literature-review.md`
- `examples/example-research-proposal.md`

Use existing generic references only when they help. Prefer the economics-specific references first.
