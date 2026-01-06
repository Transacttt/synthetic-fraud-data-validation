# synthetic-fraud-data-validation
Privacy-preserving synthetic transaction data for fraud model development and validation under regulatory constraints.

# **Privacy-Preserving Synthetic Financial Transactions for Fraud Modelling**
Overview

This project implements an end-to-end synthetic data generation pipeline for financial transaction data, designed under realistic regulatory, privacy, and modelling constraints.

Rather than producing visually similar “fake data”, the objective is to generate synthetic transactions that preserve statistical structure, correlations, and fraud decision boundaries, while avoiding memorisation of real customer records.

The work reflects real-world constraints faced by banks, fintechs, and fraud teams, where raw transaction data cannot be freely reused or shared due to GDPR, compliance, and internal risk controls.

🎯 Use Case & Risk Definition (Step 0)

Primary use case

Offline development, evaluation, and stress-testing of fraud detection models when access to real transaction data is restricted

Key risks explicitly addressed

Privacy leakage via near-duplicate synthetic rows

Distortion of extreme class imbalance (fraud vs non-fraud)

Loss of decision-boundary signal critical for downstream classifiers

Overfitting or trivial memorisation of rare fraud patterns

These risks directly inform the design and validation choices in the pipeline.

📊 Dataset Characteristics (Step 1)

Credit card transaction dataset

~280,000 rows

Severe class imbalance (~0.17% fraud)

All features numeric (PCA-transformed + Amount + Time)

High sensitivity to naïve oversampling or perturbation

Key implication:
Synthetic data must preserve structure and signal, not just marginal distributions.

🧠 Design Philosophy

This project is decision-driven, not generator-driven.

Instead of defaulting to black-box generative models, the pipeline prioritises:

Interpretability and control

Explicit handling of fraud as a first-class constraint

Validation via downstream utility, not visual similarity alone

Clear trade-offs between fidelity, privacy, and modelling usefulness

This mirrors how synthetic data is evaluated in regulated production environments.

⚙️ Synthetic Data Generation Pipeline

High-level stages:

Schema & boundary analysis

Feature ranges, distributions, and constraints explicitly examined

Target-aware handling

Fraud class treated separately to avoid boundary erosion

Correlation preservation

Multivariate structure maintained across features

Anti-memorisation intent

Generation designed to avoid collapsing onto real samples

The focus is structural realism, not perfect replication.

✅ Validation Strategy

Validation is multi-layered and utility-focused.

1. Distributional Validation

Feature-level distribution comparisons

Preservation of fraud/non-fraud proportions

2. Structural Validation

Correlation matrix comparisons

Feature interaction sanity checks

3. Downstream Task Validation (Critical)

Models are trained and evaluated on:

Real data

Synthetic data

Performance is compared to assess:

Signal retention

Directional consistency

Decision-boundary degradation risk

This directly answers the practical question:
“Can this synthetic data actually be used for fraud modelling?”

📈 Key Findings

Synthetic data preserves fraud signal directionality

Extreme class imbalance remains realistic

No evidence of trivial memorisation

Performance differences are explainable and bounded

The synthetic dataset is therefore fit for model development, evaluation, and stress-testing, not just exploratory analysis.

⚠️ Limitations & Trade-offs

Not designed for unrestricted public data release without further privacy auditing

Does not attempt perfect distributional matching at the expense of decision signal

Advanced generative models (GANs, diffusion) intentionally excluded for control and interpretability

These are explicit design decisions, not omissions.

🔮 Future Extensions

Explicit privacy metrics (distance-based leakage tests)

Stress-testing under distribution shift

Conditional generation by fraud subtype

Extension to multi-table or temporal transaction data

🧩 Why This Project Matters

This project reflects real industry constraints, including:

Regulatory limits on data usage

Privacy and leakage risk

Model validation requirements

Decision-boundary preservation

It is designed from the perspective of deploying ML in production, not completing a toy exercise.

🏷️ Portfolio Positioning

Project status:
✔ Flagship-level applied ML / data engineering project

Relevant roles:

Data Scientist (Fraud / Risk)

Machine Learning Engineer

Synthetic Data / Privacy-Aware ML

Applied Research / Modelling

Final note

All implementation details, validation steps, and design decisions are fully documented in the accompanying notebook.

