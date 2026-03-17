---
name: review-response
description: Use when the user asks to respond to referee comments, draft an economics journal revision memo, prepare an R&R response letter, map comments to manuscript changes, or analyze reviewer concerns about identification, robustness, mechanism, exposition, or data construction.
version: 0.3.0
---

# Review Response for Economics Journals

Treat this workflow as a journal `referee response / R&R` process by default, not a short conference rebuttal.

If the user asks for a strict final check, wants an adversarial review loop, or needs a score-based readiness decision before sending the response, route to `../qa-response/SKILL.md`.

## Default Outputs

- `response-letter.md`
- `comment-to-change-map.md`

## Core Workflow

```text
Parse referee comments -> Classify issue type -> Decide response stance -> Map each comment to manuscript changes -> Draft response letter -> Check tone and consistency
```

## Comment Categories

Classify comments into these economics-friendly buckets:

- identification
- robustness
- mechanism
- external validity
- data construction
- exposition
- literature positioning
- formatting or minor edits

The classification should drive both the response and the revision plan.

## Response Stances

Use one of four stances for each comment:

- `accept and revise`
- `clarify existing logic`
- `partially accommodate`
- `decline with justification`

Do not default to "we agree" when the better response is to clarify boundaries or explain why a requested change would weaken identification.

## Required Structure for Each Comment

Each response should contain:

1. a short acknowledgement
2. the substantive reply
3. the manuscript action taken
4. the location of the change
5. any appendix or robustness addition

If you do not make the requested change, explain why directly and respectfully.

## Letter-Level Structure

The response letter should usually include:

- short thank-you paragraph
- overview of major revisions
- reviewer-by-reviewer responses
- optional closing note on further improvements

The `comment-to-change-map.md` should be a compact tracking table linking each referee point to the paper revision.

## Economics Defaults

- prioritize credibility and transparency over rhetorical flourish
- explain new robustness checks in relation to the identifying assumption
- if a request cannot be met because of data limits, say what was attempted and what remains infeasible
- if a comment reflects misunderstanding, improve the paper text rather than only defending it in the letter

## References to Load On Demand

- `references/referee-response-patterns.md`
- `references/review-classification.md`
- `references/response-strategies.md`
- `references/tone-guidelines.md`

Use the old rebuttal templates only after adapting them to journal style.

## Escalation Rule

Escalate to `qa-response` when any of these are true:

- the draft is near-final and the user wants a go/no-go judgment
- there are many referee comments and traceability is hard to track manually
- the user wants critic/fixer iteration instead of a one-pass edit
- the task requires hard gates, scores, or remaining-blocker reporting
