
# Practical 7: Regression Analysis & ANOVA Modeling on Teaching Ratings

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv` (`463` rows, `13` columns)

## Overview

This practical implements Ordinary Least Squares (OLS) regression models, ANOVA modeling, and linear trend visualization on the `TeachingRatings.csv` dataset using **Pandas**, **NumPy**, **Statsmodels**, **Matplotlib**, and **Seaborn** to evaluate how instructor gender, age group, and beauty score relate to teaching evaluations.

## Questions & Key Findings

### Q1. Regression with $t$-Test: Gender vs. Teaching Evaluation
- **Method:** Encoded `gender` into a binary indicator variable (`female = 1`, `male = 0`) and fitted an OLS linear regression model (`eval ~ female`) using `statsmodels.formula.api.ols()`.
- **Model Results:**
  - **Female Coefficient:** `-0.1680`
  - **$t$-Statistic:** `-3.250`
  - **$p$-Value:** `0.001`
  - **$R^2$:** `0.022`
- **Conclusion:** Since $p < 0.05$, we **reject $H_0$**. There is a statistically significant relationship between gender and teaching evaluation rates, with female instructors scoring approximately `0.168` points lower on average than the male reference group.

### Q2. Regression with ANOVA: Beauty Score by Age Group
- **Method:** Segmented `age` into three categories (`40 years and younger`: `113`, `between 40 and 57 years`: `256`, `57 years and older`: `94`) using `pd.cut()`, fitted an OLS categorical model (`beauty ~ C(age_group)`), and computed a Type II ANOVA table (`anova_lm(..., typ=2)`).
- **ANOVA Results:**
  - **Sum of Squares (`sum_sq`):** `18.9647` (`df = 2.0`), Residual: `268.3832` (`df = 460.0`)
  - **$F$-Statistic:** `16.2524`
  - **$p$-Value (`PR(>F)`):** `1.5132e-07`
- **Conclusion:** Since $p < 0.05$, we **reject $H_0$**. Instructor beauty scores differ significantly across the three age brackets.

### Q3. Correlation Using Regression: Teaching Evaluation vs. Beauty Score
- **Method:** Fitted a simple linear regression model (`eval ~ beauty`) via `smf.ols()` and plotted the linear regression fit using `sns.regplot()`.
- **Model Results:**
  - **Intercept:** `3.9983` ($t = 157.727$, $p = 0.000$)
  - **Beauty Coefficient:** `0.1330` ($t = 4.133$, $p = 0.000$)
  - **$F$-Statistic:** `17.08` (`Prob (F-statistic)`: `4.25e-05`)
  - **$R^2$ / Adjusted $R^2$:** `0.036` / `0.034`
- **Conclusion:** Since $p < 0.05$, we **reject $H_0$**. There is a statistically significant positive linear relationship between beauty score and teaching evaluation score, with beauty rating accounting for approximately `3.6%` ($R^2 = 0.036$) of the variance in evaluation scores.

## Summary of Statistical Results

| Question | Model / Test | Key Coefficient / Statistic | $p$-Value | Decision ($\alpha = 0.05$) |
| :--- | :--- | :---: | :---: | :---: |
| **Q1** | OLS (`eval ~ female`) | `coef = -0.1680`, $t = -3.250$ | `0.001` | Reject $H_0$ |
| **Q2** | ANOVA (`beauty ~ C(age_group)`) | $F = 16.2524$ (`df = 2, 460`) | `1.51e-07` | Reject $H_0$ |
| **Q3** | OLS (`eval ~ beauty`) | `coef = +0.1330`, $t = 4.133$, $R^2 = 0.036$ | `4.25e-05` | Reject $H_0$ |

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `statsmodels`
- `matplotlib`
- `seaborn`

```bash
pip install pandas numpy statsmodels matplotlib seaborn
