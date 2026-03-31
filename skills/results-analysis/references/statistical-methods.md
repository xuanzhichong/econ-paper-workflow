# Statistical Methods and Design Diagnostics for Empirical Economics and Agricultural Economics

This file is a design-to-diagnostic map, not a generic statistics catalog.

Use it to align empirical design, identification threats, inference choices, and reporting discipline in empirical economics and agricultural economics papers.

---

## Core Principle

Statistical methods in empirical economics should follow from the empirical design, not from a generic menu of techniques.

The goal is not to ask:

- what methods are available?
- what tests look sophisticated?

The goal is to ask:

- what variation identifies the effect?
- what threats weaken that design?
- what diagnostics address those threats?
- what level of claim strength does the design support?

A good methods section and results section should therefore connect:

1. design  
2. identifying assumptions  
3. threats  
4. diagnostics  
5. reporting discipline  

---

## Baseline Regression Designs

### Cross-Section

Document:

- unit of observation
- control set logic
- heteroskedasticity treatment
- whether weights are design-based or descriptive
- why the design supports only association or a stronger claim
- major omitted-variable or selection concerns

Typical concerns:

- omitted variables
- selection on observables versus unobservables
- whether weighting changes the estimand or only improves descriptiveness

---

### Panel Fixed Effects

Document:

- panel identifiers
- FE structure
- treatment timing
- clustering level
- attrition or sample rotation issues
- whether identification comes from within-unit variation
- whether enough within-unit variation exists for the key regressor

Typical concerns:

- attrition changing the estimating sample
- treatment variation being mostly cross-sectional rather than within-unit
- unit trends or evolving composition

---

### Difference-in-Differences

Document:

- treatment definition
- comparison group
- timing variation
- estimator type
- pre-trend and composition concerns
- whether staggered adoption or heterogeneous treatment effects matter
- what identifying assumption is being maintained

Typical concerns:

- differential trends
- selective treatment timing
- composition changes after treatment
- controls that may absorb or distort treatment variation

---

### Event Study

Document:

- omitted period
- leads/lags window
- staggered-treatment estimator choice if relevant
- support and composition by relative time
- how relative-time coefficients are grouped or binned
- how comparison groups are defined over time

Typical concerns:

- visually flat pre-trends being overstated as proof
- weak support in distant leads/lags
- changing treated/control composition by event time
- dynamic estimates being interpreted more strongly than the design supports

---

### IV

Document:

- first-stage logic
- exclusion restriction argument
- relevance evidence
- monotonicity or complier interpretation when applicable
- reduced form / first stage / second stage distinction
- whether the sample is the same across stages

Typical concerns:

- weak first stage
- exclusion restriction being asserted rather than defended
- second-stage interpretation being broader than the local IV estimand allows

---

### RDD

Document:

- running variable
- cutoff
- bandwidth rule
- polynomial or local-linear choice
- manipulation and covariate continuity checks
- whether the design is sharp or fuzzy
- local interpretation and external-validity limits

Typical concerns:

- manipulation around the cutoff
- sensitivity to bandwidth choice
- overfitting with higher-order polynomials
- local treatment effects being interpreted too broadly

---

## Default Inference Checks

Check whether:

- standard errors match the error structure
- clustering level matches the treatment variation or likely correlation structure
- multi-way clustering is considered when relevant
- small-cluster concerns are acknowledged when relevant
- weighted estimates explain what is being weighted
- multiple testing is discussed if a family of outcomes is central
- inference changes materially under alternative reasonable clustering choices

Inference should be treated as design-dependent, not purely mechanical.

---

## Default Reporting Discipline

Check whether:

- coefficient units are explicit
- effect sizes are translated into economic magnitudes
- confidence intervals or standard errors are reported consistently
- observation counts and cluster counts are visible when needed
- sample definition is consistent across tables and text
- FE, clustering, weights, and sample exceptions are disclosed in notes
- robustness checks are linked to specific threats
- mechanism and heterogeneity claims are weaker than or equal to the main design can support

A well-reported estimate should tell the reader:

1. what is being estimated  
2. on what sample  
3. under what specification  
4. with what inference rule  
5. with what substantive meaning  

---

## Design-to-Diagnostic Logic

A useful working rule is:

- first identify the threat
- then choose the diagnostic
- then report what the diagnostic does and does not rule out

Examples:

- concern: selective treatment timing  
  -> diagnostic: pre-trends, alternative timing definitions, sample restrictions

- concern: instrument weakness  
  -> diagnostic: first-stage evidence, reduced form, weak-IV discussion

- concern: local nonlinearity near cutoff  
  -> diagnostic: bandwidth sensitivity, local-linear alternatives, continuity checks

Diagnostics are meaningful only when tied to a specific design concern.

---

## When Not To Use Generic Defaults

Do not force:

- `t-test -> ANOVA -> effect size`
- ML-style repeated-seed summaries
- benchmark-style model ranking
- generic checklists that ignore the design
- robustness sections that accumulate regressions without identifying a threat

Use checks that follow from the empirical design instead.

---

## Final Rule

A methods-and-results workflow is well aligned only if the design, diagnostics, inference, and interpretation all point to the same estimand and the same level of credibility.

If the method is sophisticated but the identifying variation is unclear, the empirical design is still weak.
