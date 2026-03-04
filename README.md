# Useful Prompts

[GeneratingCharts.md](https://github.com/johrenberger/genaiPrompts/blob/main/GeneratingCharts.md) - Prompts for analyzing data and generating visualization of the data
IdeaDestroyer.md - Prompt for evaluating an idea you have and providing feedback on its weakness. Useful for challenging the quality of your ideas and iterating to improve it.
IncidentResponse.md - Prompt for generating Information Security quality incident response documentation
PromptAnalytics.md - Prompts to improve the quality of what you pass to your Gen AI chat to improve the organization and output from Gen AI.


Many of the prompts are prefixed with "You are an expert at [INSERT FIELD] with over 11 years of experience." This helps frame context for the Gen AI tool by defining a level of focus and expertise. While not necessary for every request, it is a healthy habit to optimize quality and response.


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

## Evaluate Logic of Response By AI
```text
Don't give me an answer yet.

First:
1. Tell me what assumptions you're making about my situation
2. Tell me what information would change your answer significantly
3. Tell me what the most common mistake is when people ask 
   you this question

Then ask me the 2 questions that would make your answer 
actually useful for my specific situation.

Only after I answer those — write the output.

My request: [paste your actual request here]
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

