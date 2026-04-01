# Review Classification for Empirical Economics and Agricultural Economics

Classify reviewer comments by the research concern they raise.

The purpose of classification is not just labeling.  
It is to decide:

- what the reviewer is really asking about
- what response stance is appropriate
- whether the manuscript must change
- what kind of manuscript change is needed
- whether the issue requires new analysis, new exposition, narrower claims, or only clarification

A reviewer comment may have:

- one **primary category**
- one optional **secondary category**

Use the primary category to decide the main response strategy.  
Use the secondary category when the comment combines multiple concerns.

---

## Primary Categories

- `identification`
- `robustness`
- `mechanism`
- `external-validity`
- `data-construction`
- `sample-construction`
- `exposition`
- `literature-positioning`
- `causal-language`
- `minor-edit`

---

## What Each Category Usually Implies

### identification

Typical concern:

- the empirical design may not support the claimed interpretation
- the identifying assumption is unclear, weakly defended, or insufficiently tested

Usually implies:

- revisit assumptions
- add diagnostics or falsification tests
- clarify identifying variation
- narrow language if the design supports less than currently claimed
- possibly add event-study, placebo, first-stage, or design-defense material

### robustness

Typical concern:

- the baseline result may depend too much on one coding rule, one sample, one inference choice, or one specification

Usually implies:

- add alternative samples, variable definitions, clustering, or windows
- add targeted sensitivity analysis
- connect each check to a specific threat
- avoid decorative robustness additions

### mechanism

Typical concern:

- the proposed channel is unclear, weakly supported, or overstated

Usually implies:

- add supporting evidence
- clarify that the mechanism is suggestive if not separately identified
- weaken causal interpretation if the mechanism evidence is only supportive
- distinguish mechanism evidence from the main effect clearly

### external-validity

Typical concern:

- the result may not generalize across settings, groups, periods, or policy environments

Usually implies:

- clarify scope conditions
- explain where the result is likely to travel and where it may not
- add subgroup or contextual discussion when appropriate
- avoid broad generalization beyond the setting actually studied

### data-construction

Typical concern:

- variable definitions, coding rules, merge logic, or treatment construction are unclear

Usually implies:

- document variable coding more clearly
- explain merge logic, duplicate handling, and transformations
- clarify treatment, outcome, or control construction
- add appendix notes, codebook language, or variable-definition material

### sample-construction

Typical concern:

- the estimation sample is unclear, changes silently, or is difficult to reconstruct

Usually implies:

- document sample restrictions and exclusions
- explain attrition, merge losses, and missing-data rules
- clarify the final estimation sample
- align main-text and appendix sample definitions
- add flow description or appendix sample note if needed

### exposition

Typical concern:

- the paper is difficult to follow even if the underlying design or result may be valid

Usually implies:

- rewrite the manuscript, not just the letter
- improve signposting
- clarify logic, sequence, and transitions
- make table / appendix references easier to follow

### literature-positioning

Typical concern:

- the paper overstates novelty, omits key references, or misstates what the literature already shows

Usually implies:

- revise framing
- add missing citations
- distinguish direct evidence from indirect support
- narrow novelty or contribution claims
- clarify how the paper relates to the existing literature

### causal-language

Typical concern:

- the wording is stronger than the empirical design can support

Usually implies:

- trim causal language
- align abstract, introduction, results, and conclusion
- distinguish association, suggestive evidence, and stronger causal interpretation
- avoid letting robustness or mechanism results upgrade the main claim artificially

### minor-edit

Typical concern:

- local wording, formatting, notation, references, or presentation issues that do not change the paper’s substance

Usually implies:

- small manuscript edits
- improved wording or organization
- citation cleanup
- formatting or labeling corrections

---

## Common Secondary Category Pairings

Some comments are best classified with both a primary and a secondary category.

Examples:

- `identification` + `exposition`
- `robustness` + `sample-construction`
- `mechanism` + `causal-language`
- `literature-positioning` + `exposition`
- `data-construction` + `sample-construction`

Use the primary category to decide the core response.  
Use the secondary category to decide what extra manuscript revision is needed.

---

## Quick Decision Rules

### If the comment questions whether the design identifies the claimed effect
Primary category:
- `identification`

### If the comment asks whether the result survives alternative specifications
Primary category:
- `robustness`

### If the comment asks how the effect operates
Primary category:
- `mechanism`

### If the comment asks whether the setting is too narrow for broad claims
Primary category:
- `external-validity`

### If the comment asks how variables, treatment, or outcomes were built
Primary category:
- `data-construction`

### If the comment asks who is in the sample, who is excluded, or why `N` changes
Primary category:
- `sample-construction`

### If the comment says the paper is hard to follow
Primary category:
- `exposition`

### If the comment says the paper ignores or misstates prior work
Primary category:
- `literature-positioning`

### If the comment says the wording is too strong for the design
Primary category:
- `causal-language`

### If the comment is local and non-substantive
Primary category:
- `minor-edit`

---

## Working Rule

A good classification should help answer three questions quickly:

1. what kind of concern is this really?  
2. what kind of response is needed?  
3. does the manuscript need new analysis, new exposition, narrower claims, or only a small correction?  

If the classification does not help decide those three things, it is not yet useful enough.
