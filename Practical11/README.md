
# Practical 11: Sunspot Numbers — Gamma Distribution Modeling & MCMC (Metropolis-Hastings)

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** `SN_m_tot_V2.0.csv` (Monthly mean total sunspot number, Jan 1749 – Nov 2018; `3,239` records)

## Overview

This practical models monthly sunspot counts (`1749–2018`) using a right-skewed **Gamma distribution** $\text{Gamma}(a, b)$ and implements a **Metropolis-Hastings Markov Chain Monte Carlo (MCMC)** sampler from scratch in Python using **NumPy**, **Pandas**, **SciPy**, and **Matplotlib** to estimate posterior parameter distributions across different time windows.

## Workflow & Key Findings

### 1. Time-Series & 12-Year Solar Cycle Exploration
- **Dataset Scope:** Loaded `3,239` monthly records (`decimal_date <= 2018.874`) across `7` columns (`year`, `month`, `decimal_date`, `sunspot`, `std`, `n_obs`, `provisional`).
- **Solar Cycle Pattern:** Time-series plotting reveals an ~11-year solar oscillation with varying peak amplitudes. Grouping observations into 12-year blocks (`cycle` and `t_in_cycle`) and overlaying them illustrates the average solar cycle profile.

### 2. Maximum Likelihood Estimation (MLE) Gamma Fit
- **Zero Filtering:** Dropped `67` zero-count months (`sunspot <= 0`) since the Gamma distribution requires strictly positive values ($x > 0$).
- **MLE Parameters:** Fitted `stats.gamma.fit(x_pos, floc=0)`, yielding shape **$a = 1.17$** and scale **$b = 71.6$**, closely matching the right-skewed empirical histogram.

### 3. MCMC Metropolis-Hastings Sampling & Burn-In Removal
- **Sampler Setup:** Ran `10,000` iterations starting at $(a_0 = 4, b_0 = 10)$ with flat priors ($a, b > 0$) across three subsets, discarding the first **`2,000`** burn-in iterations:
  - **First 50 samples:** Acceptance rate = `0.22`
  - **All samples:** Acceptance rate = `0.16`
  - **Last 50 samples:** Acceptance rate = `0.23`

### 4. Posterior Parameter Estimates & 95% Credible Intervals

| Dataset Group | Shape $a$ (Mean) | $a$ 95% CI | Scale $b$ (Mean) | $b$ 95% CI | Implied Mean ($a \cdot b$) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **First 50 samples** | `6.19` | `[3.83, 8.79]` | `18.15` | `[12.04, 28.01]` | `107.41` |
| **All samples** | `1.18` | `[1.13, 1.23]` | `71.40` | `[67.82, 75.48]` | `84.05` |
| **Last 50 samples** | `1.31` | `[0.91, 1.86]` | `32.36` | `[20.79, 49.88]` | `41.05` |

- **Key Takeaways:**
  - On the **full dataset**, the MCMC posterior means ($a = 1.18$, $b = 71.40$) align closely with the MLE fit ($a = 1.17$, $b = 71.6$).
  - Smaller 50-month windows produce wider credible intervals and noticeably different $(a, b)$ estimates because the local phase of the ~11-year solar cycle dominates short windows.

## Prerequisites

- Python 3.x
- `numpy`
- `pandas`
- `matplotlib`
- `scipy`

```bash
pip install numpy pandas matplotlib scipy
