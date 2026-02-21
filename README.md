# genaiPrompts

## Use the 80/20 principle to learn faster
```text
I want to learn about (insert topic). 
Determine and share the 20% of the topic's lessons that are most crucial to understanding the remaining 80%
```

## Clear Task Breakdown
```text
Break this task into the smallest possible steps.
Order them so I can finish fast.
Skip anything optional.
Task: [paste task]
```

## Chain of Thought
```text
You are an expert at (INSERT FIELD) with over 11 years of experience.
Advise me on (YOUR QUESTIONS).
Let's think step by step.
```

## The Fast Decision Helper
```text
I need to decide between these options.
List pros and cons briefly.
Then tell me which option makes sense and why.
Options: [list options]
```

## The Problem Framer
```text
Help me explain this problem clearly at work.
Structure it as:
1. What is happening
2. Why it matters
3. What I suggest we do
Problem: [describe issue]
```

## Meta Prompt to Make Replies Better
```text
Whenever I ask a question, do the following before answering:
1. Rewrite my question into the best possible version of the question an expert would ask.
2. If my question is ambiguous, STOP and ask up to 2-3 clarifying questions before answering the optimized final prompt with full context and requirement.
3. When answering, For any multi-step explanation, include an ASCII flowchart diagram with boxes and arrows.

If there is a decision point, use a diamond.
If there is no decision point, still use boxes + arrows.
```

## Cognitive Mesh Protocol
```text
REASONING PROTOCOL:
1. Expand first: Generate multiple possibilities before converging
2. Then compress: Synthesize into coherent answer
3. Self-check: Am I stuck (repeating)? Am I scattered (no thread)? Am I grounded (answering the actual question)?
4. If stuck → force 3 new alternatives. If scattered → find one thread. If ungrounded → return to question.
5. Analyze prompt and select the ideal Macro for response
```

## Example Market Analysis
```text
Analyze current market data and identify 3 emerging niches with high profit potential and low saturation in the sector indicated in INPUT.

Do not hallucinate. 
Use only verifiable data from 2024-2025.

OUTPUT REQUIREMENTS:
1. Detailed SWOT Analysis.
2. Updated research data (2024–2025).
3. Indication of creative opportunities exploitable in 2026.
```