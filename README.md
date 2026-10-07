# Introduction to Machine Learning: Logistic Regression

A model is only worth what it does on data it has never seen. This repository builds your first classifier around that idea: separating what the model may look at from what it predicts, holding data back to measure it honestly, setting the score it has to beat, and catching the features that quietly give the answer away.

The model is **logistic regression**, the standard first classifier, which turns a set of measurements into a probability. Notebooks 01 to 05 work on the Palmer penguins dataset, around one main question: **can body measurements tell a penguin's sex**, which takes more than a tape measure to determine? Notebook 04 also predicts the species, a problem with three classes. Notebook 06 applies the whole workflow to a new problem, predicting who survived the sinking of the Titanic.

```
01_what_is_machine_learning         features, target, and what a model is for
        |                           (the penguins without a recorded sex)
        v
02_split_and_baseline               the score to beat, measured fairly
        |                           (a test set, two baselines, a memorizer)
        v
03_how_logistic_regression_works    one measurement, one probability
        |                           (the sigmoid and the decision boundary)
        v
04_logistic_regression_sklearn      several measurements, three species
        |                           (scaled coefficients, one-hot encoding)
        v
05_leakage                          features that know the answer
        |                           (test leakage and target leakage)
        v
06_titanic_exercise                 optional: all of it, on a new dataset
                                    (the Titanic passenger list)
```

Both datasets ship in `data/`, so every notebook runs on its own and offline.

## Learning Objectives

By the end of this repository, you should be able to:

**The workflow (01, 02):**

- Separate a table into features and target, decide whether the target makes a classification or a regression problem, and identify a feature that would not be known at the moment of prediction.
- Split data into training and test sets with a fixed seed and stratification, build a majority-class and a one-rule baseline, and measure every model against them with accuracy.
- Identify from the gap between training and test accuracy when a model has memorized its training data instead of generalizing.

**The model (03, 04):**

- Fit a logistic regression with scikit-learn, on one feature and on several, for two classes and for three, and read its predicted probabilities, coefficients and decision boundary.

**Doing it honestly (05):**

- Detect test leakage and target leakage in a workflow, and remove them.

**On a new dataset (06, optional):**

- Build a classifier end to end on a new dataset, compare it honestly with a majority-class and a domain-knowledge baseline, and keep leaking columns out of it.

## Learning Path

**Scope** marks the core path every student is expected to complete. Optional lessons stay in the repository and are worth returning to, but the day does not depend on them. **Units** are indicative pacing, where one unit is 45 minutes.

| File / Folder | Description | Scope | Units |
| --- | --- | --- | --- |
| [**1 - What Is Machine Learning?**](01_what_is_machine_learning.ipynb) | Rules written against rules learned, labeled and unlabeled penguins, features and target, classification or regression, which columns may be features, and why generalization is the goal. | Core | 1.5 |
| [**2 - Split and Baseline**](02_split_and_baseline.ipynb) | A stratified train/test split, accuracy, a majority-class baseline, a memorizer that scores 100% and learns nothing, and a body-mass threshold chosen on the training set only. | Core | 2 |
| [**3 - How Logistic Regression Works**](03_how_logistic_regression_works.ipynb) | One measurement, one probability: fit Adelie body mass against sex, draw the sigmoid, read the coefficients, and find the decision boundary. | Core | 1.5 |
| [**4 - Logistic Regression with scikit-learn**](04_logistic_regression_sklearn.ipynb) | All four measurements at once, reading coefficients on scaled features, one-hot encoding the species, and predicting the species itself as a problem with three classes. | Core | 1.5 |
| [**5 - Leakage**](05_leakage.ipynb) | Test leakage, shown by features of pure noise that look predictive once the test set helped choose them, and target leakage, a group average quietly computed from the answer itself. | Core | 1.5 |
| [**6 - Titanic Exercise**](06_titanic_exercise.ipynb) | The whole workflow on a new dataset, step by step: split, explore the training set, set two baselines, find the columns that leak the answer, train, and see what the leak would have done. | Optional | 1.25 |

### Additional Folders and Files

| File / Folder | Description |
|---|---|
| [**Data**](data/) | `penguins.csv` for notebooks 01 to 05, `titanic.csv` for notebook 06. |
| [**Solutions**](solutions/) | Reference solutions for every notebook. |
| [**pyproject.toml**](pyproject.toml) | Project configuration and dependencies. |
| [**uv.lock**](uv.lock) | Dependency lock file. |

## Setup

> [!NOTE]
> Throughout these steps, text in angle brackets like `<repo-name>` is a **placeholder**. Replace it, including the `< >` brackets, with your own value. For example, `cd <repo-name>` becomes `cd amle-ml-intro-logistic-reg`.

### 1. Create the Repository from the Template

Click **Use this template** on GitHub.

When creating the repository:

- Set yourself as the **Owner**
- Choose a repository name
- Disable **Include all branches**
- Click **Create repository**

> [!IMPORTANT]
> If you are working in pairs or groups, only **one person** should complete this step.

---

### 2. Add Collaborators (Pairs/Groups Only)

If working with teammates:

1. Open the repository on GitHub
2. Go to **Settings → Collaborators**
3. Add your teammates as collaborators
4. Share the repository link with your team

Teammates should accept the invitation before continuing.

---

### 3. Clone the Repository

Copy the SSH URL from the **Code** button on GitHub, then run:

```bash
git clone <copied-ssh-url>
```

The copied SSH URL will look like `git@github.com:<your-username>/<repo-name>.git`.

---

### 4. Move into the Project Folder and Install Dependencies

This installs all dependencies and creates a virtual environment in `.venv/`.

```bash
cd <repo-name>
uv sync
```

---

### 5. Open the Notebook

> [!NOTE]
> Make sure you open VS Code from the project root so it automatically detects the environment created by `uv sync`.

Launch VS Code in the project root folder:

```bash
code .
```

Then open `01_what_is_machine_learning.ipynb`, selecting the Python environment created by `uv sync` as the kernel. Work through the notebooks in order. Notebooks 01 to 05 are the core path, and 06 is optional practice on a new dataset.

## References & Further Reading

- [**scikit-learn: Logistic regression**](https://scikit-learn.org/stable/modules/linear_model.html#logistic-regression): The model and its options, in the official user guide.
- [**scikit-learn: Common pitfalls**](https://scikit-learn.org/stable/common_pitfalls.html): Data leakage and inconsistent preprocessing, with worked examples, the subject of notebook 05.
- [**Google Machine Learning Crash Course: Logistic regression**](https://developers.google.com/machine-learning/crash-course/logistic-regression): The sigmoid and the log loss, with interactive exercises.
- [**StatQuest: Logistic Regression**](https://www.youtube.com/watch?v=yIYKR4sgzI8): The model explained visually in under ten minutes.
- [**Kaufman et al., Leakage in Data Mining**](https://dl.acm.org/doi/10.1145/2382577.2382579): The paper that named and classified leakage, with real competition examples.
- [**palmerpenguins**](https://allisonhorst.github.io/palmerpenguins/): The dataset behind notebooks 01 to 05, collected by Dr Kristen Gorman at Palmer Station, Antarctica.
- [**OpenML: Titanic**](https://www.openml.org/d/40945): The full passenger list used in notebook 06, including the columns the better-known Kaggle version leaves out.
