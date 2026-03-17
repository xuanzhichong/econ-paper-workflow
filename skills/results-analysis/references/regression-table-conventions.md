# Regression Table Conventions

Tables should make the specification legible without forcing the reader into the code.

## Baseline Table Design

- one conceptual result per table
- columns should reflect meaningful specification changes
- table notes should state:
  - sample
  - unit of observation
  - FE
  - clustering level
  - weighting
  - significance notation

## Notes and Labels

- label treatment and outcomes with economic meaning, not raw variable names
- define transformations such as logs, winsorization, standardization, or index construction
- explain omitted categories in event-study tables

## Common Failures

- main text references a different sample than the table uses
- coefficient units are unclear
- clustering level is omitted
- table notes hide key design choices that belong in the text
