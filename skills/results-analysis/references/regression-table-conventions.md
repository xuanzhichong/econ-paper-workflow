# Regression Table Conventions for Empirical Economics and Agricultural Economics

Tables should make the specification legible without forcing the reader into the code.

This note is for empirical economics and agricultural economics papers.  
A good regression table should let a careful reader understand the estimand, sample, specification progression, and inference choices without guessing.

---

## Baseline Table Design

- one conceptual result per table
- columns should reflect meaningful specification changes
- one dependent variable or one close specification family per column
- do not combine unrelated estimands in a single crowded table
- move from parsimonious to fuller specifications in a way that is economically interpretable
- if columns are directly compared, use a harmonized sample rule when possible, or disclose clearly when the sample changes

A strong baseline table usually lets the reader see:

1. the core coefficient of interest  
2. how it changes with controls, fixed effects, or sample restrictions  
3. whether the inference is stable across meaningful specifications

---

## What Table Notes Should State

Table notes should state, as applicable:

- sample
- unit of observation
- dependent variable definition
- treatment definition if not obvious
- controls
- fixed effects
- clustering level
- weighting
- standard error type
- significance notation
- sample exceptions or restricted samples
- omitted category or omitted period when relevant

The note should be complete enough for interpretation, but it should not replace key design explanation that belongs in the main text.

---

## Notes and Labels

- label treatment and outcomes with economic meaning, not raw variable names
- define transformations such as logs, winsorization, standardization, or index construction
- explain omitted categories in event-study tables
- clarify whether coefficients are levels, log points, percentage points, elasticities, or standardized-unit effects
- use labels that match the wording in the text and appendix

Preferred practice:

- `Employment Rate` rather than `emp_rate`
- `Broadband Rollout` rather than `treat_post`
- `Log Household Income` rather than `ln_income`

---

## Specification Progression

A readable table should make specification changes interpretable.

Common progression:

1. baseline estimate
2. + controls
3. + fixed effects or richer fixed effects
4. + restricted or harmonized sample
5. + alternative inference or design-sensitive adjustment

Do not add columns mechanically.  
Each new column should answer one clear question:

- does the estimate survive controls?
- does it survive fixed effects?
- does it survive sample restrictions?
- does it survive alternative inference choices?

---

## Sample Comparability

Common problem:

- different columns silently use different samples
- the text compares coefficients as if `N` were fixed
- the appendix and main text use different sample definitions without explanation

Preferred practice:

- report observations for every column
- disclose why `N` changes
- use a harmonized adjusted sample when directly comparing specifications, or say clearly that comparability is limited
- keep main-text and appendix sample definitions aligned when describing the same result

---

## IV Table Conventions

For IV designs, readability usually improves when the table structure distinguishes:

- reduced form
- first stage
- second stage

Preferred formats:

- separate panels within one table, or
- separate tables if the design is complex

Table notes should also disclose:

- instrument definition
- first-stage diagnostic if reported
- FE, controls, clustering, and sample
- whether the sample is identical across reduced form, first stage, and second stage

Do not bury the first-stage logic in the text while presenting only second-stage estimates in a way that obscures identification.

---

## Event-Study Table and Figure Conventions

When reporting event-study results:

- state the omitted period clearly
- explain the timing convention
- define treatment timing precisely
- keep coefficient labels interpretable
- make clear whether the table reports leads/lags, grouped bins, or cumulative effects

The reader should be able to tell:

- what period is normalized to zero
- which coefficients are pre-treatment
- which coefficients are post-treatment
- how inference is constructed

---

## Heterogeneity Table Conventions

When reporting heterogeneity:

- make clear whether the table shows subgroup regressions or interaction terms
- label groups with economic meaning
- keep subgroup definitions consistent with the text
- do not overload the table with too many ad hoc splits
- use notes to clarify the baseline group if interactions are used

Heterogeneity tables should be theory-motivated, not decorative.

---

## Output Integrity

Before trusting a table, verify that:

- table titles and notes are complete
- variable labels are consistent across tables and text
- coefficient units are clear
- FE, clustering, controls, weights, and sample rules are disclosed
- appendix tables do not silently change samples without explanation
- the prose matches the final exported table, not an earlier draft
- the main text does not describe a different specification than the one actually shown

---

## Common Failures

- main text references a different sample than the table uses
- coefficient units are unclear
- clustering level is omitted
- raw variable names appear in the table
- adjusted columns silently change `N`
- table notes hide key design choices that belong in the text
- first-stage and second-stage results are mixed in a confusing way
- event-study omitted period is not explained
- appendix tables use different labels or definitions from the main text

---

## Working Rule

A good regression table should answer three questions immediately:

1. what is being estimated?  
2. on what sample and under what specification?  
3. how should the coefficient be interpreted?

If the reader cannot answer those questions from the table and note, the table is not yet ready.
