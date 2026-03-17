# Stata Workflow

Default to a staged workflow instead of one giant do-file.

## Recommended Order

1. `00_setup.do`
2. `01_import_raw.do`
3. `02_clean.do`
4. `03_merge_build_sample.do`
5. `04_construct_variables.do`
6. `05_main_results.do`
7. `06_robustness.do`
8. `07_heterogeneity_mechanisms.do`
9. `08_export_tables_figures.do`

## Good Practices

- open a log for each major stage
- use stable output filenames
- separate raw, intermediate, and analysis data
- preserve merge diagnostics
- store table exports with names that match the manuscript

## What to Document

- required packages such as `reghdfe`, `ivreg2`, `estout`
- path assumptions
- randomization or simulation seeds if applicable
- restricted-data instructions when code cannot be run end-to-end by others
