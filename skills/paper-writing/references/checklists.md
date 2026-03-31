# Economics and Agricultural Economics Paper Checklist

Use this checklist before advisor circulation, submission, or `R&R` resubmission.

This is a practical checklist for empirical economics and agricultural economics papers.  
Its purpose is to catch problems in identification, sample construction, table discipline, writing, and replication before they turn into referee concerns.

---

## Claims and Identification

- [ ] abstract claims match the design
- [ ] introduction does not promise more than the paper can identify
- [ ] identifying variation is stated in plain language
- [ ] threats to identification are acknowledged
- [ ] claim strength matches design strength across abstract, introduction, results, and conclusion
- [ ] robustness checks are linked to specific identification threats
- [ ] event-study / IV / RDD interpretation is no stronger than the design supports

---

## Data and Sample

- [ ] unit of observation is explicit
- [ ] sample window and restrictions are listed
- [ ] merges and constructed variables are documented
- [ ] missingness, winsorization, or trimming rules are disclosed
- [ ] final estimation sample can be reconstructed from the documented pipeline
- [ ] adjusted specifications do not silently change the sample, or changes are disclosed clearly
- [ ] treatment, outcome, and control construction are documented in plain language

---

## Tables and Results

- [ ] every headline claim points to a table or figure
- [ ] column notes specify FE, clustering, controls, and weights
- [ ] text matches sign, magnitude, and precision in the final tables
- [ ] appendix tables are cross-referenced consistently
- [ ] coefficient units and economic magnitudes are clear
- [ ] omitted period, normalization, or baseline group is disclosed where relevant
- [ ] main-text and appendix tables use consistent labels and sample definitions unless differences are explained

---

## Writing Discipline

- [ ] contribution is positioned against the right literature
- [ ] mechanism claims are not stronger than the evidence
- [ ] heterogeneity analysis is theory-motivated rather than decorative
- [ ] external validity discussion is proportionate
- [ ] conclusion distinguishes evidence from policy extrapolation
- [ ] robustness results are not written as entirely new headline findings
- [ ] appendix supports the paper without replacing core design explanation

---

## Replication and Disclosure

- [ ] do-file order is documented
- [ ] README explains dependencies and outputs
- [ ] restricted data or non-shareable code is disclosed honestly
- [ ] data and code availability statement is present
- [ ] main tables and figures can be traced to exact scripts
- [ ] raw, intermediate, and analysis data layers are distinguishable
- [ ] key package requirements are documented

---

## Revision Readiness

- [ ] referee-sensitive weaknesses are already visible in the text
- [ ] appendix absorbs supportive material without hiding core design details
- [ ] response map can point to every major revision location
- [ ] manuscript revision locations are easy to cite in a response letter
- [ ] key limitations are acknowledged in the manuscript rather than left only for the response letter
- [ ] the current draft is internally consistent enough for critic/fixer or final QA review

---

## Working Rule

The paper is much closer to submission-ready when a careful reader can answer the following quickly:

1. what is identified?  
2. on what sample?  
3. under what specification?  
4. how strong is the evidence?  
5. where is each key result shown?  
6. how would someone reproduce the main tables and figures?  

If those questions are still hard to answer, the paper is not yet ready.
