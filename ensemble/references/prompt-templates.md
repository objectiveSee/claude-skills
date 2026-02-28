# Prompt & Response Templates

Structured prompt construction and expected response formats for each ensemble stage type. When orchestrating a pipeline, use these templates to build the actual prompts dispatched to agents via the Task tool.

---

## Build Stage

### Prompt Template

```
You are Agent {N} of {M} working independently on the same task.

## Task
{task_description}

## Constraints
{constraints_if_any}

## Instructions
- Implement a complete solution to the task above
- Make your own independent design decisions — do NOT try to guess what other agents will do
- Focus on correctness first, then code quality
- You have full access to the codebase via your tools

## Required Response Format
Structure your final response using these exact headings:

### Approach
One paragraph describing your high-level strategy and why you chose it.

### Implementation
Summary of what you built/changed. List files modified or created.

### Key Decisions
Bullet list of non-obvious design choices you made and why.

### Confidence
One of: HIGH / MEDIUM / LOW
Brief justification (1-2 sentences).

### Risks
Bullet list of potential issues, edge cases not fully handled, or assumptions made.
```

### Notes
- Launch with `Task(prompt, isolation: "worktree", subagent_type: "general-purpose")`
- All N agents dispatched in a single message for parallel execution
- Each agent gets the same task but makes independent decisions

---

## Research Stage

### Prompt Template

```
You are Agent {N} of {M} researching the same question independently.

## Question
{research_question}

## Scope
{scope_constraints}

## Instructions
- Investigate thoroughly using all available tools (file reads, grep, web search, etc.)
- Form your own independent conclusions — do NOT try to guess what other agents will find
- Cite specific evidence (file paths, URLs, code snippets) for every claim

## Required Response Format
Structure your final response using these exact headings:

### Findings
Numbered list of key facts discovered, each with a source citation.

### Root Cause / Answer
Your direct answer to the question. Be specific and actionable.

### Confidence
One of: HIGH / MEDIUM / LOW
Brief justification (1-2 sentences).

### Evidence Quality
One of: STRONG (multiple independent sources) / MODERATE (single reliable source) / WEAK (indirect or circumstantial)

### Alternative Explanations
Bullet list of other plausible answers you considered and why you ruled them out. Write "None identified" if the answer is unambiguous.
```

### Notes
- Launch with `Task(prompt, subagent_type: "general-purpose")` — no worktree isolation needed
- All N agents dispatched in a single message for parallel execution

---

## Review Stage

### Prompt Template

```
You are Reviewer {N} of {M} evaluating {K} outputs from the previous stage.

## Original Task
{original_task_description}

## Outputs to Evaluate

{for each prior output:}
--- Output {i} (Agent {i}) ---
{agent_i_full_response}
--- End Output {i} ---

## Evaluation Criteria
Use this rubric (see references/consensus-evaluation.md for full details):
| Criterion   | Weight | Description                                    |
|-------------|--------|------------------------------------------------|
| Correctness | 40%    | Does it correctly address the task?            |
| Completeness| 25%    | Edge cases, constraints handled?               |
| Quality     | 20%    | Code quality, clarity, maintainability         |
| Approach    | 15%    | Sound reasoning and design?                    |

## Instructions
- Evaluate each output independently against the criteria
- Compare outputs to identify patterns of agreement and divergence
- Arrive at a clear verdict

## Required Response Format
Structure your final response using these exact headings:

### Per-Output Assessment
For each output, provide:
- **Output {i}**: Score {1-10}, one-sentence summary of strengths/weaknesses

### Patterns
- **Agreements**: What did multiple outputs get right or approach similarly?
- **Divergences**: Where did outputs disagree or take different approaches?

### Verdict
One of:
- **CONSENSUS: Output {i}** — if one output is clearly best, state which and why
- **NO_CONSENSUS** — if no clear winner, summarize the core disagreement

### Rationale
2-3 sentences explaining your verdict.
```

### Notes
- Launch with `Task(prompt, subagent_type: "general-purpose")` — no worktree isolation
- The prompt must include ALL prior outputs inline so reviewers can compare
- All M reviewers dispatched in a single message for parallel execution
- Keep prior outputs verbatim — do not summarize them for reviewers

---

## Synthesize Stage

### Prompt Template

```
You are the Synthesizer. You have received {K} outputs from the previous stage.

## Original Task
{original_task_description}

## Outputs to Synthesize

{for each prior output:}
--- Output {i} (Agent {i}) ---
{agent_i_full_response}
--- End Output {i} ---

## Instructions
- Identify what each output got right
- Resolve contradictions by picking the better-supported position
- Produce a single unified answer that takes the best from each output
- If outputs are code: produce a single best implementation, cherry-picking the strongest elements
- If outputs are research: produce a single coherent answer with the strongest evidence

## Required Response Format
Structure your final response using these exact headings:

### Consensus Points
Bullet list of conclusions or design choices that multiple outputs agreed on.

### Contradictions
Bullet list of points where outputs disagreed, with your resolution and reasoning for each.

### Synthesis
The final unified answer, implementation plan, or conclusion. This is the primary deliverable.

### Open Questions
Bullet list of unresolved issues that need human input. Write "None" if everything is resolved.

### Verdict
One of:
- **CONSENSUS** — the outputs were largely compatible and a strong synthesis was possible
- **PARTIAL_CONSENSUS** — synthesis was possible but significant disagreements remain (see Open Questions)
- **NO_CONSENSUS** — outputs were fundamentally incompatible; human guidance needed
```

### Notes
- Typically 1 synthesizer agent (default), but can be more for complex tasks
- Launch with `Task(prompt, subagent_type: "general-purpose")` — no worktree isolation
- The synthesizer sees ALL prior outputs inline
- For code tasks, the synthesizer may need worktree isolation if it needs to produce a merged implementation
