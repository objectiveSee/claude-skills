---
name: ensemble
description: Multi-agent ensemble orchestrator. Triggers on "ensemble", "consensus", "multi-agent", "fan out", /ensemble, or any request to have multiple agents independently work on the same problem and compare results. Supports multi-stage fan-out/fan-in pipelines, git worktree isolation for code stages, structured prompts/responses, and human-in-the-loop escalation.
---

# Ensemble

## Overview

Ensemble orchestrates multi-agent pipelines where N agents independently tackle the same problem, then M reviewers evaluate all outputs to find consensus. The pattern is: **fan-out -> fan-in -> consensus gate -> optional iterate**. Every stage produces structured, comparable outputs using templates from `references/prompt-templates.md`, and consensus is evaluated using the algorithm in `references/consensus-evaluation.md`.

This is a pure orchestration skill — it drives the Task tool to dispatch agents, not deterministic scripts.

## Stage Types

Four stage types compose every pipeline:

| Stage Type   | Direction | Isolation | Purpose |
|--------------|-----------|-----------|---------|
| `build`      | fan-out   | worktree  | Each agent writes code independently in isolated git worktrees |
| `research`   | fan-out   | none      | Each agent investigates a question independently |
| `review`     | fan-in    | none      | Agents compare all prior outputs, score them, evaluate agreement |
| `synthesize` | fan-in    | none      | Single agent merges the best elements from all prior outputs |

**Fan-out** stages dispatch N agents in parallel, each working independently on the same task.
**Fan-in** stages receive all prior outputs and produce a comparative evaluation or merged result.

## Orchestration Workflow

Follow these steps exactly when orchestrating an ensemble pipeline:

### Step 1: Parse the Request

Analyze the user's natural language request and decompose it into a pipeline of stages. Determine:
- What stages are needed (build, research, review, synthesize)
- How many agents per stage (use defaults if not specified)
- What the task/question is for fan-out stages
- Whether worktree isolation is needed (code tasks = yes)

### Step 2: Present Pipeline for Confirmation

**Always present the pipeline to the user and wait for confirmation before dispatching any agents.** Use AskUserQuestion with a summary like:

```
Here's the pipeline I'll run:

Stage 1 (build, fan-out): 5 agents write implementations in isolated worktrees
  Task: "{task summary}"

Stage 2 (review, fan-in): 3 reviewers evaluate all 5 outputs
  Criteria: correctness, completeness, quality, approach

Stage 3 (synthesize, fan-in): 1 synthesizer merges the best elements

Estimated: 9 agent dispatches across 3 stages.
```

Options: "Run this pipeline", "Adjust agent counts", "Modify stages", "Cancel"

### Step 3: Execute Each Stage

For each stage in sequence:

1. **Construct prompts** using the templates in `references/prompt-templates.md`
   - Fill in the template variables: agent ID, task description, constraints, prior outputs
   - **CRITICAL**: Every prompt MUST include the `## Required Response Format` section from the corresponding template. Copy it verbatim — all agents in the same stage must receive the identical format. This is what makes their outputs comparable.
   - Every prompt includes the agent's role identifier ("You are Agent 3 of 5")

2. **Dispatch agents** via the Task tool
   - All agents within a stage launch in a **single message** for parallel execution
   - See "Launching Agents" below for exact Task tool parameters per stage type

3. **Collect structured responses** from all agents
   - Parse each agent's response according to the expected format
   - Note any agents that failed or returned malformed responses

4. **Run the consensus gate** after each fan-in stage
   - Apply the algorithm from `references/consensus-evaluation.md`
   - If consensus: proceed to next stage or present final result
   - If no consensus: stop and escalate to human

### Step 4: Present Results

After the final stage:
- If consensus was reached: present the winning output or synthesis to the user
- Include a brief summary of the pipeline execution (agent counts, consensus details, any dissent)
- Ask the user to approve the result before taking any action on it

## Defaults

| Parameter | Default | Notes |
|-----------|---------|-------|
| Builders (fan-out) | 5 | Can be adjusted by user in pipeline confirmation |
| Reviewers (fan-in) | 3 | Odd number recommended to avoid ties |
| Synthesizers | 1 | Rarely needs more than 1 |
| Consensus threshold | 2/3 majority | Per `references/consensus-evaluation.md` |
| Agent model | inherit | Agents inherit the current model unless user specifies |

## Critical Rules

These rules are **non-negotiable** and must be followed for every orchestration run:

1. **Response format is mandatory.** Every agent prompt MUST include a `## Required Response Format` section copied from the corresponding stage template in `references/prompt-templates.md`. All agents within the same stage MUST receive the identical response format. Without standardized formats, comparing outputs across agents is impossible and the consensus gate cannot function.

2. **Prior outputs must be included verbatim.** Fan-in stages (review, synthesize) MUST include the complete structured output from every prior agent. Do not summarize, truncate, or paraphrase — reviewers and synthesizers need the full original text to evaluate accurately.

3. **Pipeline confirmation is required before dispatch.** Never launch agents without presenting the pipeline plan to the user first and receiving explicit approval (Step 2). No exceptions.

4. **Consensus failure always escalates to human.** When the consensus gate fails, you MUST stop and present the disagreement to the user. Never auto-resolve a consensus failure by picking a winner yourself.

## Launching Agents

### Build Stage
```
Task(
  prompt: "<built from references/prompt-templates.md Build template>",
  subagent_type: "general-purpose",
  isolation: "worktree"
)
```
- Dispatch all N build agents in a **single message** with N Task tool calls
- Each agent gets `isolation: "worktree"` for independent code changes
- Each prompt includes "You are Agent {N} of {M}" and the structured response format

### Research Stage
```
Task(
  prompt: "<built from references/prompt-templates.md Research template>",
  subagent_type: "general-purpose"
)
```
- Dispatch all N research agents in a **single message** with N Task tool calls
- No worktree isolation — research agents only read, they don't write code

### Review Stage
```
Task(
  prompt: "<built from references/prompt-templates.md Review template, including ALL prior outputs>",
  subagent_type: "general-purpose"
)
```
- Dispatch all M reviewers in a **single message** with M Task tool calls
- The prompt **must include all prior outputs verbatim** so reviewers can compare
- Each reviewer independently scores and selects

### Synthesize Stage
```
Task(
  prompt: "<built from references/prompt-templates.md Synthesize template, including ALL prior outputs>",
  subagent_type: "general-purpose"
)
```
- Typically 1 synthesizer, dispatched as a single Task tool call
- The prompt includes all prior outputs for the synthesizer to merge
- For code synthesis that needs to produce files, add `isolation: "worktree"`

## Human-in-the-Loop

This skill is designed for human oversight at every critical juncture:

1. **Pipeline confirmation** (Step 2): Always present the full pipeline plan and wait for user approval before dispatching any agents. Never auto-dispatch.

2. **Consensus failure**: When the consensus gate fails (per `references/consensus-evaluation.md`), stop immediately and present the disagreement summary to the user via AskUserQuestion with clear numbered options.

3. **Final result approval**: After the pipeline completes, present the result to the user. Do not automatically apply code changes, merge worktrees, or take action — wait for explicit approval.

4. **Mid-pipeline adjustment**: If a stage produces unexpected results (e.g., all agents report LOW confidence), pause and ask the user whether to continue, adjust, or abort.

## Error Handling

### Agent Failure
- If an agent fails but >= 2 agents in the same stage succeeded: proceed with the successful outputs. Note the failure in the pipeline summary.
- If < 2 agents succeed in a stage: escalate to human. Present what failed and offer options: re-run the stage, re-run with different parameters, or abort.

### Worktree Failure
- If worktree creation fails for a build agent: retry that agent without isolation (`isolation` parameter omitted). Note the degradation in the pipeline summary — the agent's changes will be in the main working directory.
- If multiple worktree failures occur: ask the user whether to continue without isolation or abort.

### Stage Failure
- A stage fails if < 2 agents produce usable structured responses.
- On stage failure: stop the pipeline, present what was collected, and offer options via AskUserQuestion: re-run the stage, skip to next stage (if fan-in), or abort.

### Malformed Responses
- If an agent's response doesn't follow the structured format: still include it in the pipeline but flag it for reviewers as "unstructured response — evaluate content directly."

## Common Pipeline Patterns

### Code Implementation (default)
```
build (5 agents, worktree) -> review (3 agents) -> synthesize (1 agent)
```

### Research Question
```
research (5 agents) -> synthesize (1 agent)
```

### Research with Review
```
research (5 agents) -> review (3 agents) -> synthesize (1 agent)
```

### Quick Comparison (lightweight)
```
build (3 agents, worktree) -> review (2 agents)
```

### Deep Investigation
```
research (5 agents) -> review (3 agents) -> research (3 agents, refined question) -> synthesize (1 agent)
```

## References

- `references/prompt-templates.md` — Structured prompt and response format templates for all four stage types. Read this before constructing any agent prompt.
- `references/consensus-evaluation.md` — Consensus algorithm, evaluation rubric, thresholds, and escalation format. Read this before evaluating any fan-in stage results.
