# Evaluation, Safety, and Ethics

AI systems should be evaluated before users depend on them. Evaluation measures quality, safety, and reliability. It also helps teams improve prompts, retrieval, data, models, and product design.

## Why Evaluation Is Hard

Traditional software often has exact expected outputs. AI outputs can be variable and still be acceptable. This means evaluation may need rubrics, examples, human review, and automated checks.

## Evaluation Methods

- Golden datasets: representative inputs with expected answers.
- Unit tests: small checks for formatting, refusal behavior, or required fields.
- Rubrics: scoring criteria for usefulness, accuracy, completeness, and tone.
- Human review: expert judgment on important outputs.
- A/B tests: product comparison using real user behavior.
- Monitoring: production tracking of quality, cost, latency, and incidents.

## Safety Risks

Common AI risks include:

- Hallucination: confident but incorrect output.
- Bias: unfair behavior across user groups.
- Privacy leaks: exposing personal, confidential, or sensitive data.
- Prompt injection: malicious instructions hidden in user or document content.
- Insecure tool use: calling APIs or actions without proper controls.
- Overreliance: users trusting AI when human review is needed.

## Responsible Design

Responsible AI design includes:

- Clear user expectations.
- Citations or source links when facts matter.
- Uncertainty when evidence is weak.
- Human review for high-impact decisions.
- Data minimization and privacy controls.
- Logs and audit trails.
- Feedback mechanisms for users to report problems.

## Evaluation Checklist

Before launch, ask:

- What are the highest-risk mistakes?
- Do tests cover realistic and adversarial examples?
- Can the system say it does not know?
- Are private data and secrets protected?
- Are tool calls permissioned and logged?
- Is there a rollback or disable plan?

## Learning Goal

Learners should be able to evaluate AI systems beyond accuracy and think about user safety, privacy, trust, and operational risk.

