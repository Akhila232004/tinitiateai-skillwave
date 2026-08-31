# Problem Framing for AI

Good AI projects begin with the problem, not with the model. A clear problem statement prevents wasted effort, helps choose the right technique, and gives the team a way to measure progress.

## Start With the User Outcome

Describe what the user or business should be able to do after the AI feature exists.

Strong examples:

- Support agents should find the right answer faster.
- Students should receive personalized practice questions.
- Analysts should summarize long reports with citations.
- Operators should detect unusual system behavior earlier.

Weak examples:

- Add AI to the product.
- Use a chatbot.
- Train a model.

The weak examples describe technology choices, not outcomes.

## Choose the Task Type

Most AI features fit one or more task types:

- Classification: decide which category an input belongs to.
- Regression: predict a number.
- Ranking: order results by relevance or value.
- Clustering: group similar items without predefined labels.
- Retrieval: find the most relevant documents or records.
- Generation: create content from instructions and context.
- Extraction: pull structured fields from unstructured input.
- Planning: choose steps toward a goal.

## Decide Whether AI Is Needed

AI is not always the right answer. Use simpler software first when rules are stable, data is small, precision must be exact, or the cost of errors is very high. Use AI when there is variability, ambiguity, scale, or natural language that would be hard to handle with fixed rules.

## Define Success Metrics

Success metrics should be chosen before implementation.

- Product metric: time saved, completion rate, conversion, retention, or satisfaction.
- Model metric: accuracy, precision, recall, F1 score, ranking quality, or answer quality.
- Operational metric: latency, cost per request, uptime, and failure rate.
- Safety metric: harmful outputs, privacy incidents, bias reports, or escalation rate.

## Write a Problem Frame

Use this template:

```text
For [target user], we want to [desired outcome].
The AI task is [classification, generation, retrieval, etc.].
The system will use [available data or context].
Success means [measurable result].
The main risks are [privacy, bias, accuracy, cost, safety].
```

## Learning Goal

By the end of this topic, learners should be able to turn an AI idea into a concrete product and engineering plan.

