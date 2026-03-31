---
name: paper-self-review
description: Use when the user asks for a structured pre-submission review of an empirical economics or agricultural economics paper, wants to check identification logic, regression tables, appendix consistency, citation integrity, data/code reproducibility, or asks for a systematic self-review before journal submission, advisor review, or R&R resubmission.
version: 0.4.0
---

# Paper Self-Review for Empirical Economics and Agricultural Economics

Use this skill as a structured quality gate before submission, advisor review, or R&R resubmission.

This skill is for disciplined self-review, not for a fully adversarial critic/fixer/verifier loop.

If the user asks for a strict audit, adversarial review, submission-readiness judgment, score-based decision, pass/fail gate, or explicitly wants a multi-round review/fix workflow, route to `../qa-paper/SKILL.md` instead of doing only a structured self-review.

## Scope

This skill is most appropriate for:

- empirical economics papers
- agricultural economics papers
- policy evaluation manuscripts
- household survey papers
- food, nutrition, public health, sustainability, labor, development, and related applied empirical work

Default orientation:

- design-aware
- economics-facing
- replication-conscious
- cautious about causal language
- suitable for manuscript and appendix self-audit

## Core Checklist

```text
Empirical Economics and Agricultural Economics Self-Review
- [ ] Research question and identification strategy match
- [ ] Treatment variation, comparison group, and interpretation are aligned
- [ ] Sample selection is traceable from raw data to estimation sample
- [ ] Treatment, outcome, and control variables are defined consistently
- [ ] Fixed effects and standard error choices are justified
- [ ] Adjusted specifications do not silently change the sample, or changes are disclosed clearly
- [ ] Main tables, appendix tables, and text use the same sample and variable definitions
- [ ] Mechanism and heterogeneity claims do not outrun the evidence
- [ ] Citations are verified and literature positioning is accurate
- [ ] Data/code/README are sufficient for replication, or restrictions are clearly disclosed
```

## What to Review

### 1. Identification Logic

Check whether:

- the paper states the identifying variation clearly
- the treatment, comparison group, timing, and source of variation are coherent
- threats to identification are acknowledged
- robustness checks actually target those threats
- the interpretation matches the design
- causal language is no stronger than the identification strategy can support

### 2. Data and Sample Transparency

Check whether:

- sample restrictions are explicit
- merge, append, reshape, attrition, and exclusion logic are documented
- descriptive statistics match the stated sample
- appendix notes explain unusual coding decisions
- missing-value rules are clear
- the estimation sample can be traced from raw or intermediate data to final tables

### 3. Regression and Table Integrity

Check whether:

- tables use consistent variable labels
- clustering and FE choices are stable and justified
- treatment variation and clustering level are aligned
- significance stars, notes, units, and sample descriptions are consistent
- no-controls and with-controls columns silently change the estimation sample
- text descriptions match the sign, magnitude, and precision reported in tables
- appendix tables use the same definitions stated in the main text

### 4. Writing Discipline

Check whether:

- the introduction promises only what the design can support
- the literature positioning matches what the paper actually contributes
- the results section interprets economic magnitudes correctly
- mechanism evidence is not overstated
- heterogeneity analysis is theory-motivated rather than ad hoc
- the conclusion does not overclaim beyond the evidence
- the appendix absorbs supporting material without hiding critical design details

### 5. Reproducibility

Check whether:

- do-files run in a documented order
- table and figure outputs can be traced back to scripts
- intermediate outputs are named consistently
- logs exist for major steps
- README explains dependencies, restricted data, and expected outputs
- replication limits are disclosed honestly when full replication is not possible

## Design-Specific Review Prompts

Use the prompts relevant to the paper’s design.

### DID / Event Study

Check whether:

- treatment timing is clearly defined
- the comparison group is explicit
- staggered adoption issues are recognized when relevant
- pre-trends are checked appropriately
- anticipation effects are considered
- event-study coefficients are interpreted cautiously

### IV

Check whether:

- the instrument is clearly defined
- first-stage relevance is shown
- exclusion restriction is defended
- first stage, reduced form, and second stage are distinguishable in text and tables
- IV claims do not exceed what the design can support

### RDD

Check whether:

- the running variable and cutoff are clear
- sharp vs fuzzy design is explicit
- bandwidth logic is discussed
- manipulation and continuity checks are reported when relevant
- local interpretation is stated appropriately

### Matching / PSM

Check whether:

- matching is treated as supportive rather than automatically causal
- balance is documented
- common support is discussed
- matched-sample claims are not overstated

### Control Function / Selection Correction

Check whether:

- the source of endogeneity or selection is clearly stated
- first-stage logic is documented
- correction terms are interpreted cautiously
- the corrected estimates are compared clearly with baseline results

## Citation and Literature Review Check

Check whether:

- citations used for core claims are verified
- working-paper and published versions are not mixed incorrectly
- policy and dataset citations rely on the right source type
- contribution claims match the actual literature
- literature review distinguishes direct evidence from indirect support

If citation fidelity becomes a major issue, use `../citation-verification/SKILL.md`.

## Review Output

Prefer a structured review with:

- `Major risks`
- `Moderate issues`
- `Quick fixes`
- `Evidence gaps`
- `Replication gaps`
- `Recommendation`

The recommendation should use one of the following:

- `Ready for advisor/internal review`
- `Needs targeted revision before advisor/internal review`
- `Not ready for submission`
- `Escalate to qa-paper`

If the paper is not ready, say exactly what blocks submission or serious internal circulation.

## Escalation Rule

Escalate to `qa-paper` when any of these are true:

- the user asks whether the draft is submission-ready
- the paper has multiple tables/appendices and consistency risk is material
- the user wants iterative critic/fixer review
- the task requires a score or pass/fail quality gate
- the user wants an adversarial audit rather than a structured self-review
