# Practical 6: Hypothesis Testing & Correlation Analysis on Teaching Ratings

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical applies inferential statistical methods—an Independent Two-Sample $t$-Test, One-Way ANOVA, Chi-Square Test of Independence, and Pearson Correlation—to evaluate relationships between instructor gender, age, tenure status, beauty ratings, and teaching evaluation scores in the `TeachingRatings.csv` dataset (`463` observations) using **Pandas** and **SciPy**.

## Questions & Key Findings

### Q1. Independent Two-Sample $t$-Test: Gender vs. Teaching Evaluation
- **Hypotheses:**
  - $H_0$: There is no difference in teaching evaluation scores between male and female instructors.
  - $H_1$: There is a difference in teaching evaluation scores between male and female instructors.
- **Method:** Compared `eval` scores between `female` and `male` instructors using `ttest_ind(female_eval, male_eval, equal_var=True)`.
- **Results:**
  - **$t$-Statistic:** `-3.2499` (`-3.249938`)
  - **$p$-Value:** `0.00124` (`0.001239`)
- **Decision & Conclusion:** Since $p = 0.00124 < 0.05$, we **reject $H_0$**. There is sufficient statistical evidence that gender significantly affects teaching evaluation scores.

### Q2. One-Way ANOVA: Beauty Score by Age Group
- **Hypotheses:**
  - $H_0$: The mean beauty scores of all three age groups are equal ($\mu_1 = \mu_2 = \mu_3$).
  - $H_1$: At least one age group's mean beauty score is different.
- **Method:** Segmented continuous `age` into three categories (`40 years and younger` $\le 40$, `between 40 and 57 years` $>40$ and $<57$, `57 years and older` $\ge 57$) and ran a one-way ANOVA using `f_oneway(young, middle, old)`.
- **Results:**
  - **$F$-Statistic:** `17.5976` (`17.597558`)
  - **$p$-Value:** `4.32e-08` (`4.322550e-08`)
- **Decision & Conclusion:** Since $p < 0.05$, we **reject $H_0$**. Beauty scores differ significantly across instructor age groups.

### Q3. Chi-Square Test of Independence: Tenure vs. Gender
- **Hypotheses:**
  - $H_0$: Tenure and gender are independent.
  - $H_1$: Tenure and gender are associated.
- **Method:** Constructed a $2 \times 2$ contingency table (`pd.crosstab(df['tenure'], df['gender'])`) and applied `chi2_contingency()`:

| Tenure Status | Female | Male |
| :--- | :---: | :---: |
| **Not Tenured (`no`)** | `50` | `52` |
| **Tenured (`yes`)** | `145` | `216` |

- **Results:**
  - **Chi-Square ($\chi^2$):** `2.2068` (`2.206782`)
  - **Degrees of Freedom (`dof`):** `1`
  - **$p$-Value:** `0.1374` (`0.137405`)
- **Decision & Conclusion:** Since $p = 0.1374 > 0.05$, we **fail to reject $H_0$**. There is no statistically significant association between tenure status and gender.

### Q4. Pearson Correlation: Teaching Evaluation vs. Beauty Score
- **Hypotheses:**
  - $H_0$: There is no correlation between beauty score and teaching evaluation score.
  - $H_1$: There is a correlation between beauty score and teaching evaluation score.
- **Method:** Computed linear correlation between `beauty` and `eval` using `pearsonr(df['beauty'], df['eval'])`.
- **Results:**
  - **Correlation Coefficient ($r$):** `0.189` (`0.189039`)
  - **$p$-Value:** `0.0000425` (`4.247116e-05`)
- **Decision & Conclusion:** Since $p < 0.05$, we **reject $H_0$**. There is a statistically significant, weak positive linear relationship ($r = 0.189$) between beauty scores and teaching evaluations.

## Summary of Statistical Results

| Question | Statistical Test | Test Statistic | $p$-Value | Decision ($\alpha = 0.05$) |
| :--- | :--- | :---: | :---: | :---: |
| **Q1** | Independent Two-Sample $t$-Test | $t = -3.2499$ | `0.00124` | Reject $H_0$ |
| **Q2** | One-Way ANOVA | $F = 17.5976$ | `4.32e-08` | Reject $H_0$ |
| **Q3** | Chi-Square Test of Independence | $\chi^2 = 2.2068$ (`dof = 1`) | `0.1374` | Fail to reject $H_0$ |
| **Q4** | Pearson Correlation | $r = 0.1890$ | `0.0000425` | Reject $H_0$ |

## Prerequisites

- Python 3.x
- `pandas`
- `scipy`

```bash
pip install pandas scipy
