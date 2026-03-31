# Common Pitfalls in Empirical Economics and Agricultural Economics Results Analysis

Use this as a failure checklist before trusting a regression table, event-study figure, mechanism section, or headline empirical claim.

This is a design-aware checklist for empirical economics and agricultural economics results analysis.  
It is not just a generic statistical-hygiene list.  
The goal is to check whether the reported results, interpretations, and supporting evidence actually match the identification strategy, sample construction, and empirical design.

---

## 1. Sample Drift Across Specifications

Problem:

- different columns silently use different samples
- text compares coefficients as if the sample were fixed
- adjusted specifications lose observations because of control-variable missingness without disclosure

Check:

- report observation counts for every column
- explain why the sample changes
- verify appendix and main text use the same sample definition when claiming comparability
- use a harmonized adjusted sample rule when directly comparing specifications, or state clearly why not

---

## 2. Clustering That Does Not Match the Design

Problem:

- clustering at the wrong level
- switching between `robust` and clustered SE without explanation
- inference choices do not match treatment variation or likely error correlation

Check:

- state the decision rule for clustering
- tie the clustering level to the treatment variation or error structure
- note if inference is fragile to alternative clustering choices
- verify that table notes disclose the clustering level consistently

---

## 3. Identification Claim Stronger Than the Design

Problem:

- wording implies causality when the design only supports association
- robustness checks do not address the actual threat
- conclusion language is stronger than what the identification strategy warrants

Check:

- identify the threat first
- map each robustness check to that threat
- trim language if the design does not support the strong claim
- make sure the abstract, introduction, results, and conclusion use aligned claim strength

---

## 4. Opaque Sample Construction

Problem:

- merges, exclusions, or missing-value rules are undocumented
- treatment or outcome construction is described only in code
- sample pipeline cannot be reconstructed from the text and appendix

Check:

- write the sample pipeline in plain language
- record merge keys and duplicate handling
- state missingness and winsorization rules
- clarify how the final estimation sample is obtained from the raw or intermediate data

---

## 5. Event Study Misread as Causal Proof

Problem:

- insignificant pre-trends treated as proof of validity
- normalization period or treatment timing not explained
- staggered timing issues ignored
- post-treatment coefficients interpreted without clarifying the comparison structure

Check:

- state omitted period and timing convention
- interpret pre-trends cautiously
- discuss power limits and composition issues when relevant
- clarify how treatment timing and comparison groups are constructed
- avoid treating visually flat pre-trends as conclusive proof of identification validity

---

## 6. Mechanism Section That Overruns the Evidence

Problem:

- mechanism regressions are presented as structural proof
- heterogeneity is written as if it reveals a mechanism automatically
- supporting evidence is narrated as if it were separately identified

Check:

- distinguish suggestive evidence from identified mechanism evidence
- keep mechanism claims narrower than the main effect claim
- state clearly when a mechanism result is only consistent with an interpretation rather than proving it

---

## 7. Heterogeneity Analysis Without Theory

Problem:

- many subgroup results are reported without clear theoretical motivation
- heterogeneity looks like data mining
- subgroup comparisons are interpreted too strongly

Check:

- justify subgroup definitions theoretically
- explain why the heterogeneity matters for interpretation
- avoid turning exploratory subgroup patterns into headline conclusions
- keep heterogeneity claims more cautious than baseline claims

---

## 8. Economic Magnitude Misinterpretation

Problem:

- coefficients are interpreted in the wrong units
- level effects, percentage-point effects, log-point effects, and elasticities are mixed up
- statistical significance is reported without economic significance
- a small but precise estimate is described as substantively large without justification

Check:

- state the unit of the coefficient clearly
- distinguish levels, logs, percentages, and elasticities
- explain economic magnitude in plain language
- make sure the text does not overstate the practical importance of small effects

---

## 9. Table Notes That Omit Critical Design Choices

Problem:

- no table-note disclosure for FE, clustering, weights, or sample restrictions
- readers cannot tell how the specification differs across columns
- special sample rules or treatment coding choices are hidden

Check:

- every table should document FE, clustering, controls, weights, and sample exceptions
- disclose special treatment definitions or restricted samples in the note
- make the table note sufficient for a careful reader to understand the design choices

---

## 10. Placebo and Robustness Without Purpose

Problem:

- many checks appear, but none are linked to an identification concern
- placebo and robustness sections become decorative rather than diagnostic
- the paper accumulates checks without clarifying what concern each one addresses

Check:

- each placebo or robustness exercise should answer one explicit challenge
- remove decorative robustness checks
- organize the robustness section by threat, not by arbitrary accumulation

---

## 11. Text-Table Inconsistency

Problem:

- coefficients, signs, units, or significance in prose do not match the table
- text refers to an earlier table version
- appendix and main text describe the same result differently

Check:

- verify every headline sentence against the final table export
- avoid drafting prose before the table shell is stable
- cross-check appendix, figure captions, and conclusion against the final estimates

---

## 12. Replication Path Missing

Problem:

- results are discussed without a clear do-file order, log files, or provenance
- readers cannot tell which script generates which table
- restricted-data steps are omitted or ambiguously described

Check:

- list the execution order
- note which file creates each main table and figure
- disclose restricted-data steps clearly
- make the provenance from code to output legible enough for internal audit or submission review

---

## Working Rule for Results Sections

A disciplined empirical results section should usually follow this logic:

1. baseline estimates
2. identification support or dynamic evidence
3. targeted robustness checks tied to specific threats
4. heterogeneity and mechanism as supporting evidence
5. appendix signposting for supplementary material

If the section instead reads like an accumulation of tables, checks, and claims without a design-driven organizing logic, treat that as a warning sign.
