# Generate Charts
A set of prompts to aid in analyzing datasets and generating useful graphs that tell a story about the data. It also includes a prompt to challenge the system on the quality of what it created.

## Initial Data Analysis Prompt
```text
I uploaded a dataset. Your task is to produce decision-grade visualizations and the code used to generate them.

Work in this order:

1. Data audit
Inspect the dataset and produce exactly 10 bullets covering:
- columns and inferred meanings
- data types
- missing values
- duplicates
- invalid or suspicious values
- category cardinality / odd labels
- time fields and granularity
- likely joins or derived fields
- data quality risks
- limitations that could distort interpretation

2. Decision questions
Identify the 5 most important business or analytical questions this dataset can answer.

3. Chart options
For each of those 5 questions, propose 1 chart:
- chart type
- exact fields used
- required aggregation or transformation
- why this chart is the right choice
- what decision it informs

4. Select and build
Choose the best 3 charts based on decision value, clarity, and data reliability.
Create those 3 charts with these rules:
- clean design
- minimal nonessential color
- clear title
- labeled axes with units
- readable ticks and legends
- no chartjunk
- annotate peaks, drops, outliers, and breakpoints when relevant
- include a 1-sentence takeaway under each chart

5. Validation
List 5 concrete checks you performed to verify the charts are accurate.
Examples: aggregation correctness, date parsing sanity, denominator checks, duplicate handling, missing-value impact.

6. Reproducibility
Provide the exact code used to generate the final 3 charts in Python using matplotlib.

Behavior rules:
- Do not invent fields, units, or meanings.
- State assumptions explicitly.
- If a critical ambiguity blocks correct analysis, ask only the minimum clarifying question and stop.
- Prefer simple charts unless additional complexity materially improves decision quality.

Output format:
A. 10-bullet data audit
B. 5 decision questions
C. 5 proposed chart options
D. 3 final charts with 1-sentence takeaway each
E. 5 validation checks
F. Reproducible Python/matplotlib code
```
## Ask for 3 chart drafts & critique
```text
Generate 3 materially different chart variants for the same analytical question.

For each variant, provide:
- chart type
- why this design might work
- main risk or weakness
- what audience it best serves

Then critique all 3 like a senior data visualization lead using these criteria:
- decision clarity
- accuracy
- interpretability
- visual efficiency
- risk of misleading the viewer
- accessibility / readability

Choose 1 winner.
Explain why it wins and why the others lose.
If none are good enough, say so and propose a better 4th option.
```
## Build a chart ladder
```text
Start with the simplest chart that could answer the decision question.

Then evaluate whether it succeeds.
If it does not, add exactly one layer of complexity at a time and justify each addition.

Possible complexity layers include:
- segmentation
- faceting
- trend lines
- annotations
- normalization
- uncertainty bands
- secondary encoding

After each step, state:
- what was added
- why it was necessary
- what confusion or failure it fixed
- whether further complexity is still justified

Stop at the minimum complexity required for a decision-grade chart.
```
## Use it as a data detective before it’s a designer
```text
Before evaluating this chart aesthetically, act as a data detective.

List all assumptions required to interpret the chart correctly, including assumptions about:
- data completeness
- sampling
- time windows
- aggregation logic
- category definitions
- units
- baselines
- causality vs correlation
- missing or excluded segments

For each assumption, label it:
- likely true
- uncertain
- likely false

Then identify:
- the 3 assumptions most likely to break the takeaway
- how each could mislead the viewer
- what additional check or data would validate it
```
## Force reproducibility
```text
Make this chart fully reproducible from the raw file.

Output:
1. exact transformation steps in order
2. field mappings used
3. filters applied
4. aggregation logic
5. sorting logic
6. handling of nulls, duplicates, and outliers
7. derived columns or calculations
8. final chart-generation code

Requirements:
- no skipped steps
- no hidden assumptions
- use deterministic code
- include imports
- use Python and matplotlib
- ensure another analyst could recreate the same result from the raw file without guessing
```
## Make it fight itself
```text
Challenge the chart’s main takeaway.

First, state the primary takeaway in 1 sentence.
Then argue against it by generating the strongest alternative explanations that also fit the data.

For each alternative explanation, provide:
- why it is plausible
- what assumptions it depends on
- what evidence would support or weaken it

Then conclude with:
- the most defensible interpretation
- the confidence level
- what additional data would most reduce uncertainty
```
