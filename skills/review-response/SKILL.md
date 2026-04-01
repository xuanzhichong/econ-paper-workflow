---
name: review-response
description: Use when the user asks to respond to reviewer comments, draft an economics or agricultural economics journal revision memo, prepare an R&R response letter, map comments to manuscript changes, or analyze reviewer concerns about identification, robustness, mechanism, exposition, data construction, or claim strength.
version: 0.4.1
---

# Review Response for Economics and Agricultural Economics Journals

Treat this workflow as a journal `reviewer response / R&R` process by default, not a short conference response.

Use this skill for drafting and revising response letters, organizing comment-to-change traceability, and choosing appropriate response strategies for empirical economics and agricultural economics manuscripts.

If the user asks for a strict final check, wants an adversarial review loop, or needs a score-based readiness decision before sending the response, route to `../qa-response/SKILL.md`.

---

## Default Outputs

- `response-letter.md`
- `comment-to-change-map.md`

Generate additional tracking notes only when they improve coverage, traceability, or manuscript-response alignment.

---

## Core Workflow

    Parse reviewer comments
        ->
    Classify issue type
        ->
    Decide response stance
        ->
    Map each comment to manuscript changes
        ->
    Draft response letter
        ->
    Check tone, traceability, and consistency

---

## Comment Categories

Classify comments into these economics- and agricultural-economics-friendly buckets:

- identification
- robustness
- mechanism
- external validity
- data construction
- sample construction
- exposition
- literature positioning
- causal language
- minor edit

A comment may have:

- one primary category
- one optional secondary category

The classification should drive both the response and the revision plan.

---

## Response Stances

Use one of the following stances for each comment:

- `accept and revise`
- `clarify and revise exposition`
- `clarify without revising`
- `partially accommodate`
- `decline with justification`

Do not default to "we agree" when the better response is to clarify boundaries, narrow claims, explain infeasibility, or explain why a requested change would weaken identification.

---

## Required Structure for Each Comment

Each response should contain:

1. a short acknowledgement
2. the response stance
3. the substantive reply
4. the manuscript action taken, if any
5. the location of the change
6. any appendix or robustness addition, if relevant
7. any remaining limitation or scope boundary, if the request is only partially addressed or declined

If you do not make the requested change, explain why directly and respectfully.

Do not blur:

- manuscript revision
- response-only clarification
- partial accommodation
- respectful decline

---

## Letter-Level Structure

The response letter should usually include:

- a short thank-you paragraph
- an overview of the major revisions
- reviewer-by-reviewer responses
- editor-specific note if relevant
- an optional short closing paragraph

The `comment-to-change-map.md` should be a compact tracking table linking each reviewer point to:

- response stance
- manuscript action
- location of change
- appendix or supplementary material if relevant

---

## Economics and Agricultural Economics Defaults

- prioritize credibility and transparency over rhetorical flourish
- explain new robustness checks in relation to the identifying assumption
- if a request cannot be met because of data limits, say what was attempted and what remains infeasible
- if a comment reflects misunderstanding, improve the paper text rather than only defending it in the letter
- do not overstate what a new robustness check proves
- keep mechanism evidence weaker than or equal to what the design can actually support
- distinguish clearly between revised manuscript content and response-only clarification
- narrow causal language when the design supports less than the current wording suggests

---

## Response Discipline

A strong response should make it easy for the reviewer or editor to answer:

1. what is the concern?
2. what is the author’s stance?
3. what changed in the manuscript, if anything?
4. where can that change be found?
5. what remains outside the paper’s scope, if relevant?

If those five points are not easy to identify, the response is not yet strong enough.

---

## References to Load On Demand

- `references/reviewer-response-patterns.md`
- `references/review-classification.md`
- `references/response-strategies.md`
- `references/tone-guidelines.md`
- `references/successful-cases.md`
- `references/response-letter-templates.md`

Use older legacy response templates only after adapting them to journal response style.

---

## Escalation Rule

Escalate to `qa-response` when any of these are true:

- the draft is near-final and the user wants a go / no-go judgment
- there are many reviewer comments and traceability is hard to track manually
- the user wants critic / fixer iteration instead of a one-pass edit
- the task requires hard gates, scores, or remaining-blocker reporting
- the user wants a strict final audit of coverage, tone, and response-manuscript consistency
