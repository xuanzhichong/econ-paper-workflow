# Visualization Best Practices for Empirical Economics and Agricultural Economics

Figures should clarify identification, interpretation, and empirical support.  
They are not decoration.

A good figure should help the reader answer one of three questions:

1. what identifying variation does the paper use?  
2. what does the main empirical pattern look like?  
3. how robust or limited is that pattern?  

If a figure does not improve identification clarity, empirical interpretation, or transparency, it probably does not belong in the main text.

---

## Figures Should Support Identification

Prioritize figures that clarify:

- treatment timing
- support around the cutoff
- dynamic effects
- balance or distribution shifts
- robustness patterns across specifications
- sample construction when attrition or exclusion is material
- whether the graphical pattern matches the regression interpretation

Figures should help the reader see the design, not just the result.

---

## Preferred Figure Families

### 1. Event-study coefficients with confidence intervals

Use when the design depends on treatment timing and dynamic effects.

Best for showing:

- pre-treatment patterns
- post-treatment dynamics
- omitted period normalization
- whether coefficients are precise or noisy over relative time

Must disclose:

- omitted period
- interval type
- treatment timing convention
- whether distant leads/lags are binned

---

### 2. Binned scatterplots with transparent construction notes

Use when the figure helps show a descriptive relationship or residualized pattern clearly.

Best for showing:

- conditional relationships
- partialled-out associations
- variation in support across the observed range

Must disclose:

- what is residualized, if anything
- how bins are constructed
- whether the plotted line is descriptive or model-based
- sample used

Do not let the graph imply stronger causal interpretation than the underlying design supports.

---

### 3. RD plots with bandwidth disclosure

Use when the design is regression discontinuity.

Best for showing:

- support around the cutoff
- discontinuity at the threshold
- local fit on either side of the cutoff

Must disclose:

- cutoff
- bandwidth
- binning rule
- fit type or smoothing rule
- whether the graph is illustrative or corresponds exactly to the estimating sample

A good RD graph makes the local nature of the design visible.

---

### 4. Coefficient plots for robustness sweeps

Use when many related estimates need to be compared without crowding the paper with many tables.

Best for showing:

- how the coefficient changes across specifications
- how interval width changes
- whether sign, size, and precision are stable

Must disclose:

- what changes across specifications
- whether the sample changes
- interval type
- omitted baseline if relevant

Do not combine incomparable specifications in a way that makes visual comparison misleading.

---

### 5. Sample flow diagrams when attrition is material

Use when sample construction is central to interpretation or there is substantial attrition, exclusion, or linkage loss.

Best for showing:

- initial sample
- exclusion stages
- merge failures
- final estimation sample

Must disclose:

- reason for each exclusion
- count at each stage
- final analysis sample

This is especially useful when the reader would otherwise struggle to reconstruct the estimation sample from the text alone.

---

### 6. Descriptive trend plots

Use when pre-treatment evolution, raw trends, or institutional timing need to be shown before moving to the formal estimate.

Best for showing:

- treated versus comparison-group trends
- outcome evolution before and after policy timing
- broad descriptive context for later regression results

Must disclose:

- whether values are raw or adjusted
- sample used
- timing markers
- whether the graph is descriptive only

Descriptive trend plots should support the regression evidence, not replace it.

---

### 7. Distribution or support plots

Use when support, overlap, skewness, or trimming decisions matter for interpretation.

Best for showing:

- running-variable density near a cutoff
- treatment intensity distribution
- support by subgroup
- balance or overlap problems

Must disclose:

- sample
- scaling
- trimming or winsorization if relevant
- subgroup definitions

These figures are especially useful when sample support is part of the identification story.

---

## Non-Negotiables

- axis labels include units
- omitted period or normalization is labeled
- captions state sample, estimator, and interval type when relevant
- color is helpful but not required for interpretation
- do not hide economically important scale choices
- figures should remain interpretable in grayscale or poor print conditions
- interval display should be clear enough to support inference reading
- graphical choices should not make the pattern look stronger than the underlying estimate

---

## Caption Discipline

A good caption should state, as relevant:

- what is plotted
- sample
- unit of observation
- estimator or construction method
- confidence interval or standard error type
- omitted period / cutoff / normalization
- whether the figure is descriptive or tied directly to the regression specification

The caption should make the figure interpretable without forcing the reader back into the main text for basic decoding.

---

## Comparability Across Figures

When multiple figures are meant to be compared:

- keep scales comparable when the comparison is substantive
- label specifications consistently
- keep subgroup definitions stable
- avoid changing units or normalization silently across panels
- make clear when one panel uses a different sample or specification

Comparability problems can make a figure set visually attractive but substantively misleading.

---

## Scale and Construction Transparency

Do not hide important choices in construction.

Disclose when relevant:

- binning rules
- bandwidth choices
- smoothing methods
- residualization steps
- normalization
- sample restrictions
- grouped leads/lags or trimmed windows

If the visual pattern depends heavily on one construction choice, the reader should know that.

---

## Common Failures

- event-study graph without clear omitted category
- coefficient plot with incomparable specifications
- RD graph without bandwidth or binning disclosure
- figure title that overstates causality
- styling choices that make inference harder to read than the table
- descriptive graph narrated as if it were causal evidence
- caption too vague to explain what is actually plotted
- panel scales that silently change and distort visual comparison
- figures and tables that appear to support different substantive conclusions

---

## Working Rule

A strong empirical figure should make one important point clearer than a table alone could.

If the figure:

- hides the identifying convention
- obscures uncertainty
- makes incomparable estimates look comparable
- or pushes the reader toward a stronger causal reading than the design supports

then it is not ready.
