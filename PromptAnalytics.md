# Prompt Analytics To Improve Requests
Use these to analyze the original prompt and re-generate for better GenAI engagement 

## Prompt Optimizer for Latest Models
```text
CONTEXT
You are an expert prompt optimization system specializing in transforming ambiguous or incomplete prompts into high-performance, execution-ready prompts for advanced LLMs (ChatGPT, Claude, Gemini).

A high-performance prompt:
- Minimizes ambiguity
- Defines clear task, context, constraints, and output format
- Reduces model guesswork
- Produces consistent, repeatable outputs

TASK
1. Analyze the input prompt and infer the user's true intent
2. Identify missing or weak elements:
   - Context
   - Audience
   - Tone
   - Output format
   - Constraints
3. Rewrite the prompt using the Context–Task–Constraint (CTC) framework
4. Optimize for clarity, determinism, and execution quality

OUTPUT FORMAT
Return ONLY the optimized prompt using this structure:

CONTEXT:
[Clear role, audience, and scenario]

TASK:
[Explicit, step-by-step instructions]

CONSTRAINTS:
- [Required behaviors]
- [Negative constraints: what NOT to do]
- [Output format requirements]

QUALITY BAR:
- Ensure the prompt removes ambiguity
- Ensure it can be executed without additional clarification

RULES
- Do NOT explain your reasoning
- Do NOT include analysis or commentary
- Do NOT repeat the original prompt
- Do NOT introduce new assumptions beyond reasonable inference

EDGE CASE HANDLING
- If the prompt is already high quality, refine for precision only
- If the prompt is unclear, resolve ambiguity using best judgment and note assumptions implicitly

INPUT:
[PROMPT TO EVALUATE]
```

## Friction Remover Prompt
```text
<role> You are a Prompt Logic Architect.</role> 
<task> Analyze the user's intent below and rewrite it into a high-performance prompt using the 'Context-Task-Constraint' framework. </task>
<rules>
Identify what the user forgot to mention (tone, audience, or length).
Add a 'Negative Constraint' (what the AI should NOT do).
Keep the output clean and copy-paste ready.
</rules>
[PROMPT TO EVALUATE]
```
## Prompt Evaluation 
Evaluate the quality of the prompt I provide and give practical, structured feedback to improve it.
```text
INPUT Paste the prompt to evaluate below: [PASTE PROMPT HERE]

EVALUATION CRITERIA Assess the prompt against these dimensions: - Clarity — Is it easy to understand and unambiguous?
- Completeness — Does it include enough context, constraints, and success criteria to get the intended output?
- Specificity — Are the instructions precise and actionable (not vague or overly broad)?
- Risk of misinterpretation — Where might a model misunderstand, make assumptions, or go off-topic?
- Style/tone/format alignment — Does it specify the desired voice, formatting, and level of detail?
- Actionability — Could a model produce a usable answer immediately? What’s missing if not?

OUTPUT FORMAT Return your evaluation using exactly these sections:
- Strengths: bullet list
- Weaknesses: bullet list
- Recommendations: numbered, step-by-step improvements (most impactful first)
- Overall score (1–10): include 2–4 sentences of justification
- Optimized rewrite (optional): provide a revised version of the prompt GUIDELINES
- Be direct and candid.
- Prefer concrete fixes (e.g., “add target audience,” “define output schema,” “add examples,” “set constraints”) over generic advice.
- If key information is missing, explicitly list what to add and provide reasonable default assumptions the author could adopt.
- Do not answer the prompt’s subject matter; only evaluate and improve the prompt itself.
```

## Meta Prompt to Make Replies Better
Run this prompt first before asking your question
```text
Whenever I ask a question, do the following before answering:
1. Rewrite my question into the best possible version of the question an expert would ask.
2. If my question is ambiguous, STOP and ask up to 2-3 clarifying questions before answering the optimized final prompt with full context and requirement.
3. When answering, For any multi-step explanation, include an ASCII flowchart diagram with boxes and arrows.

If there is a decision point, use a diamond.
If there is no decision point, still use boxes + arrows.
```
## Define the Reasoning Protocol
Run this prompt before asking a question to define how to structure the response logic to your question
```text
REASONING PROTOCOL:
1. Expand first: Generate multiple possibilities before converging
2. Then compress: Synthesize into coherent answer
3. Self-check: Am I stuck (repeating)? Am I scattered (no thread)? Am I grounded (answering the actual question)?
4. If stuck → force 3 new alternatives. If scattered → find one thread. If ungrounded → return to question.
```
