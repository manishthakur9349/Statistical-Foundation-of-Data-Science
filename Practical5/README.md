
# Practical 5: Probability Calculations & Two-Tailed Hypothesis Testing

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical computes empirical probabilities on teaching evaluation scores from the `TeachingRatings.csv` dataset (`463` records) and performs a two-tailed normal distribution hypothesis test ($z$-test) comparing regional basketball player scoring averages against a historic professional benchmark using **Pandas**, **NumPy**, and **SciPy**.

## Questions & Key Findings

### Q1. Probability of Receiving an Evaluation Score Greater Than 4.5
- **Method:** Computed the empirical proportion of records satisfying `df['eval'] > 4.5` across all `463` observations.
- **Result:** `79 / 463` observations → **`0.1706` (`17.06%`)**

### Q2. Probability of Receiving an Evaluation Score Between 3.5 and 4.2
- **Method:** Computed the empirical proportion of records strictly between `3.5` and `4.2` (`(df['eval'] > 3.5) & (df['eval'] < 4.2)`).
- **Result:** `164 / 463` observations → **`0.3542` (`35.42%`)**

### Q3. Two-Tailed Hypothesis Test (Basketball Scoring Comparison)
Tested whether a sample of regional basketball players differs significantly from the historic professional mean at significance level $\alpha = 0.05$:

- **Hypotheses:**
  - **Null Hypothesis ($H_0$):** The mean points per game of regional players is not different from the historic mean ($\mu = 12$).
  - **Alternative Hypothesis ($H_a$):** The mean points per game of regional players is different from the historic mean ($\mu \neq 12$).

| Parameter / Metric | Value |
| :--- | :---: |
| **Historic Pro Mean ($\mu$)** | `12.0` |
| **Population Std Dev ($\sigma$)** | `5.5` |
| **Sample Size ($n$)** | `36` |
| **Regional Sample Mean ($\bar{x}$)** | `10.7` |
| **$z$-Score** | `-1.4182` |
| **Two-Tailed $p$-Value** | `0.1561` |
| **Significance Level ($\alpha$)** | `0.05` |

- **Conclusion:** **Fail to reject $H_0$** ($p = 0.1561 > 0.05$). There is insufficient statistical evidence to conclude that the regional players' average score differs significantly from the historic professional mean of `12` points per game.

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `scipy`

```bash
pip install pandas numpy scipy
