
# Practical 8: Decision Tree Classification, Impurity Analysis & Max Depth Tuning

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `diabetes_prediction_dataset.csv` (`100,000` rows, `9` columns)

## Overview

This practical builds a Decision Tree classification pipeline on the `diabetes_prediction_dataset.csv` dataset using **Pandas**, **NumPy**, **Scikit-Learn**, and **Matplotlib**. It evaluates feature splitting quality via **Entropy**, **Information Gain**, and **Gini Reduction**, trains an entropy-based Decision Tree classifier (`max_depth=4`), evaluates predictions using a confusion matrix and classification report, and compares model accuracy across tree depths `1` through `10`.

## Workflow & Key Findings

### 1. Dataset Exploration & Train-Test Split
- **Dataset Summary:** `100,000` records (`0` missing values, `3,854` duplicate rows) with `8` predictor features (`gender`, `age`, `hypertension`, `heart_disease`, `smoking_history`, `bmi`, `HbA1c_level`, `blood_glucose_level`) and binary target `diabetes` (`0` = No Diabetes: `91,500` / `91.5%`; `1` = Diabetes: `8,500` / `8.5%`).
- **Train-Test Split:** Stratified 80/20 split (`test_size=0.20`, `random_state=42`) yielding `80,000` training samples and `20,000` testing samples.
- **Target Entropy:** Initial training target entropy is **`0.419556`** (Gini Index: **`0.15555`**).

### 2. Feature Impurity & Root Node Selection
Evaluated single-level splits (`max_depth=1`) for each feature using both `entropy` and `gini` criteria:

| Feature | Information Gain | Gini Reduction |
| :--- | :---: | :---: |
| **`HbA1c_level`** | **`0.152283`** | **`0.067614`** |
| **`blood_glucose_level`** | `0.126046` | `0.056606` |
| **`age`** | `0.045421` | `0.009669` |
| **`bmi`** | `0.023247` | `0.005670` |
| **`hypertension`** | `0.019516` | `0.006095` |
| **`heart_disease`** | `0.013370` | `0.004479` |
| **`smoking_history`** | `0.011500` | `0.002224` |
| **`gender`** | `0.001019` | `0.000222` |

- **Best Root Node:** `HbA1c_level` achieved the highest Information Gain (`0.152283`) and Gini Reduction (`0.067614`), splitting at threshold **`HbA1c_level <= 6.7`**.

### 3. Decision Tree Pipeline (`max_depth=4`) & Evaluation
- **Pipeline Architecture:** Used `ColumnTransformer` with `OneHotEncoder(handle_unknown="ignore")` for categorical variables (`gender`, `smoking_history`) and `passthrough` for numerical features, paired with `DecisionTreeClassifier(criterion="entropy", max_depth=4, random_state=42)`.
- **Test Accuracy:** **`97.23%`** (`0.9723`)

#### Confusion Matrix (`20,000` Test Samples)
| Actual \ Predicted | No Diabetes (`0`) | Diabetes (`1`) |
| :--- | :---: | :---: |
| **No Diabetes (`0`)** | `18,300` (TN) | `0` (FP) |
| **Diabetes (`1`)** | `554` (FN) | `1,146` (TP) |

#### Classification Report
| Class | Precision | Recall | F1-Score | Support |
| :--- | :---: | :---: | :---: | :---: |
| **No Diabetes (`0`)** | `0.97` | `1.00` | `0.99` | `18,300` |
| **Diabetes (`1`)** | `1.00` | `0.67` | `0.81` | `1,700` |
| **Weighted Avg / Accuracy** | `0.97` | `0.97` | `0.97` | `20,000` |

### 4. `max_depth` Hyperparameter Comparison (`1` to `10`)

| Max Depth | Test Accuracy |
| :---: | :---: |
| `1` | `95.45%` (`0.95450`) |
| `2` – `9` | **`97.23%`** (`0.97230`) |
| `10` | `97.20%` (`0.97195`) |

- **Finding:** Test accuracy jumps from `95.45%` at `max_depth=1` to a peak plateau of **`97.23%`** across depths `2` through `9`, before slightly declining to `97.20%` at `max_depth=10` due to minor overfitting.

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `scikit-learn`

```bash
pip install pandas numpy matplotlib scikit-learn
