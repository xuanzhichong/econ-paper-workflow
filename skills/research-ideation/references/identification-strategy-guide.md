# Identification Strategy Guide

The objective is to make the source of credible variation explicit before designing regressions.

## Common Designs

### RCT

- treatment assignment is randomized
- check compliance, attrition, spillovers, and treatment timing

### DID / Event Study

- define treated and comparison groups
- justify timing
- inspect pre-trends and anticipation
- state omitted event-time period

### IV

- define instrument relevance
- defend exclusion
- state the affected margin and likely LATE interpretation

### RDD

- define running variable and cutoff
- justify bandwidth and polynomial choices
- inspect manipulation and balance near the cutoff

### Matching / Reweighting

- state overlap assumptions
- show balance diagnostics
- clarify whether matching is preprocessing or main identification

## Minimum Output

For every candidate design, write:

- identifying variation
- key assumption
- most likely threat
- first diagnostic or falsification exercise
- backup design if the preferred one fails
