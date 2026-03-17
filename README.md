# Econ Scholar Workflow for Codex

Language: English | [中文](README.zh-CN.md)

An empirical-economics workflow layer for Codex, tuned for:

- empirical microeconomics
- policy evaluation
- `Stata + Python`
- paper drafting, submission QA, and `R&R` response work

This repository is not a standalone application. It is a workflow pack made of:

- routing rules in `AGENTS.md`
- agent prompts in `agents/`
- skills in `skills/`
- config examples in `config.example.toml`
- report templates in `quality_reports/`

## What This Workflow Assumes

By default, Codex should interpret your requests in an economics context:

- "results" means regression tables, not benchmark leaderboards
- "experiment" means empirical design, not model training
- "paper" means economics paper structure, not AI conference structure
- "review response" means journal `R&R`, not conference rebuttal

The default stack is:

- literature: `Google Scholar`, `RePEc`, `IDEAS`, `NBER`, `AEA journals`
- analysis: `Stata` first, `Python` for support tasks
- outputs: `literature-review.md`, `analysis-plan.md`, `regression-spec-matrix.md`, `response-letter.md`

## Quick Start

### 1. Treat This Repo As a Workflow Overlay

This repo is meant to be merged into your Codex setup, not run by itself.

Core files:

- `AGENTS.md`: project-level routing and workflow rules
- `config.example.toml`: example registrations for agents and MCP
- `agents/`: specialized agent prompts
- `skills/`: reusable workflow instructions

### 2. Configure Codex

Use `config.example.toml` as a reference for:

- enabling `multi_agent`
- enabling `memories`
- enabling `skill_approval`
- registering economics agents
- enabling Zotero MCP

Important:

- the checked-in `config.example.toml` contains template placeholders for model/provider setup
- merge the research workflow sections into your real `~/.codex/config.toml`
- do not copy placeholder values like `your-api-key`

### 3. Optional but Recommended: Zotero MCP

If you want literature-management and paper-import workflows, configure Zotero MCP.

See:

- `MCP_SETUP.md`
- `MCP_SETUP.zh-CN.md`

### 4. Start a Session in the Project Root

Open Codex in the project directory so it reads `AGENTS.md`.

Suggested first prompt:

```text
Read AGENTS.md and treat this repository as an empirical economics workflow. I am working on [topic]. Help me set up the workflow and start from the right stage.
```

## The Working Workflow

### Stage 1. Research Ideation

Use:

- `research-ideation`
- `literature-reviewer`

Outputs:

- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `research-design.md`

Best for:

- sharpening the question
- mapping identification strategies
- checking whether the literature is already saturated
- deciding whether the data are feasible

### Stage 2. Data Audit and Analysis Planning

Use:

- `results-analysis`
- `data-analyst`

Inputs:

- `.dta`
- `.do`
- `.log`
- `.csv`
- `.xlsx`
- regression `.tex` tables

Outputs:

- `analysis-plan.md`
- `regression-spec-matrix.md`
- `table-shells.md`
- `replication-checklist.md`

Best for:

- reconstructing do-file order
- documenting sample construction
- planning baseline regressions
- laying out robustness and appendix tables

### Stage 3. Paper Drafting

Use:

- `ml-paper-writing`
- `paper-miner`

Default structure:

1. `Introduction`
2. `Institutional background / context`
3. `Data`
4. `Empirical strategy / identification`
5. `Main results`
6. `Mechanisms / heterogeneity`
7. `Robustness`
8. `Conclusion`
9. `Appendix`

Economics template entrypoint:

- `skills/ml-paper-writing/templates/econ/README.md`

### Stage 4. Submission QA

Use:

- `paper-self-review` for a static audit
- `qa-paper` for a strict critic/fixer/verifier loop

`qa-paper` is the default when you need:

- a go / no-go decision
- a score
- multiple review-fix rounds
- hard-gate enforcement before advisor sharing or submission

### Stage 5. R&R and Response Letters

Use:

- `review-response`
- `rebuttal-writer`
- `qa-response` for final QA

Default outputs:

- `response-letter.md`
- `comment-to-change-map.md`

## Second-Round QA System

This repo includes a Codex-native port of the `critic/fixer` pattern.

### Agents

- `paper-critic`
- `paper-fixer`
- `response-critic`
- `response-fixer`
- `artifact-verifier`

### Skills

- `qa-paper`
- `qa-response`

### Loop

```text
pre-flight -> critic -> fixer -> verifier -> repeat if needed -> APPROVED or max 5 rounds
```

### Thresholds

- `80` = commit-ready
- `90` = submission-ready
- `95` = excellence

### Hard Gates

Paper:

- identification failure
- text/table mismatch
- unverifiable citations
- missing replication note

Response:

- missing key referee reply
- untraceable promised change
- response / change-map inconsistency
- materially evasive tone

Reports are written to:

- `quality_reports/papers/`
- `quality_reports/responses/`
- `quality_reports/verifier/`

## Practical Prompts

### Start a literature review

```text
I want to study [topic]. Use the empirical economics workflow. Start with literature mapping, identification strategies, and feasible data sources.
```

### Audit a Stata project

```text
I have a set of do-files and dta files. Reconstruct the data pipeline, identify the estimation sample, and produce a regression-spec matrix.
```

### Draft results text

```text
Use these regression results to draft the Main Results and Empirical Strategy sections in economics-journal style.
```

### Run strict paper QA

```text
Run qa-paper on this draft. I want hard gates, a score, and a clear submission-readiness verdict.
```

### Draft and QA an R&R response

```text
Use review-response to draft the letter, then run qa-response before finalizing it.
```

## Repository Layout

- `AGENTS.md`: project-level routing and quality rules
- `config.example.toml`: example Codex config additions
- `agents/`: specialized reviewer and worker prompts
- `skills/`: workflow instructions and references
- `quality_reports/`: QA outputs and report templates

## Current Scope

Covered well:

- empirical microeconomics
- policy evaluation
- `Stata + Python`
- paper and `R&R` QA loops

Not yet covered deeply:

- full replication-package audit
- dedicated critic/fixer for data cleaning
- theory-economics workflows


