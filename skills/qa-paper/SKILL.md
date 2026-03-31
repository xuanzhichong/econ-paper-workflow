---
name: qa-paper
description: Use when the user wants a strict, adversarial QA loop for an empirical economics or agricultural economics paper draft, a submission-readiness decision, score-based quality gates, or iterative critic/fixer review before advisor sharing, journal submission, or R&R resubmission.
version: 0.2.0
---

# QA Paper

Run a repo-native critic/fixer/verifier loop for empirical economics and agricultural economics manuscripts.

This skill is for strict, adversarial quality control.  
Use it when the user wants more than a structured self-review and explicitly needs a quality gate, submission-readiness judgment, or multi-round revision loop.

## When To Use

Use this skill when the user wants:

- a harsh pre-submission review
- a go / no-go decision
- a numeric score
- multiple review-fix rounds
- hard-gate enforcement for identification, tables, citations, and replication
- an adversarial manuscript audit before advisor sharing, submission, or R&R resubmission

Use `../paper-self-review/SKILL.md` instead when the user wants a structured but non-adversarial self-review rather than a formal QA loop.

## Core Loop

```text
Pre-flight
    ->
paper-critic round 1
    ->
paper-fixer round 1
    ->
artifact-verifier
    ->
repeat if needed
    ->
stop at APPROVED or STOPPED-NOT-APPROVED
```

Maximum default loop length:

- 5 rounds

## Agent Roles

- `paper-critic` identifies substantive problems, hard-gate failures, and provisional scores
- `paper-fixer` implements conservative revisions against the critic report
- `artifact-verifier` is the final gatekeeper and decides whether the paper is approved, should continue, or must stop without approval

Do not collapse these roles into one generic review step.

## Pre-flight

Before the loop starts, identify:

- manuscript source files
- tables / figures / appendices referenced in the draft
- replication materials or README
- whether citations can be checked from available artifacts
- whether the available materials are sufficient for strict adversarial QA

If the draft is too incomplete for adversarial QA, say so and produce a scoped pre-flight note instead of pretending the loop ran cleanly.

## Hard Gates

The artifact cannot be approved while any of these remain unresolved:

- identification logic error
- text / table mismatch on a headline result
- unverifiable or distorted citation
- missing replication note for a claim that depends on code / data workflow
- undisclosed inconsistency in sample, variable definition, or specification that materially affects interpretation

When citation fidelity is materially at issue, use:

- `../citation-verification/SKILL.md`

## Design-Aware QA Rule

QA must follow the empirical design rather than applying a generic checklist.

Match the review logic to the design when relevant, including:

- DID / event study
- IV
- RDD
- matching / PSM
- control function
- panel FE / clustered SE settings

Do not review identification as if every paper had the same threats or diagnostics.

## Scoring Rubric

Score each category from `0-100`:

- identification
- econometrics
- data transparency
- literature accuracy
- writing clarity
- appendix / replication readiness

Thresholds:

- `80` = commit-ready
- `90` = submission-ready
- `95` = excellence

## Report Locations

- critic reports: `quality_reports/papers/*_critic_roundN.md`
- fixer reports: `quality_reports/papers/*_fixer_roundN.md`
- verifier reports: `quality_reports/verifier/*_paper_verifier_roundN.md`

Use the templates in `quality_reports/templates/` when creating a new report.

## Expected Round Logic

1. `paper-critic` produces:
   - issue list
   - hard-gate findings
   - provisional scores
2. `paper-fixer` addresses issues conservatively and reports what changed, what remains blocked, and what requires further evidence
3. `artifact-verifier` decides:
   - `APPROVED`
   - `CONTINUE`
   - `STOPPED-NOT-APPROVED`

If the verifier returns `CONTINUE`, run another critic/fixer round focused on unresolved items rather than reopening the entire paper from scratch.

If 5 rounds are completed without approval, stop the loop and report the remaining blockers clearly.

## Final Output

Always provide:

- current verdict
- overall score
- hard-gate status
- top remaining blockers
- whether the draft is `below-threshold`, `commit-ready`, `submission-ready`, or `excellence`
- next-round target, if the paper is not approved

## Output Discipline

When the paper is not ready:

- say exactly what blocks approval
- distinguish hard-gate failures from moderate weaknesses
- do not pretend the paper is close to submission if core identification, citation, or replication issues remain

When the paper is approved:

- confirm that hard gates pass
- confirm that no critical unresolved issue remains
- report the final readiness level clearly
