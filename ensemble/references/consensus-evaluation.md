# Consensus Evaluation

How to determine whether agents have reached consensus, and what to do when they haven't.

---

## Consensus Algorithm

After collecting all reviewer/synthesizer verdicts from a fan-in stage, apply these rules in order:

### 1. Unanimous Agreement
**Condition**: All reviewers return `CONSENSUS` and select the **same** output.
**Action**: Proceed automatically with the selected output. Report to user: "All {M} reviewers agreed on Output {i}."

### 2. Unanimous Consensus, Different Selections
**Condition**: All reviewers return `CONSENSUS` but select **different** outputs.
**Action**: Stop. Present the options to the human via AskUserQuestion:
- Each selected output as a numbered option with the reviewer's rationale
- "Re-run review stage" option
- "Provide guidance and re-run" option

### 3. Supermajority Consensus (>= 2/3)
**Condition**: At least 2/3 of reviewers return `CONSENSUS` for the **same** output.
**Action**: Proceed with the majority pick. Report to user: "{X} of {M} reviewers selected Output {i}. {Y} reviewer(s) dissented — {brief dissent summary}."

### 4. Simple Majority but Below Threshold
**Condition**: More than half but fewer than 2/3 of reviewers agree.
**Action**: Stop. Escalate to human (see Escalation Format below).

### 5. No Majority
**Condition**: No output receives more than half of reviewer selections, or majority returned `NO_CONSENSUS`.
**Action**: Stop. Escalate to human (see Escalation Format below).

---

## Evaluation Rubric

Reviewers use this rubric when scoring outputs in the review stage. Each criterion has a weight that determines its contribution to the overall score.

| Criterion    | Weight | What to Evaluate |
|--------------|--------|------------------|
| Correctness  | 40%    | Does the output correctly solve the stated task? Are there bugs, logical errors, or misunderstandings of the requirements? |
| Completeness | 25%    | Are edge cases handled? Are all constraints from the task addressed? Is anything missing? |
| Quality      | 20%    | Code: readability, maintainability, idiomatic patterns. Research: clarity, organization, citation quality. |
| Approach     | 15%    | Is the overall strategy sound? Are design decisions well-reasoned? Is the solution appropriately scoped? |

### Scoring Guide
- **9-10**: Exceptional. No meaningful improvements needed.
- **7-8**: Good. Minor issues that don't affect core correctness.
- **5-6**: Acceptable. Works but has notable gaps or quality issues.
- **3-4**: Below expectations. Significant problems with correctness or completeness.
- **1-2**: Fundamentally flawed. Major misunderstanding of the task or broken implementation.

### Weighted Score Calculation
```
weighted_score = (correctness * 0.40) + (completeness * 0.25) + (quality * 0.20) + (approach * 0.15)
```

Reviewers do not need to compute this explicitly — it guides relative importance when forming their verdict.

---

## Escalation Format

When consensus fails (rules 4 or 5 above), present the disagreement to the human using AskUserQuestion with this structure:

### Summary Message
```
The review stage did not reach consensus ({X} of {M} reviewers agreed, threshold is 2/3).

Here's where the reviewers landed:

**Position A** ({count} reviewer(s)): {1-sentence summary of position}
  - Selected: Output {i}
  - Key reasoning: {brief rationale}

**Position B** ({count} reviewer(s)): {1-sentence summary of position}
  - Selected: Output {j}
  - Key reasoning: {brief rationale}

{Additional positions if any}

**Core Disagreement**: {1-sentence description of what the reviewers fundamentally disagree about}
```

### AskUserQuestion Options
Present these as numbered options:

1. **"Go with Output {i}"** — Description: "Position A ({count} reviewers). {1-sentence rationale}."
2. **"Go with Output {j}"** — Description: "Position B ({count} reviewers). {1-sentence rationale}."
3. **"Re-run with more agents"** — Description: "Add more builders and reviewers to break the tie."
4. **"Provide guidance"** — Description: "Give direction to resolve the disagreement, then re-run."

If there are more than 2 distinct positions, include up to 4 output options (the AskUserQuestion limit), prioritized by reviewer count.

---

## Applying Consensus to Synthesize Stages

The synthesizer's `Verdict` field maps to consensus as follows:
- `CONSENSUS` → Proceed. Present synthesis to user as the final result.
- `PARTIAL_CONSENSUS` → Present synthesis to user but highlight Open Questions. Ask if they want to proceed or provide guidance on the open items.
- `NO_CONSENSUS` → Escalate. Present the synthesizer's Contradictions analysis and use the Escalation Format above, adapted for synthesis (positions come from the synthesizer's analysis rather than from multiple reviewers).
