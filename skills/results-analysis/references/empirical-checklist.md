# Empirical Economics Results Checklist

Use this list when reviewing an empirical results pipeline in economics or agricultural economics.

This is a short, design-aware checklist for checking whether the empirical pipeline, specifications, diagnostics, and reported outputs are consistent enough to support paper writing and results interpretation.

## Data Pipeline

- raw sources identified
- merge / append / reshape logic documented
- sample restrictions explicit
- missing-data rules stated
- treatment, outcome, and control construction traceable
- final estimation sample can be reconstructed from the documented pipeline

## Specification

- main equation or design defined
- treatment variation clearly stated
- FE stated
- controls justified
- clustering level justified
- weights disclosed if used
- treatment variation matches FE / clustering structure
- adjusted specifications do not silently change the sample, or changes are disclosed clearly

## Diagnostics

Diagnostics should match the empirical design, not follow a generic checklist.

- pre-trends where needed
- placebo checks where relevant
- first stage strength if IV
- bandwidth or window sensitivity if applicable
- manipulation or continuity checks if applicable
- balance or overlap checks if applicable

## Output Integrity

- table titles and notes are complete
- variable labels are consistent across tables and text
- text matches table signs, magnitudes, units, and significance
- FE, clustering, weights, and sample exceptions are disclosed in notes
- appendix tables do not silently change samples without explanation

## Claim Discipline

- claim strength matches design strength
- robustness checks are linked to specific identification threats
- mechanism evidence is presented as supportive rather than definitive unless separately identified
- heterogeneity analysis is theory-motivated and not overstated
