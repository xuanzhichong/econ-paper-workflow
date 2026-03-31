# Example Research Proposal: Broadband Rollout and Labor Market Adjustment

## Research Question

How does broadband expansion affect labor market adjustment in smaller municipalities, and through which margins does the adjustment occur?

More specifically, does broadband rollout improve employment outcomes by easing job search, supporting remote work, encouraging firm creation, reducing frictions in local matching, or changing migration and commuting behavior?

## Why It Matters

Broadband policy is often justified as a tool for local development, especially in smaller or lagging municipalities where market access and labor market thickness may be limited.

However, the relevant adjustment margin is often unclear. Observed gains in employment or local economic activity may reflect improved matching efficiency, new firm formation, outward commuting, migration responses, or broader compositional change rather than a single direct employment channel.

This makes broadband rollout an important setting for studying how digital infrastructure affects local labor market adjustment, especially outside large urban labor markets.

## Working Hypothesis

Broadband expansion is likely to improve labor market adjustment in smaller municipalities, but the effect may operate through multiple margins rather than through a single immediate increase in local employment.

Short-run effects may appear in job search efficiency, vacancies, or labor force participation, while medium-run effects may emerge through firm entry, reallocation, migration, or remote-work opportunities.

## Identification Sketch

### Primary design

- staggered rollout of broadband infrastructure across municipalities
- municipality and year fixed effects
- event-study specification around rollout timing

### Treatment definition

- treatment is municipality-level broadband rollout or meaningful expansion in access
- untreated or not-yet-treated municipalities serve as the comparison group

### Core identification idea

The design uses differences in rollout timing across municipalities to compare labor market outcomes before and after rollout, relative to municipalities that have not yet experienced rollout in the same period.

## Main Risks to Identification

- rollout may target municipalities already on different growth paths
- treatment timing may correlate with local political capacity, fiscal capacity, or administrative readiness
- infrastructure placement may be related to geographic feasibility in ways that also predict labor market outcomes
- nearby treated municipalities may generate spillovers through commuting, migration, or firm relocation

## Planned Responses

- pre-trend analysis
- event-study coefficients to inspect dynamic effects
- controls for pre-period municipal trends where defensible
- robustness to alternative rollout definitions
- placebo timing exercises
- controls for geographic rollout feasibility where available
- sensitivity checks excluding municipalities with unusually early or policy-prioritized rollout

## Data Plan

Potential data inputs include:

- broadband infrastructure rollout records
- labor market or social security microdata
- municipality finance and demographic controls
- geographic covariates for rollout feasibility

### Likely empirical structure

- unit of analysis: municipality-year, with linked worker- or firm-level outcomes if available
- sample: municipalities observed before and after rollout over a multi-year panel
- key requirement: credible timing data for broadband rollout matched to local labor market outcomes

### Data feasibility questions

- can rollout timing be measured consistently across municipalities?
- can labor market outcomes be observed at sufficiently fine geographic resolution?
- can worker, firm, and municipality data be linked reliably?
- are there enough pre-treatment years to assess pre-trends?

## Main Outcomes and Mechanisms

### Main outcomes

- employment rate
- unemployment or non-employment measures
- wage or earnings outcomes
- job finding or transition rates
- firm entry or establishment creation
- migration or commuting adjustments when available

### Mechanism margins

- job search efficiency
- remote work or digital job access
- local firm creation
- labor reallocation across sectors or places
- migration and commuting responses

## Expected Contribution

Relative to the existing literature on digital infrastructure, place-based policy, and local labor markets, this project is likely to contribute in three ways:

1. it studies broadband rollout in smaller municipalities, where labor market adjustment may differ from large urban settings;
2. it distinguishes immediate employment responses from medium-run reallocation margins;
3. it clarifies whether broadband improves local labor market performance through matching, firm dynamics, or spatial adjustment channels.

## Planned Outputs

- `literature-review.md`
- `identification-map.md`
- `data-source-plan.md`
- `research-design.md`

## Feasibility Note

The project is most promising if rollout timing is observed credibly, enough pre-treatment years are available, and labor market outcomes can be linked to municipalities consistently.

The main empirical risk is that rollout timing is not sufficiently exogenous. If that concern remains strong, the project may need to shift toward a narrower design, stronger institutional justification, or a feasibility-based comparison strategy rather than relying only on staggered timing.
