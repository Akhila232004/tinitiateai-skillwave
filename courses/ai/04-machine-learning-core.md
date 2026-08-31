# Machine Learning Core

Machine learning is a way to build software that learns patterns from examples. Instead of manually writing every rule, developers provide data, choose a model, train it, and evaluate how well it performs.

## The ML Workflow

A typical machine learning workflow looks like this:

1. Define the task and metric.
2. Collect and prepare data.
3. Split data into training, validation, and test sets.
4. Train a baseline model.
5. Improve features, model choice, and parameters.
6. Evaluate on the test set.
7. Deploy and monitor behavior in production.

## Supervised Learning

Supervised learning uses labeled examples. Each training example includes input data and a known correct answer.

Common supervised tasks:

- Classification: predict a class such as approved, rejected, fraud, or not fraud.
- Regression: predict a number such as price, risk score, or delivery time.

Common models:

- Logistic regression.
- Decision trees.
- Random forests.
- Gradient boosted trees.
- Neural networks.

## Unsupervised Learning

Unsupervised learning finds patterns without predefined labels.

Common tasks:

- Clustering similar users, documents, or products.
- Reducing high-dimensional data into a smaller representation.
- Finding unusual records through anomaly detection.

## Reinforcement Learning

Reinforcement learning trains an agent through rewards and penalties. It is useful for decision-making problems where actions affect future states, such as robotics, game playing, resource allocation, or control systems. It is powerful but often harder to apply than supervised learning.

## Overfitting and Generalization

Overfitting happens when a model memorizes training data but performs poorly on new data. Generalization means the model works well on examples it has not seen before. Validation data, regularization, simpler baselines, and realistic tests help detect overfitting.

## Learning Goal

Learners should be able to explain how machine learning systems are trained, evaluated, improved, and used for inference.

