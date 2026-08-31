# Prompt Engineering

Prompt engineering is the practice of writing instructions and context so a generative model produces useful, consistent, and safe outputs. A good prompt reduces ambiguity and gives the model enough information to complete the task.

## Prompt Structure

A strong prompt often includes:

- Role: what perspective the model should take.
- Task: what the model must do.
- Context: the facts, documents, data, or examples to use.
- Constraints: rules, tone, format, limits, and forbidden behavior.
- Output format: markdown, JSON, table, checklist, or plain text.
- Evaluation hints: what a good answer should optimize for.

## Example Prompt

```text
You are an AI tutor for beginner software engineers.
Explain vector embeddings in simple language.
Use one analogy, one short technical definition, and one practical example.
Keep the answer under 200 words.
Do not mention topics outside embeddings and search.
```

## Prompting Techniques

- Be specific about the outcome.
- Provide examples when format matters.
- Ask for structured output when software will parse the result.
- Break complex tasks into smaller steps.
- Tell the model what sources or context it is allowed to use.
- Ask the model to state uncertainty when evidence is missing.

## Common Mistakes

- Asking broad questions without context.
- Mixing too many unrelated tasks in one prompt.
- Expecting exact facts without providing sources.
- Requesting JSON but not defining a schema.
- Forgetting edge cases and failure behavior.

## Prompt Quality Checklist

Before using a prompt in production, check:

- Does it define the user goal?
- Does it include the required context?
- Does it specify the output format?
- Does it handle missing information?
- Does it avoid asking for unsupported claims?
- Has it been tested on realistic examples?

## Learning Goal

Learners should be able to design prompts that are clear, testable, structured, and aligned with the user's task.

