# Practical 5: Empirical Probability & Two-Tailed $z$-Test Analysis

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `TeachingRatings.csv`

## Overview

This practical calculates empirical probabilities for teaching evaluation scores in `TeachingRatings.csv` (`463` observations) and performs a two-tailed one-sample $z$-test using **Pandas** and **SciPy** (`scipy.stats.norm`) to compare regional basketball player scoring averages against a historic professional benchmark.

## Questions & Key Findings

### Q1. Probability of Receiving an Evaluation Score Greater Than 4.5
- **Formula:** $P(\text{eval} > 4.5) = \frac{\text{Number of eval scores} > 4.5}{\text{Total number of observations}}$
- **Counts:** `79` out of `463` observations
- **Result:** **`0.1706`** (`0.170626...` / **`17.06%`**)

### Q2. Probability of Receiving an Evaluation Score Between 3.5 and 4.2
- **Condition:** $P(3.5 < \text{eval} < 4.2)$ using `(df['eval'] > 3.5) & (df['eval'] < 4.2)`
- **Counts:** `164` out of `463` observations
- **Result:** **`0.3542`** (`0.354212...` / **`35.42%`**)

### Q3. Two-Tailed One-Sample $z$-Test (Normal Distribution)
Tested whether the regional players' average points per game differs significantly from the historical professional mean at $\alpha = 0.05$:

| Parameter / Metric | Value |
| :--- | :---: |
| **Historical Pro Mean ($\mu$)** | `12` |
| **Population Std Dev ($\sigma$)** | `5.5` |
| **Sample Size ($n$)** | `36` |
| **Regional Sample Mean ($\bar{x}$)** | `10.7` |
| **$z$-Statistic** | `-1.418` (`-1.418182`) |
| **Two-Tailed $p$-Value** | `0.156` (`0.156138`) |
| **Significance Level ($\alpha$)** | `0.05` |

- **Conclusion:** Since $p \approx 0.156 > 0.05$, we **fail to reject the null hypothesis ($H_0$)**. There is insufficient statistical evidence to conclude that the regional players' mean points per game differs from the historical professional mean of `12` points per game.

## Prerequisites

- Python 3.x
- `pandas`
- `scipy`

```bash
pip install pandas scipy
