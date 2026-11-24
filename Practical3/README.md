# Practical 3: Statistical Analysis & Data Visualization on Teaching Ratings

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical explores demographic trends, tenure status, age distributions, and evaluation scores in the `TeachingRatings.csv` dataset using **Pandas** and **Matplotlib**.

## Questions & Key Findings

### Q1. Tenure Percentage Among Visible Minority Professors
Cross-tabulated `minority` and `tenure` status using `pd.crosstab()` with row-wise normalization to compare tenure proportions across groups:

| Minority Status | Not Tenured (`no`) | Tenured (`yes`) |
| :--- | :---: | :---: |
| **Non-Minority (`no`)** | `23.06%` | `76.94%` |
| **Visible Minority (`yes`)** | `15.63%` | `84.38%` |

- **Percentage Tenured (Visible Minority):** `84.375%` (`84.38%`)
- **Finding:** A higher proportion of visible minority professors in this dataset hold tenure (`84.38%`) compared to non-minority professors (`76.94%`).

### Q2. Average Age by Tenure Status
Grouped instructors by `tenure` (`yes` vs. `no`) using `.groupby("tenure")["age"].agg(["mean", "std"])`:

| Tenure Status | Mean Age | Std Dev |
| :--- | :---: | :---: |
| **Tenured (`yes`)** | `47.85` | `10.42` |
| **Untenured (`no`)** | `50.19` | `6.95` |

- **Finding:** Untenured professors have a slightly higher mean age (`50.19` years) than tenured professors (`47.85` years), while tenured faculty show a wider age spread (standard deviation of `10.42` vs. `6.95`).

### Q3. Best Graph for the `age` Variable
- **Graph Choice:** A **Histogram** (`plt.hist(df["age"], bins=10, edgecolor="black")`) works best because `age` is a continuous numerical variable.
- **Finding:** Binning into 10 intervals clearly displays the frequency distribution, overall spread (roughly `30` to `70+` years), and central clustering around the `48–55` age range.

### Q4. `pyplot.bar()` vs. `pyplot.barh()` & Gender Distribution
- **Difference:**
  - `plt.bar()` plots **vertical bars** (gender categories along the horizontal X-axis and professor counts along the vertical Y-axis).
  - `plt.barh()` plots **horizontal bars** (gender categories along the vertical Y-axis and professor counts along the horizontal X-axis), which improves readability when category labels are long.
- **Gender Distribution:** Computed via `df["gender"].value_counts()` (`male`: `268`, `female`: `195`) and visualized using both vertical and horizontal bar charts.

### Q5. Median Evaluation Score for Tenured Professors
- Filtered the dataset for `df["tenure"] == "yes"` and computed `.median()` on the `eval` column.
- **Median Evaluation Score:** `4.0`

## Prerequisites

- Python 3.x
- `pandas`
- `matplotlib`

```bash
pip install pandas matplotlib
