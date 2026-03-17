# Common Pitfalls in Empirical Economics Results Analysis

Use this as a failure checklist before trusting a regression table.

## 1. Sample Drift Across Specifications

Problem:

- different columns silently use different samples
- text compares coefficients as if the sample were fixed

Check:

- report observation counts for every column
- explain why the sample changes
- verify appendix and main text use the same sample definition when claiming comparability

## 2. Clustering That Does Not Match the Design

Problem:

- clustering at the wrong level
- switching between `robust` and clustered SE without explanation

Check:

- state the decision rule for clustering
- tie the clustering level to the treatment variation or error structure
- note if inference is fragile to alternative clustering choices

## 3. Identification Claim Stronger Than the Design

Problem:

- wording implies causality when the design only supports association
- robustness checks do not address the actual threat

Check:

- identify the threat first
- map each robustness check to that threat
- trim language if the design does not support the strong claim

## 4. Opaque Sample Construction

Problem:

- merges, exclusions, or missing-value rules are undocumented
- treatment or outcome construction is described only in code

Check:

- write the sample pipeline in plain language
- record merge keys and duplicate handling
- state missingness and winsorization rules

## 5. Event Study Misread as Causal Proof

Problem:

- insignificant pre-trends treated as proof of validity
- normalization period or treatment timing not explained

Check:

- state omitted period and timing convention
- interpret pre-trends cautiously
- discuss power limits and composition issues when relevant

## 6. Mechanism Section That Overruns the Evidence

Problem:

- mechanism regressions are presented as structural proof
- heterogeneity is written as if it reveals a mechanism automatically

Check:

- distinguish suggestive evidence from identified mechanism evidence
- keep mechanism claims narrower than the main effect claim

## 7. Table Notes That Omit Critical Design Choices

Problem:

- no table-note disclosure for FE, clustering, weights, or sample restrictions

Check:

- every table should document FE, clustering, controls, weights, and sample exceptions

## 8. Placebo and Robustness Without Purpose

Problem:

- many checks appear, but none are linked to an identification concern

Check:

- each placebo or robustness exercise should answer one explicit challenge
- remove decorative robustness checks

## 9. Text-Table Inconsistency

Problem:

- coefficients, signs, units, or significance in prose do not match the table

Check:

- verify every headline sentence against the final table export
- avoid drafting prose before the table shell is stable

## 10. Replication Path Missing

Problem:

- results are discussed without a clear do-file order, log files, or provenance

Check:

- list the execution order
- note which file creates each main table
- disclose restricted-data steps clearly
