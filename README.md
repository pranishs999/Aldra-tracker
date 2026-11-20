# ALDRA

**Adaptive Lightweight Domain-based Routing Architecture**

ALDRA is an experimental lightweight domain-prediction system. The current development scope is limited to classifying a natural-language query into one of four domains and returning the predicted domain with its confidence.

## Current scope

- Mathematics
- Science
- Computer Science
- General (fallback)

**Current output:** JSON containing `domain` and `confidence`.

**Not in the current eight-phase build:** cost/resource optimization, expert-model selection, and LLM routing. These are later development stages.

## Experimental classifier target

- TF-IDF: `max_features=320`, `ngram_range=(1, 2)`, `sublinear_tf=True`
- MLP: `320 → 128 → 64 → 4`
- Target trainable parameters: approximately 49,604 (verify against the implemented architecture)

## Development phases

1. Project Foundation
2. Dataset Engineering
3. Text Preprocessing
4. Feature Extraction
5. Classifier Development
6. Model Training
7. Testing and Evaluation
8. Prediction Interface

Training and testing workflows must report their progress, metrics, and important operations visibly.

## Repository structure

```text
ALDRA/
├── aldra/
│   ├── preprocessing/
│   ├── features/
│   ├── models/
│   └── prediction/
├── datasets/
│   ├── raw/
│   └── processed/
├── training/
├── experiments/
├── tests/
├── notebooks/
├── examples/
├── docs/
├── .gitignore
└── README.md
```

## Development principles

- Keep domain prediction independent from downstream model inference.
- Fit the vectorizer on training data only; transform validation and test data with that fitted vectorizer.
- Keep a held-out test set for final evaluation.
- Do not present illustrative confidence values as measured results.
- Preserve experiment configurations and evaluation results.
- Do not add routing or optimization to the current prediction-only milestone.
