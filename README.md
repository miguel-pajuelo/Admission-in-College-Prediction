# College Admission Prediction

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)](https://python.org)
[![Scikit-learn](https://img.shields.io/badge/Scikit--learn-F7931E?style=flat&logo=scikit-learn&logoColor=white)](https://scikit-learn.org)
[![Jupyter](https://img.shields.io/badge/Jupyter-notebook-F37626?style=flat&logo=jupyter&logoColor=white)](https://jupyter.org)

Supervised and unsupervised machine learning analysis of a **college admission dataset**. The project estimates an applicant's `Chance of Admit` from academic and profile variables, compares several regression models, and explores the structure of the applicants with PCA and K-Means clustering.

> **Disclaimer:** This is an academic machine learning project, not an official admissions tool. Its predictions should not be used to make real university admission decisions.

---

## What it does

1. **Data inspection and cleaning** — loads 500 applicant records, removes the serial-number field from the predictors, and standardizes the target column name.
2. **Exploratory data analysis** — visualizes the target distribution and correlation structure between applicant characteristics and admission probability.
3. **Preprocessing** — splits the data into 80% training and 20% test sets, applying `StandardScaler` where scaling is required.
4. **Unsupervised analysis** — uses PCA to identify the main directions of variation and K-Means to group applicants with similar profiles.
5. **Supervised learning** — tunes and compares four regression models:
   - K-Nearest Neighbors Regressor
   - Linear Regression
   - Random Forest Regressor
   - Gradient Boosting Regressor
6. **Model comparison** — evaluates performance using R², MAE, and RMSE, with hyperparameters selected through GridSearchCV.

---

## Dataset

The dataset contains **500 applicant profiles** and the following variables:

- `GRE Score`
- `TOEFL Score`
- `University Rating`
- `SOP` — Statement of Purpose strength
- `LOR` — Letter of Recommendation strength
- `CGPA` — Cumulative Grade Point Average
- `Research` — research-experience indicator
- `Chance of Admit` — target variable, expressed as an estimated probability

The identifier column `Serial No.` is used as the dataframe index and is not used as a predictive feature.

---

## Results

The final comparison on the held-out test set is:

| Model | R² ↑ | MAE ↓ | RMSE ↓ |
|---|---:|---:|---:|
| **Linear Regression** | **0.8188** | **0.0427** | **0.0609** |
| Random Forest Regressor | 0.8122 | 0.0439 | 0.0620 |
| Gradient Boosting Regressor | 0.7947 | 0.0440 | 0.0648 |
| KNN Regression | 0.7830 | 0.0476 | 0.0666 |

**Linear Regression** achieves the strongest test performance in this experiment. This suggests that, for this dataset, the relationship between the main applicant variables and admission probability is largely captured by a linear model.

In the unsupervised analysis, PCA highlights the relevance of academic variables such as `GRE Score`, `TOEFL Score`, and `CGPA`. K-Means identifies **2 applicant clusters** as the best option according to the silhouette score.

---

## Stack

- **Python** — NumPy, Pandas
- **Scikit-learn** — preprocessing, regression models, GridSearchCV, PCA, K-Means, metrics
- **Matplotlib + Seaborn** — exploratory and model-evaluation visualizations

---

## How to run

Install the required packages:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

Place `admission_predict.csv` in the same folder as the notebook, then run:

```bash
jupyter notebook admission_prediction.ipynb
```

---

## Structure

```text
├── admission_prediction.ipynb   # Main analysis notebook
├── admission_predict.csv        # Applicant dataset
└── README.md
```
