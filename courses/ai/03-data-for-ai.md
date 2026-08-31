# Data for AI

AI quality depends heavily on data quality. Even powerful models fail when the data is incomplete, biased, inconsistent, stale, or poorly matched to the task.

## Types of Data

AI systems can use many kinds of data:

- Structured data: rows, columns, transactions, events, and metrics.
- Unstructured text: documents, tickets, emails, chats, policies, and logs.
- Images and video: visual input for inspection, recognition, or generation.
- Audio: speech, calls, meetings, and sound events.
- Behavioral data: clicks, searches, purchases, ratings, and sessions.
- Knowledge sources: manuals, product docs, FAQs, code, and support history.

## Data Quality Checklist

Useful AI data should be:

- Relevant to the real task.
- Representative of real users and edge cases.
- Clean enough to avoid misleading patterns.
- Labeled consistently when labels are required.
- Split correctly into training, validation, and test sets.
- Documented so future teams understand its source and limits.

## Training, Validation, and Test Sets

For machine learning, data is commonly split into three sets:

- Training set: used to fit the model.
- Validation set: used to tune model choices.
- Test set: used only for final quality checks.

The test set should represent real future use. If the model sees test examples during training or tuning, the evaluation becomes unreliable. This problem is called data leakage.

## Bias and Coverage

Bias appears when the data overrepresents some users, behaviors, regions, languages, or cases while underrepresenting others. Coverage matters because AI systems often fail on rare but important examples. Good datasets include normal cases, edge cases, and known failure cases.

## Data Documentation

Every important dataset should have a short data card:

- What is the source?
- Who owns it?
- What does each field mean?
- What time period does it cover?
- What cleaning was applied?
- What sensitive data is present?
- What should the dataset not be used for?

## Learning Goal

Learners should understand that data is not just an input file. It is the foundation of AI quality, reliability, and trust.

