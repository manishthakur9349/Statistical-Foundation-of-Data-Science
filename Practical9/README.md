
# Practical 9: K-Nearest Neighbors (KNN) Classification & Cross-Validation on the Iris Dataset

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** Built-in `sklearn.datasets.load_iris()` (`150` rows, `4` features, `3` species)

## Overview

This practical implements a complete **K-Nearest Neighbors (KNN)** classification workflow on the Iris dataset using **Pandas**, **NumPy**, **Scikit-Learn**, **Matplotlib**, and **Seaborn**. It covers exploratory data analysis (EDA), stratified train-test splitting, leakage-free feature standardization via `Pipeline`, hyperparameter tuning for $K$ (`1` to `20`) using 5-fold stratified cross-validation, and final test-set evaluation using a confusion matrix, classification report, and scatter visualization.

## Workflow & Key Findings

### 1. Exploratory Data Analysis (EDA) & Data Splitting
- **Dataset Summary:** `150` samples across `3` balanced species (`setosa`: `50`, `versicolor`: `50`, `virginica`: `50`) with `0` missing values and `4` numerical features (`sepal length (cm)`, `sepal width (cm)`, `petal length (cm)`, `petal width (cm)`).
- **Train-Test Split:** Stratified 80/20 split (`test_size=0.20`, `random_state=42`, `stratify=y`) yielding **`120`** training samples and **`30`** testing samples (`10` per species).
- **Feature Scaling:** Applied `StandardScaler()` inside a Scikit-Learn `Pipeline` so mean and standard deviation scaling is learned strictly within each training fold without data leakage.

### 2. Hyperparameter Tuning ($K = 1$ to $20$) via 5-Fold Stratified Cross-Validation
Evaluated `KNeighborsClassifier(n_neighbors=k)` across $K \in [1, 20]$ using `StratifiedKFold(n_splits=5, shuffle=True, random_state=42)`:

| $K$ Value | Mean CV Accuracy | Mean CV Error Rate | CV Accuracy SD |
| :---: | :---: | :---: | :---: |
| `1` | `0.9417` | `0.0583` | `0.0204` |
| **`3` (Optimal)** | **`0.9667`** | **`0.0333`** | **`0.0167`** |
| `4` – `5` | `0.9583` | `0.0417` | `0.0264` |
| `9` – `10` | `0.9583` | `0.0417` | `0.0264` / `0.0000` |
| `19` – `20` | `0.9167` | `0.0833` | `0.0527` |

- **Selected $K$:** **`K = 3`** achieved the lowest cross-validation error rate (**`0.0333`** / **`3.33%`**) and highest mean accuracy (**`96.67%`**).

### 3. Final Model Evaluation on Held-Out Test Set (`30` Samples)
- **Test Accuracy:** **`93.33%`** (`0.9333` — `28` out of `30` samples correctly classified)
- **Test Error Rate:** **`6.67%`** (`0.0667` — `2` `virginica` samples misclassified as `versicolor`)

#### Confusion Matrix
| Actual \ Predicted | `setosa` | `versicolor` | `virginica` |
| :--- | :---: | :---: | :---: |
| **`setosa`** | `10` | `0` | `0` |
| **`versicolor`** | `0` | `10` | `0` |
| **`virginica`** | `0` | `2` | `8` |

#### Classification Report
| Species | Precision | Recall | F1-Score | Support |
| :--- | :---: | :---: | :---: | :---: |
| **`setosa`** | `1.000` | `1.000` | `1.000` | `10` |
| **`versicolor`** | `0.833` | `1.000` | `0.909` | `10` |
| **`virginica`** | `1.000` | `0.800` | `0.889` | `10` |
| **Accuracy / Weighted Avg** | `0.944` | `0.933` | `0.933` | `30` |

### 4. Visualization
- **Error Rate Curve:** Plotted 5-fold CV error rate across $K = 1\dots20$ highlighting the minimum error at $K = 3$.
- **Test Prediction Scatter Plot:** Visualized `sepal length (cm)` vs. `petal length (cm)` distinguishing correct predictions (`o`) from misclassifications (`X`).

## Prerequisites

- Python 3.x
- `numpy`
- `pandas`
- `matplotlib`
- `seaborn`
- `scikit-learn`

```bash
pip install numpy pandas matplotlib seaborn scikit-learn
