# Code Design

## Continuous Text vs. Chapters
* **Continuous Text**: Written from start to finish without breaks ➡️ Hard to follow, difficult to find specific information.
* **Chapters**: Divided into sections and paragraphs ➡️ Easy to grasp the overall structure, allows extracting only what's needed.

Code is writing. Instead of putting everything into one massive file, the key is to **divide it into modules based on roles and functions**.

---

## Jupyter Notebook vs. `.py` Modules
* **Jupyter Notebook (`.ipynb`)**: Great for quick experiments and data visualization. However, as code grows, execution order gets tangled and reuse becomes difficult.
* **Python Modules (`.py`)**: Neatly organized into functions/classes. Easy to `import` into other files and suitable for real-world deployment.

!!! example "Example: Data Preprocessing"

=== "Jupyter Notebook (Experimental)"

    ```python
    # Cell 1
    import pandas as pd
    df = pd.read_csv('data.csv')
    ```
    ```python
    # Cell 2
    df = df.dropna()
    df['price'] = df['price'] * 1.1
    ```

=== ".py Module (Reusable/Deployment)"

    ```python
    # data_processor.py
    import pandas as pd

    def clean_and_process_data(filepath: str) -> pd.DataFrame:
        """Loads data, removes missing values, and adjusts prices."""
        df = pd.read_csv(filepath)
        df = df.dropna()
        df['price'] = df['price'] * 1.1
        return df
    ```

---

## Monolithic Script vs. Modular Code
* **Monolithic Script**: Code written sequentially from top to bottom in a single file. Hard to predict where errors will occur when making changes.
* **Modular Code**: Code separated into functional units (data processing, model training, etc.) like Lego blocks. When issues arise, only the relevant block needs fixing or replacing.

!!! example "Example: Load → Preprocess → Visualize"
    **All-in-one file** vs. **Divided structure (`config` + `src` + `utils`)**.

=== "Monolithic Script"

    ```python
    # analysis.py: Reading, preprocessing, and plotting mixed in one file
    import pandas as pd
    import matplotlib.pyplot as plt

    df = pd.read_csv("data/sample.csv")
    df = df.dropna()
    df["value"] = df["value"].clip(lower=0)

    plt.figure()
    df["value"].hist(bins=20)
    plt.tight_layout()
    plt.savefig("outputs/dist.png")
    ```

=== "Modular + Folder Structure"

    ```text
    my_project/
    ├── config.json           # Paths, column names, etc.
    ├── data/
    │   └── sample.csv
    ├── outputs/              # Saved figures (can be gitignored)
    └── src/
        ├── main.py           # Connects the pipeline
        ├── data_io.py        # Data loading
        ├── preprocess.py     # Preprocessing
        └── utils/
            └── viz.py        # Visualization
    ```

    ```json title="config.json"
    {
      "paths": { "csv": "data/sample.csv", "figure": "outputs/dist.png" },
      "plot": { "column": "value", "bins": 20 }
    }
    ```

    ```python title="main.py"
    # src/main.py: Reads config and calls modules step-by-step
    import json
    from pathlib import Path
    from data_io import load_csv
    from preprocess import clean
    from utils.viz import plot_hist

    cfg = json.loads(Path("config.json").read_text(encoding="utf-8"))
    df = load_csv(cfg["paths"]["csv"])
    df = clean(df)
    plot_hist(df, column=cfg["plot"]["column"], bins=cfg["plot"]["bins"], out_path=cfg["paths"]["figure"])
    ```

---

## Benefits of Structuring
**Structuring (modularizing) code** into meaningful units like directories, classes, and functions offers several advantages:

1. **Improved Readability**: Easier for your future self and colleagues to read and understand.
2. **Easier Collaboration**: Divided files reduce Git conflicts when multiple people work simultaneously.
3. **Maintainability**: Easier to locate bugs and add new features without breaking existing code.
4. **Reusability**: Well-designed modules can be easily reused in other projects.
5. **AI Coding Optimization**: LLM coding agents (like Claude or Antigravity) can better grasp the context and suggest much better code.
