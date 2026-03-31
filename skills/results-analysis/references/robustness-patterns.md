# Robustness Patterns for Empirical Economics and Agricultural Economics

Use robustness checks to test the design's weak spots, not to generate a random appendix.

Robustness checks should be **threat-driven**, not accumulation-driven.  
Adding more checks does not automatically strengthen identification if those checks do not address a real design concern.

The key question is always:

> What concern does this specification address?

---

## Core Principle

A good robustness section does not ask:

- how many extra regressions can we show?
- how many appendix tables can we add?

A good robustness section asks:

- what identification threats remain after the baseline design?
- which checks directly speak to those threats?
- does the substantive conclusion survive once those threats are probed?

A robustness exercise is useful only if it helps the reader evaluate the credibility, scope, or interpretation of the main result.

---

## Typical Layers

### 1. Sample Robustness

Use sample robustness when the main concern is that the result depends on who is included in the estimation sample.

Common checks:

- alternative age, region, or sector restrictions
- balanced versus unbalanced panels
- excluding influential observations
- harmonized adjusted sample versus changing sample across specifications
- excluding policy-prioritized, unusually early-treated, or otherwise atypical units when treatment timing may be selective
- excluding neighboring or potentially contaminated units when spillovers are plausible

Use this layer to ask:

- does the result survive plausible sample restrictions?
- is the estimate driven by a narrow subset of observations?
- are differences across columns really specification effects, or just sample drift?

---

### 2. Variable Robustness

Use variable robustness when the main concern is coding, timing, or measurement of treatment, outcomes, or key controls.

Common checks:

- alternative outcome definitions
- alternative treatment timing
- different winsorization or trimming rules
- alternative treatment intensity or exposure definitions
- alternative coding of rollout, eligibility, or policy onset
- alternative index construction or standardization rules

Use this layer to ask:

- is the result sensitive to one specific coding rule?
- does the conclusion survive reasonable alternative definitions?
- is the treatment effect being driven by a fragile measurement choice?

---

### 3. Design Robustness

Use design robustness when the main concern is that the identifying design may be too dependent on one specification or inference choice.

Common checks:

- alternative FE structures
- alternative clustering levels
- placebo treatments or outcomes
- pre-trend checks
- bandwidth or event-window sensitivity
- spillover-sensitive samples or neighboring exclusions
- first-stage strength and instrument-definition checks if IV
- manipulation or continuity checks if RDD

Use this layer to ask:

- does the design remain credible under reasonable alternative implementation choices?
- is inference fragile to FE or clustering choices?
- does the result weaken once the design is tested against its main validity threats?

---

### 4. Interpretation Robustness

Use interpretation robustness when the estimate remains directionally similar, but statistical precision or substantive meaning may change across specifications.

Common checks:

- show whether magnitudes are economically meaningful
- explain when significance changes but sign and size remain similar
- distinguish loss of precision from genuine instability
- clarify whether the substantive conclusion survives even when statistical significance weakens
- avoid treating sign stability alone as proof of causal validity

Use this layer to ask:

- is the paper's substantive claim still reasonable?
- does the reader need a weaker verbal interpretation?
- is the change about power, sample composition, or a genuinely different estimate?

---

## How to Organize Robustness in the Paper

Robustness should be organized by **identification threat**, not by arbitrary sequences of extra regressions.

A good robustness paragraph usually follows this logic:

1. state the concern
2. explain the check
3. report the result
4. explain what the result implies for credibility

Example logic:

- concern: treatment timing may be selective
- check: exclude early adopters and use alternative timing definitions
- result: the coefficient remains similar in sign and magnitude
- implication: the baseline finding is less likely to be driven only by early-treatment selection

---

## What Robustness Is Not

Robustness is not:

- repeating the baseline with cosmetic changes
- adding appendix tables with no design purpose
- moving core identification logic out of the main text
- presenting decorative placebo tests that answer no real concern
- treating every extra regression as equally informative

If a check does not answer a real challenge to the design, it should not be presented as an important robustness result.

---

## Writing Rule

When writing the robustness section, avoid generic statements such as:

- the results are robust to a variety of specifications

Prefer explicit, threat-linked wording such as:

- these checks reduce the concern that the baseline estimate is driven by treatment coding
- the result remains stable after excluding early adopters
- alternative clustering choices leave the substantive conclusion unchanged
- the estimate is less precise, but its sign and economic magnitude remain similar

---

## Final Discipline Rule

Every robustness check should answer:

1. what threat does this check address?
2. what changed relative to the baseline?
3. did the substantive conclusion survive?
4. how should the main claim be updated, if at all?

If those questions cannot be answered clearly, the check is probably not worth keeping.
