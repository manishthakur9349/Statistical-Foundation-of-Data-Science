
# Practical 3: Statistical Analysis & Data Visualization on Teaching Ratings

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical explores demographic trends, tenure status, age distributions, and evaluation scores in the `TeachingRatings.csv` dataset using **Pandas** and **Matplotlib**[cite: 1].

## Questions & Key Findings

### Q1. Tenure Percentage Among Visible Minority Professors[cite: 1]
Cross-tabulated `minority` and `tenure` status to compare tenure proportions across groups[cite: 1]:

| Minority Status | Not Tenured (`no`) | Tenured (`yes`) |
| :--- | :---: | :---: |
| **Non-Minority (`no`)**[cite: 1] | `23.06%`[cite: 1] | `76.94%`[cite: 1] |
| **Visible Minority (`yes`)**[cite: 1] | `15.63%`[cite: 1] | `84.38%`[cite: 1] |

- **Percentage Tenured (Visible Minority):** `84.375%` (`84.38%`)[cite: 1]
- **Finding:** A higher proportion of visible minority professors in this dataset hold tenure (`84.38%`) compared to non-minority professors (`76.94%`)[cite: 1].

### Q2. Average Age by Tenure Status[cite: 1]
Grouped instructors by `tenure` (`yes` vs. `no`) using `.groupby("tenure")["age"].agg(["mean", "std"])`[cite: 1]:

| Tenure Status | Mean Age | Std Dev |
| :--- | :---: | :---: |
| **Tenured (`yes`)**[cite: 1] | `47.85`[cite: 1] | `10.42`[cite: 1] |
| **Untenured (`no`)**[cite: 1] | `50.19`[cite: 1] | `6.95`[cite: 1] |

- **Finding:** Untenured professors have a slightly higher mean age (`50.19` years) than tenured professors (`47.85` years), while tenured faculty show a wider age spread (standard deviation of `10.42` vs. `6.95`)[cite: 1].

### Q3. Best Graph for the `age` Variable[cite: 1]
- **Graph Choice:** A **Histogram** (`plt.hist(df["age"], bins=10, edgecolor="black")`) is used to visualize the `age` variable[cite: 1].
- **Finding:** Because `age` is a continuous numerical variable, binning into 10 intervals clearly displays frequency distribution, spread (ranging from roughly `30` to `70+` years), and clustering around the `48–55` age range[cite: 1, 2].

### Q4. `pyplot.bar()` vs. `pyplot.barh()` & Gender Distribution[cite: 2]
- **Difference:**
  - `plt.bar()` plots **vertical bars** (gender categories along the X-axis and professor counts along the Y-axis)[cite: 2, 3].
  - `plt.barh()` plots **horizontal bars** (gender categories along the Y-axis and professor counts along the X-axis)[cite: 2, 3].
- **Gender Distribution:** Computed via `df["gender"].value_counts()`[cite: 2, 3]:
  - **Male:** `268`[cite: 3]
  - **Female:** `195`[cite: 3]

### Q5. Median Evaluation Score for Tenured Professors[cite: 3]
- Filtered the dataset for `df["tenure"] == "yes"` and computed `.median()` on the `eval` column[cite: 3].
- **Median Evaluation Score:** `4.0`[cite: 3]

## Prerequisites

- Python 3.x[cite: 1]
- `pandas`[cite: 1]
- `matplotlib`[cite: 1]

```bash
pip install pandas matplotlib
