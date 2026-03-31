# Stata Workflow for Empirical Economics and Agricultural Economics

Default to a staged workflow instead of one giant do-file.

This workflow is designed for empirical economics and agricultural economics projects, especially those involving data cleaning, sample construction, causal inference, robustness analysis, and manuscript-ready table output.

A good Stata workflow should make it easy to answer:

1. where the data came from  
2. how the estimation sample was built  
3. how variables were constructed  
4. which script produced each main table and figure  
5. whether the results are reproducible and auditable  

---

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

### Role of Each Stage

**`00_setup.do`**
- define globals or project paths
- set Stata version and reproducibility options
- check required packages
- open project-wide settings

**`01_import_raw.do`**
- import raw files from original sources
- standardize file formats and encodings if needed
- save untouched imported copies to intermediate storage rather than modifying raw files

**`02_clean.do`**
- clean source datasets separately
- standardize IDs, dates, variable formats, labels, and obvious coding errors
- document cleaning rules clearly

**`03_merge_build_sample.do`**
- merge or append cleaned datasets
- preserve merge diagnostics
- define the initial analytical sample
- document exclusions and duplicate handling

**`04_construct_variables.do`**
- construct treatment, outcomes, controls, weights, and subgroup variables
- apply winsorization, trimming, standardization, or index construction rules
- save a clear analysis-ready dataset

**`05_main_results.do`**
- estimate baseline specifications
- export core manuscript tables
- log the final estimation sample and specification settings

**`06_robustness.do`**
- run robustness checks tied to specific identification threats
- avoid turning this file into an unstructured dump of regressions

**`07_heterogeneity_mechanisms.do`**
- run theory-motivated heterogeneity and mechanism analyses
- keep subgroup and mechanism definitions aligned with the paper text

**`08_export_tables_figures.do`**
- export manuscript-ready tables and figure inputs
- ensure filenames match the manuscript structure
- keep a stable mapping from output files to table/figure numbers in the paper

---

## Good Practices

- open a log for each major stage
- use stable output filenames
- separate raw, intermediate, and analysis data
- preserve merge diagnostics
- store table exports with names that match the manuscript
- never overwrite raw data
- use analysis datasets that can be regenerated from earlier stages
- keep sample construction traceable across stages
- make sure adjusted specifications do not silently change the sample without disclosure
- keep exported tables and figures linked clearly to the scripts that produced them
- use filenames and folder structure that remain readable under version control

---

## What to Document

Document the following clearly:

- required packages such as `reghdfe`, `ivreg2`, `estout`
- path assumptions
- randomization or simulation seeds if applicable
- restricted-data instructions when code cannot be run end-to-end by others
- merge keys and duplicate handling
- sample restrictions and exclusion rules
- variable construction rules
- missing-data treatment
- winsorization, trimming, or standardization rules
- the exact script that produces each main table and figure
- any reason why main-text and appendix specifications use different samples or definitions

---

## Output Discipline

A good workflow should produce outputs that are easy to audit.

Recommended discipline:

- main tables should come from clearly named export scripts
- appendix tables should not rely on hidden alternative definitions without disclosure
- logs should correspond to major execution stages
- output filenames should match manuscript table and figure references as closely as possible
- intermediate outputs should not be overwritten silently if they matter for later audit

Example naming style:

- `table2_main_results.tex`
- `table3_robustness.tex`
- `tableA2_alt_sample.tex`
- `figure2_event_study_data.dta`

---

## Common Failures

Common workflow failures include:

- one giant do-file with no clear stages
- raw data being overwritten
- merge diagnostics not preserved
- sample restrictions applied without documentation
- variable construction logic existing only in code comments or memory
- main results and appendix results using different definitions without explanation
- exported tables not matching the manuscript numbering
- no clear record of which script created which output
- logs missing for key stages
- restricted-data limitations not disclosed

---

## Working Rule

A strong Stata workflow should make the empirical pipeline legible without forcing a future reader to reverse-engineer the entire project.

If a coauthor, advisor, referee, or future you cannot quickly tell:

- how the sample was built
- how the main variables were constructed
- which file generated Table 2
- whether Appendix Table A3 uses the same sample as the main text

then the workflow is not yet ready.
