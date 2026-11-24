# Practical 4: Duplicate Handling, Group Comparisons & Bivariate Visualization on Teaching Ratings

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical investigates duplicate instructor records, evaluates teaching score differences across course divisions, and visualizes the relationship between instructor age and teaching evaluation scores (both overall and segmented by gender) in the `TeachingRatings.csv` dataset using **Pandas**, **NumPy**, **Matplotlib**, and **Seaborn**.

## Questions & Key Findings

### Q1. Duplicate Instructor Records & Age Statistics
Identified duplicate observations using the `prof` identifier (`369` duplicate rows across `463` total records, leaving `94` unique instructors) and compared age metrics before and after deduplication:

| Dataset Scope | Observations (`n`) | Mean Age | Std Dev |
| :--- | :---: | :---: | :---: |
| **All Observations** | `463` | `48.37` (`48.365`) | `9.80` (`9.803`) |
| **Unique Instructors** | `94` | `47.55` (`47.553`) | `10.26` (`10.257`) |

- **Finding:** Removing duplicate course entries shifts the mean instructor age slightly lower from `48.37` to `47.55` years while slightly increasing the standard deviation from `9.80` to `10.26`.

### Q2. Average Teaching Evaluation by Course Division
Grouped courses by `division` (`lower` vs. `upper`) and visualized mean evaluation scores using `sns.barplot()`:

| Course Division | Mean Evaluation Score |
| :--- | :---: |
| **Lower Division** | `4.087` (`4.087261`) |
| **Upper Division** | `3.953` (`3.952614`) |

- **Finding:** Yes, instructors teaching lower-division courses receive higher average teaching evaluations than those teaching upper-division courses by approximately `0.135` points.

### Q3. Relationship Between Age and Teaching Evaluation Scores
- **Visualization:** Generated both a standard scatter plot (`sns.scatterplot()`) and a linear regression trend plot (`sns.regplot()`) mapping `age` against `eval`.
- **Finding:** There is a **weakly negative association** overall—as instructor age increases, evaluation scores tend to decline slightly. Because this is observational data, this reflects correlation rather than causation.

### Q4. Gender-Differentiated Scatter & Regression Plots
- **Visualization:** Created a combined hue-grouped scatter plot (`sns.scatterplot(..., hue='gender')`) and side-by-side linear regression subplots (`sns.lmplot(..., col='gender')`).
- **Finding:** Comparing trends across genders shows a steeper downward trend in evaluation scores with age for female instructors compared to the nearly flat trend line for male instructors.

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`

```bash
pip install pandas numpy matplotlib seaborn
