# Useful Prompts
Many of the prompts are prefixed with "You are an expert at [INSERT FIELD] with over 11 years of experience." This helps frame context for the Gen AI tool by defining a level of focus and expertise.

While not necessary for every request, it is a healthy habit to optimize quality and response.


## Use the 80/20 principle to learn faster
```text
You are an expert at [INSERT FIELD] with over 11 years of experience.
I want to learn about [INSERT TOPIC]. 
Determine and share the 20% of the topic's lessons that are most crucial to understanding the remaining 80%
```

## Clear Task Breakdown
```text
You are an expert at [INSERT FIELD] with over 11 years of experience.
Break this task into the smallest possible steps.
Order them so I can finish fast.
Skip anything optional.
Task: [PASTE TASK]
```

## Chain of Thought
```text
You are an expert at [INSERT FIELD] with over 11 years of experience.
Advise me on [YOUR QUESTIONS].
Let's think step by step.
```

## The Fast Decision Helper
```text
You are an expert at [INSERT FIELD] with over 11 years of experience.
I need to decide between these options.
List pros and cons briefly.
Then tell me which option makes sense and why.
Options: [LIST OPTIONS]
```

## The Problem Framer
```text
You are an expert at [INSERT FIELD] with over 11 years of experience.
Help me explain this problem clearly at work.
Structure it as:
1. What is happening
2. Why it matters
3. What I suggest we do
Problem: [DESCRIBE ISSUE]
```
## Prompt Analytics To Improve Requests
Use these to analyze the original prompt and re-generate for better GenAI engagement 
### Meta Prompt to Make Replies Better
Run this prompt first before asking your question
```text
Whenever I ask a question, do the following before answering:
1. Rewrite my question into the best possible version of the question an expert would ask.
2. If my question is ambiguous, STOP and ask up to 2-3 clarifying questions before answering the optimized final prompt with full context and requirement.
3. When answering, For any multi-step explanation, include an ASCII flowchart diagram with boxes and arrows.

If there is a decision point, use a diamond.
If there is no decision point, still use boxes + arrows.
```
### Define the Reasoning Protocol
Run this prompt before asking a question to define how to structure the response logic to your question
```text
REASONING PROTOCOL:
1. Expand first: Generate multiple possibilities before converging
2. Then compress: Synthesize into coherent answer
3. Self-check: Am I stuck (repeating)? Am I scattered (no thread)? Am I grounded (answering the actual question)?
4. If stuck → force 3 new alternatives. If scattered → find one thread. If ungrounded → return to question.
```
### Friction Remover Prompt
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
## Example Market Analysis
```text
You are an expert at [INSERT FIELD] with over 11 years of experience.
Analyze current market data and identify 3 emerging niches with high profit potential and low saturation in the sector indicated in INPUT.
Do not hallucinate. 
Use only verifiable data from 2024-2025.

OUTPUT REQUIREMENTS:
1. Detailed SWOT Analysis.
2. Updated research data (2024–2025).
3. Indication of creative opportunities exploitable in 2026.
```
## Generate Charts
### Initial Data Analysis Prompt
```text
I uploaded a dataset. Your job is to produce decision-grade visualizations.

First, inspect the dataset and write a 10-bullet data audit:
columns, types, missing values, duplicates, weird categories, time granularity, likely data quality risks
Then propose 5 different chart options that answer the most important decision questions in this data:
for each: chart type, what it shows, why it matters, and the exact fields used

Create the best 3 charts with these rules:
clean design, minimal colors, clear title, labeled axes with units, readable ticks, no clutter
annotate key points (peaks, drops, breakpoints)
include 1 sentence takeaway under each chart

Validation step:
list 5 checks you performed to ensure the charts are accurate
if anything is ambiguous, stop and ask only the minimum clarifying question

Output:
deliver the charts and also provide the code used to generate them in Python (matplotlib) or JavaScript (Plotly), my choice: Python
```
### Ask for 3 chart drafts & critique
```text
Generate 3 chart variants, then critique each like a data viz lead and choose the winner.
```
### Build a chart ladder
```text
Make the simplest chart possible. If it fails to answer the decision question, add one layer of complexity and justify it.
```
### Use it as a data detective before it’s a designer
```text
List all assumptions required to interpret this chart correctly. Flag the ones likely to be false.
```
### Force reproducibility
```text
Output the exact transform steps and code so the chart is reproducible from raw file
```
### Make it fight itself
```text
Argue against your own takeaway. What alternative explanations fit the data?
```
