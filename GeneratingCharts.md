# Generate Charts
A set of prompts to aid in analyzing datasets and generating useful graphs that tell a story about the data. It also includes a prompt to challenge the system on the quality of what it created.

## Initial Data Analysis Prompt
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
## Ask for 3 chart drafts & critique
```text
Generate 3 chart variants, then critique each like a data viz lead and choose the winner.
```
## Build a chart ladder
```text
Make the simplest chart possible. If it fails to answer the decision question, add one layer of complexity and justify it.
```
## Use it as a data detective before it’s a designer
```text
List all assumptions required to interpret this chart correctly. Flag the ones likely to be false.
```
## Force reproducibility
```text
Output the exact transform steps and code so the chart is reproducible from raw file
```
## Make it fight itself
```text
Argue against your own takeaway. What alternative explanations fit the data?
```
