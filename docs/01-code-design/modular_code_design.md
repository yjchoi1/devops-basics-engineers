# Modular Code Design

Good code is **easy to read, easy to modify, and easy to test**.
Modular design is a set of principles aimed at achieving these three goals simultaneously.

---

## Single Responsibility Principle (SRP)

> "Functions should do one thing. They should do it well. They should do it only." (*Clean Code*, Robert C. Martin)

If a function handles data loading, preprocessing, model training, and visualization all at once, changing one part will affect the others.
By dividing roles, you narrow the scope of changes and make it obvious where to look when issues arise.

```python
# Bad
def run():
    data = pd.read_csv(...)   # Load
    data = data.dropna()      # Preprocess
    model.fit(data)           # Train
    plt.plot(...)             # Visualize

# Good
data  = load_data(path)
data  = preprocess(data)
model = train(model, data)
plot_results(model)
```

---

## Separation of Configuration from Logic

> "The twelve-factor app stores config in the environment." ([12-Factor App](https://12factor.net/config), Factor III)

If you hardcode **frequently changing values** like experimental conditions, hyperparameters, or file paths, you have to open the logic code every time you want to change them.
By separating configurations into distinct files (`.json`, `.yaml`), you can swap inputs without touching the code.

```text
project/
├── config.json      ← Changing values (conditions, paths, hyperparameters)
└── src/
    ├── train.py     ← Unchanging logic
    └── evaluate.py
```

Config tools: `json` or `argparse` for simple cases, [Hydra](https://hydra.cc) (`.yaml` + CLI override) for large-scale experiments.

---

## Modularity: High Cohesion, Low Coupling

> "Maximize cohesion and minimize coupling." (Larry Constantine, *Structured Design*)

- **High Cohesion**: Group related code together in the same module (file/class).
- **Low Coupling**: Modules should know as little about each other as possible. They should communicate only through interfaces (function signatures).

With low coupling, you can replace one module without breaking the rest of the system.

```text
dataset.py   → Handles only data loading/preprocessing
model.py     → Handles only model architecture
train.py     → Handles only the training loop (imports and assembles dataset and model)
evaluate.py  → Handles only evaluation
```

---

## Test-Driven Development (TDD)

> "Write new code only if an automated test has failed." (*Test-Driven Development: By Example*, Kent Beck)

Modules must be well-separated to test individual units independently.
Modularity and TDD enforce each other. If code is hard to test, it's a sign that the design needs to be revisited.

```text
tests/
├── test_dataset.py    # Tests load_data() in isolation
├── test_model.py      # Tests model output shapes
└── test_train.py      # Smoke test for the training loop
```

---

## Summary

| Principle | Key Question | Source |
|---|---|---|
| SRP | Does this function do exactly one thing? | *Clean Code* |
| Separate Config | Do I have to open the code to change a value? | *12-Factor App* |
| High Cohesion / Low Coupling | Can I replace this module without breaking the rest? | Larry Constantine |
| TDD | Can I test this function independently? | Kent Beck |
