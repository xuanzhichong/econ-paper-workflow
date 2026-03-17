# Statistical Methods for Empirical Economics

This file is a design-to-diagnostic map, not a generic statistics catalog.

## Baseline Regression Designs

### Cross-Section

Document:

- unit of observation
- control set logic
- heteroskedasticity treatment
- whether weights are design-based or descriptive

### Panel Fixed Effects

Document:

- panel identifiers
- FE structure
- treatment timing
- clustering level
- attrition or sample rotation issues

### Difference-in-Differences

Document:

- treatment definition
- comparison group
- timing variation
- estimator type
- pre-trend and composition concerns

### Event Study

Document:

- omitted period
- leads/lags window
- staggered-treatment estimator choice if relevant
- support and composition by relative time

### IV

Document:

- first-stage logic
- exclusion restriction argument
- relevance evidence
- monotonicity or complier interpretation when applicable

### RDD

Document:

- running variable
- cutoff
- bandwidth rule
- polynomial or local-linear choice
- manipulation and covariate continuity checks

## Default Inference Checks

- standard errors match the error structure
- small-cluster concerns are acknowledged when relevant
- weighted estimates explain what is being weighted
- multiple testing is discussed if a family of outcomes is central

## Default Reporting Discipline

- coefficient units are explicit
- effect sizes are translated into economic magnitudes
- confidence intervals or standard errors are reported consistently
- observation counts and cluster counts are visible when needed

## When Not To Use Generic Defaults

Do not force:

- `t-test -> ANOVA -> effect size`
- ML-style repeated-seed summaries
- benchmark-style model ranking

Use checks that follow from the empirical design instead.
