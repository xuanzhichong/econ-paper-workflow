---
name: qa-response
description: Use when the user wants a strict, adversarial QA loop for an economics or agricultural economics referee response or R&R letter, including comment-coverage checks, manuscript-change traceability review, score-based quality gates, and iterative critic/fixer review before sending the response.
version: 0.2.0
---

# QA Response

Run a repo-native critic/fixer/verifier loop for economics and agricultural economics `response-letter.md` workflows.

This skill is for strict, adversarial quality control of referee responses and R&R letters.  
Use it when the user wants more than a normal drafting pass and explicitly needs a quality gate, submission-readiness judgment, or multi-round response-review loop.

## When To Use

Use this skill when the user wants:

- a final `R&R` response audit
- a coverage check for many referee comments
- a score or pass/fail verdict
- iterative critic/fixer review before sending the response
- hard-gate enforcement for coverage, traceability, tone, and revision mapping

Use `../review-response/SKILL.md` instead when the user primarily wants drafting help rather than a strict QA loop.

## Core Loop

```text
Pre-flight
    ->
response-critic round 1
    ->
response-fixer round 1
    ->
artifact-verifier
    ->
repeat if needed
    ->
stop at APPROVED or STOPPED-NOT-APPROVED
```

Maximum default loop length:

- 5 rounds

## Agent Roles

- `response-critic` identifies coverage failures, traceability problems, tone issues, and provisional scores
- `response-fixer` revises the response package conservatively and updates the change map
- `artifact-verifier` is the final gatekeeper and decides whether the response is approved, should continue, or must stop without approval

Do not collapse these roles into one generic review step.

## Pre-flight

Before the loop starts, identify:

- referee comments
- editor letter if relevant
- current `response-letter.md`
- `comment-to-change-map.md`
- manuscript locations cited in the response
- appendix / tables / figures cited in the response
- whether traceability can actually be checked from available artifacts

If comment-to-change traceability does not exist yet, create the minimal tracking structure before claiming QA coverage.

If the response package is too incomplete for adversarial QA, say so and produce a scoped pre-flight note instead of pretending the loop ran cleanly.

## Hard Gates

The response cannot be approved while any of these remain unresolved:

- a key referee point is unanswered
- the response promises a manuscript change that is not traceable
- the letter and revision map disagree materially
- the response cites manuscript changes that cannot be located
- the tone is evasive, defensive, or materially misleading
- the response blurs the distinction between manuscript revision and response-only explanation

When literature support or citation fidelity is materially disputed, use:

- `../citation-verification/SKILL.md`

## Response QA Rule

QA must prioritize:

- full coverage of referee concerns
- exact mapping from comment to response
- exact mapping from response to manuscript change
- consistency across response letter, revision map, and cited manuscript sections
- professional but non-evasive tone
- clear distinction between:
  - agreed and revised
  - clarified without revising
  - partially accommodated
  - respectfully declined

Do not treat polished wording as a substitute for traceability.

## Scoring Rubric

Score each category from `0-100`:

- completeness
- alignment to comments
- evidence and traceability
- tone
- revision mapping
- unresolved blockers

Thresholds:

- `80` = commit-ready
- `90` = submission-ready
- `95` = excellence

## Report Locations

- critic reports: `quality_reports/responses/*_critic_roundN.md`
- fixer reports: `quality_reports/responses/*_fixer_roundN.md`
- verifier reports: `quality_reports/verifier/*_response_verifier_roundN.md`

Use the templates in `quality_reports/templates/` when creating a new report.

## Expected Round Logic

1. `response-critic` produces:
   - issue list
   - hard-gate findings
   - provisional scores
2. `response-fixer` updates the response and change map conservatively, and reports what changed, what remains blocked, and what still requires manuscript-side evidence
3. `artifact-verifier` decides:
   - `APPROVED`
   - `CONTINUE`
   - `STOPPED-NOT-APPROVED`

If the verifier returns `CONTINUE`, run another critic/fixer round focused on unresolved coverage, traceability, or tone failures rather than reopening the entire response from scratch.

If 5 rounds are completed without approval, stop the loop and report the remaining blockers clearly.

## Final Output

Always provide:

- current verdict
- overall score
- hard-gate status
- top remaining blockers
- whether the response is `below-threshold`, `commit-ready`, `submission-ready`, or `excellence`
- next-round target, if the response is not approved

## Output Discipline

When the response is not ready:

- say exactly what blocks approval
- distinguish hard-gate failures from moderate weaknesses
- do not pretend the response is close to ready if coverage or traceability remains weak

When the response is approved:

- confirm that hard gates pass
- confirm that no critical unresolved issue remains
- report the final readiness level clearly
