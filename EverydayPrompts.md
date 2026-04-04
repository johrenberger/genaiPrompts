# Everyday Prompts
## Use the 80/20 principle to learn faster
```text
CONTEXT:
You are a top-tier expert in [FIELD].

TASK:
Teach me [TOPIC] using the 80/20 principle.

INSTRUCTIONS:
1. Identify the critical ~20% of concepts that unlock ~80% of understanding.
2. For each concept:
   - Explain concisely
   - State why it matters
   - Provide a concrete example
3. Explicitly exclude low-value topics.

GUARDRAILS:
- Do not invent facts, frameworks, or terminology.
- If uncertain, say “Uncertain” and bound the claim.
- Prefer widely accepted concepts over niche interpretations.
- Flag any assumptions explicitly.

OUTPUT FORMAT:
- Key Concepts
- Why They Matter
- Examples
- What to Ignore
- Assumptions & Uncertainty
```

## Clear Task Breakdown
```text
CONTEXT:
You are an execution strategist optimizing for speed and correctness.

TASK:
Break the task into atomic steps.

INPUT:
Task: [PASTE TASK]

INSTRUCTIONS:
1. Decompose into smallest actionable steps.
2. Order for fastest completion (parallelize where valid).
3. Remove non-essential steps.
4. Highlight dependencies.

GUARDRAILS:
- Do not assume tools, access, or permissions unless stated.
- Flag missing prerequisites explicitly.
- If multiple valid approaches exist, choose one and justify briefly.
- Avoid implicit steps—everything must be explicit.

OUTPUT FORMAT:
- Step-by-step plan
- Parallelizable steps
- Critical path
- Dependencies / Missing Inputs
- Risks / Failure Points
```

## Chain of Thought
```text
CONTEXT:
You are an expert in [FIELD] known for precise reasoning.

TASK:
Advise on the following:

INPUT:
[QUESTION / PROBLEM]

INSTRUCTIONS:
1. Break problem into components.
2. Reason stepwise (concise).
3. State assumptions explicitly.
4. Deliver a clear recommendation.

GUARDRAILS:
- Separate facts vs assumptions vs inference.
- Do not fabricate data or cite unknown sources.
- If uncertainty is high, provide bounded scenarios instead of a single answer.
- Avoid overconfidence.

OUTPUT FORMAT:
- Problem Breakdown
- Assumptions
- Reasoning
- Recommendation
- Confidence & Uncertainty
```

## The Fast Decision Helper
```text
CONTEXT:
You are a decision strategist optimizing for outcome quality.

TASK:
Evaluate and choose the best option.

INPUT:
Options: [LIST OPTIONS]

INSTRUCTIONS:
1. Evaluate each option: Impact, Risk, Effort.
2. Keep analysis concise.
3. Make a clear recommendation.

GUARDRAILS:
- Do not default to “it depends”—force a decision.
- Surface only tradeoffs that change the outcome.
- If data is missing, state assumptions clearly.
- Identify any bias in evaluation criteria.

OUTPUT FORMAT:
- Comparison Table
- Key Tradeoffs
- Recommendation
- Assumptions
- Confidence Level
```

## The Problem Framer
```text
CONTEXT:
You are a senior operator communicating to executives.

TASK:
Frame the problem clearly.

INPUT:
Problem: [DESCRIBE ISSUE]

INSTRUCTIONS:
1. Remove ambiguity.
2. Focus on measurable impact.
3. Make recommendation actionable.

GUARDRAILS:
- Do not include speculation as fact.
- Quantify impact where possible (or label as estimate).
- Avoid vague language (“significant”, “large”) without context.
- Clearly separate facts from interpretation.

OUTPUT FORMAT:
1. What is happening (facts)
2. Why it matters (quantified impact)
3. Recommended action
4. Expected outcome
5. Assumptions / Unknowns
```
## Goal Deconstructor
```text
CONTEXT:
You are a goal strategist focused on execution success.

INPUT:
Goal = [GOAL]
Deadline = [DATE]

TASK:
Create a high-probability execution plan.

INSTRUCTIONS:
1. Define measurable success.
2. Break into 3–5 milestones.
3. Convert to actions.
4. Define habits.
5. Identify failure risks.

GUARDRAILS:
- Validate feasibility vs timeline (flag if unrealistic).
- Do not assume unlimited time/resources.
- Highlight dependency on external factors.
- Prioritize actions by impact, not volume.

OUTPUT FORMAT:
- Goal Definition
- Milestones
- Action Plan
- Key Habits
- Failure Risks + Mitigation
- Feasibility Assessment
- Immediate Next Actions
```

## Evaluate Logic of Response By AI
```text
CONTEXT:
You are a precision advisor optimizing for relevance.

TASK:
Do NOT answer yet.

INSTRUCTIONS:
1. List key assumptions.
2. Identify missing info that would change the answer.
3. Identify common failure modes.
4. Ask exactly 2 high-impact clarifying questions.

GUARDRAILS:
- Do not proceed without user input.
- Focus only on decision-critical gaps.
- Avoid generic or low-signal questions.

STOP.

INPUT:
My request: [INSERT REQUEST]
```

## Example Market Analysis
```text
CONTEXT:
You are a market intelligence analyst.

TASK:
Identify high-potential niches.

INPUT:
Sector: [INSERT]

INSTRUCTIONS:
1. Identify 3 niches with high growth + low saturation.
2. Base on recent patterns (prefer 2024–2025).

GUARDRAILS:
- Do not fabricate market data.
- Clearly label speculative insights as “Speculative”.
- Prefer directional trends over precise but unverifiable numbers.
- Avoid generic or obvious niches.

OUTPUT FORMAT (per niche):
- Niche Description
- Why Now (trend drivers)
- Market Gap
- SWOT Analysis
- Monetization Paths
- 2026 Outlook
- Evidence vs Speculation
```
