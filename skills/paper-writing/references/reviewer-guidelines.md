# Economics and Agricultural Economics Referee Lenses

Think like a careful journal referee.

Use these lenses when reading an empirical economics or agricultural economics paper for internal review, pre-submission checking, revision planning, or response-letter preparation.

The goal is not just to spot flaws in isolation.  
It is to identify the kinds of concerns that a serious referee is most likely to raise.

---

## Lens 1: Identification

Ask:

- what variation identifies the claim?
- are the assumptions visible before the result is interpreted?
- do robustness checks target the right threat?
- is the claim stronger than the design supports?
- are identification limits acknowledged honestly?

Common referee concerns under this lens:

- the identifying variation is not stated clearly
- the paper interprets suggestive evidence too strongly
- robustness checks do not address the main threat
- event-study / IV / RDD evidence is narrated too confidently
- mechanism or heterogeneity results are treated as if they were separately identified

A referee reading through this lens is asking:

- what exactly is identified here?
- why should I believe that?
- what would most likely invalidate the claim?

---

## Lens 2: Econometrics

Ask:

- are FE, clustering, weights, and sample restrictions justified?
- are columns comparable?
- are diagnostics appropriate for the design?
- do adjusted specifications silently change the sample?
- are coefficient units and estimands clear?

Common referee concerns under this lens:

- clustering does not match treatment variation or error structure
- columns are compared even though the sample changes silently
- diagnostics are generic rather than design-matched
- specifications are not organized clearly enough to show what changes and why
- table notes omit key econometric choices

A referee reading through this lens is asking:

- is the empirical implementation as careful as the design claim?
- are the estimates legible and comparable?
- is the inference rule appropriate?

---

## Lens 3: Literature Positioning

Ask:

- is the paper compared to the right literature?
- does it distinguish classic papers, recent work, and related but non-comparable designs?
- are contribution claims calibrated?
- does it distinguish direct evidence from indirect support?
- does it overstate novelty or understate prior work?

Common referee concerns under this lens:

- the contribution claim is too broad
- related work is cited but not actually engaged
- literature categories are blurred together
- papers with very different designs or settings are treated as directly comparable
- classic references are missing or recent relevant work is ignored

A referee reading through this lens is asking:

- does the paper know where it sits in the literature?
- is the claimed contribution believable?
- is the framing precise rather than promotional?

---

## Lens 4: Writing and Tables

Ask:

- can the reader map text to table evidence quickly?
- are table notes complete?
- does the prose overclaim mechanism or policy relevance?
- is the structure driven by identification logic rather than accumulation of material?
- are headline claims traceable to specific tables or figures?

Common referee concerns under this lens:

- prose and tables do not align
- table notes omit FE, clustering, weights, or sample exceptions
- results are presented in an order that obscures the main empirical logic
- mechanism, robustness, or heterogeneity sections overrun the baseline result
- policy discussion extrapolates beyond the evidence

A referee reading through this lens is asking:

- is this paper easy to evaluate?
- do the tables make the empirical design legible?
- is the writing disciplined enough for the evidence?

---

## Lens 5: Replication

Ask:

- can an RA reconstruct the pipeline from README, do-files, and appendix notes?
- are restricted-data constraints disclosed rather than hidden?
- can the reader tell which script produced which main table?
- are sample construction and variable definitions recoverable from the documentation?
- does the appendix support replication rather than merely accumulate extra output?

Common referee concerns under this lens:

- do-file order is unclear
- main tables cannot be traced to scripts
- sample construction lives only in code or memory
- restricted-data limitations are not stated clearly
- appendix lacks the information needed to understand the final estimation sample

A referee reading through this lens is asking:

- if I had to audit this paper seriously, could I reconstruct the empirical pipeline?
- is non-reproducibility being disclosed honestly?
- are the paper and appendix transparent enough for a journal-standard submission?

---

## How to Use the Lenses

Use these lenses in sequence or in parallel.

A practical order is:

1. Identification
2. Econometrics
3. Literature Positioning
4. Writing and Tables
5. Replication

This order works well because many later concerns are easier to diagnose once the design logic is clear.

---

## Typical Referee Failure Signals

Warning signs that often trigger major referee comments:

- the paper’s claim is stronger than its design
- the sample changes across columns without explanation
- a key result appears only in prose and is hard to verify in tables
- robustness checks are numerous but poorly targeted
- literature review uses “gap” language without showing what the literature already knows
- appendix is large but still does not clarify sample construction or variable definitions
- the paper is polished rhetorically but opaque empirically

---

## Working Rule

A strong referee-style reading asks not only:

- “Is there a problem?”

but also:

- “What kind of referee comment is this paper most vulnerable to?”

If you can identify the likely comment type in advance, you can usually improve the manuscript before submission.
