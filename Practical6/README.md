
# Practical 6: Hypothesis Testing & Correlation Analysis on Teaching Ratings

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical applies inferential statistical tests—including an Independent Two-Sample $t$-Test, One-Way ANOVA, Chi-Square Test of Independence, and Pearson Correlation—to analyze relationships between instructor demographics, beauty ratings, tenure status, and teaching evaluation scores in `TeachingRatings.csv` using **Pandas**, **SciPy**, **Seaborn**, and **Matplotlib**.

## Questions & Key Findings

### Q1. Independent $t$-Test: Gender vs. Teaching Evaluation
- **Method:** Separated `eval` scores into `male` and `female` groups and ran an independent two-sample $t$-test (`stats.ttest_ind(male_eval, female_eval)`).
- **$p$-Value:** `0.0012`
- **Conclusion:** Since $p = 0.0012 < 0.05$, gender has a statistically significant effect on teaching evaluation scores in this dataset.

### Q2. One-Way ANOVA: Age Groups vs. Beauty Score
- **Method:** Categorized continuous `age` values into three brackets (`Young`: `<40`, `Mid`: `40–55`, `Senior`: `>55`) using `pd.cut()` and compared mean `beauty` scores across groups via `stats.f_oneway()`.
- **$p$-Value:** `0.0000` ($p < 0.0001$)
- **Conclusion:** Since $p < 0.05$, instructor beauty scores differ significantly across age groups.

### Q3. Chi-Square Test: Tenure vs. Gender
- **Method:** Built a $2 \times 2$ contingency table (`pd.crosstab(df['tenure'], df['gender'])`) and performed a Chi-Square test of independence (`stats.chi2_contingency()`).
- **$p$-Value:** `0.1374`
- **Conclusion:** Since $p = 0.1374 > 0.05$, there is no statistically significant association between an instructor's gender and tenure status.

### Q4. Pearson Correlation: Teaching Evaluation vs. Beauty Score
- **Method:** Computed the Pearson correlation coefficient and $p$-value between `eval` and `beauty` (`stats.pearsonr(df['eval'], df['beauty'])`), accompanied by a correlation heatmap (`sns.heatmap()`) across `eval`, `beauty`, and `age`.
- **$p$-Value:** `0.0000` ($p < 0.0001$)
- **Conclusion:** Since $p < 0.05$, there is a statistically significant correlation between instructor beauty scores and teaching evaluation ratings.

## Summary of Statistical Results

| Question | Statistical Test | Variables Tested | $p$-Value | Significant ($\alpha = 0.05$)? |
| :--- | :--- | :--- | :---: | :---: |
| **Q1** | Independent $t$-Test | `gender` vs. `eval` | `0.0012` | Yes |
| **Q2** | One-Way ANOVA | `age_group` vs. `beauty` | `0.0000` | Yes |
| **Q3** | Chi-Square Test | `tenure` vs. `gender` | `0.1374` | No |
| **Q4** | Pearson Correlation | `eval` vs. `beauty` | `0.0000` | Yes |

## Prerequisites

- Python 3.x
- `pandas`
- `scipy`
- `seaborn`
- `matplotlib`

```bash
pip install pandas scipy seaborn matplotlib
