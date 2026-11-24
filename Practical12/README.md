# Practical 12: Stochastic MCMC Sampling (Metropolis Algorithm) & Deterministic Simulation (Logistic Growth Model)

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Jupyter Notebook / Local Python 3  
**Dataset:** Synthetic Simulation (No external CSV required)

## Overview

This practical explores two contrasting computational modeling paradigms in Python using **NumPy**, **SciPy**, and **Matplotlib**:
1. **Part A (Stochastic Modeling):** Implementing the **Metropolis Algorithm** (Markov Chain Monte Carlo) to draw random samples from a standard normal target distribution.
2. **Part B (Deterministic Modeling):** Simulating a continuous **Logistic Growth Model** numerically via **Euler's Method** to observe resource-constrained population dynamics over time.

## Sections & Key Findings

### Part A: Implementation of the Metropolis Algorithm (MCMC)
- **Aim:** Generate random samples from a standard normal probability density function $\mathcal{N}(0, 1)$ (`scipy.stats.norm.pdf(x, loc=0, scale=1)`) using a symmetric Gaussian random-walk proposal.
- **Simulation Parameters:**
  - **Iterations:** `1,000` (with `10,000` samples visualized in the density comparison)
  - **Initial Value:** `0`
  - **Proposal Std Dev:** `1`
- **Results:**
  - **Acceptance Rate:** **`0.6992`** (`69.92%`)
  - **Visualization:** Plotted a normalized 50-bin histogram of generated Metropolis samples overlaid against the exact standard normal PDF curve, confirming that the Markov chain converges closely to the target bell distribution.

### Part B: Deterministic Simulation — Logistic Growth Model
- **Aim:** Simulate population growth under limited resources using the ordinary differential equation:
  $$\frac{dP}{dt} = rP\left(1 - \frac{P}{K}\right)$$
- **Numerical Solver:** Approximated trajectories over $t \in [0, 50]$ (`200` evenly spaced time steps) using **Euler's Method**:
  $$P_{\text{next}} = P_{\text{current}} + \Delta t \times rP\left(1 - \frac{P}{K}\right)$$

| Parameter / Metric | Value |
| :--- | :---: |
| **Growth Rate ($r$)** | `0.2` |
| **Carrying Capacity ($K$)** | `1000` |
| **Initial Population ($P_0$)** | `50` |
| **Time Horizon ($t$)** | `0` to `50` (`200` steps) |
| **Final Population ($t = 50$)** | **`999.22`** (`999.2235`) |

- **Results:** Plotting population size against time produces a classic S-shaped (sigmoid) growth curve—accelerating rapidly at low population sizes before leveling off asymptotically near the carrying capacity $K = 1000$.

## Prerequisites

- Python 3.x
- `numpy`
- `scipy`
- `matplotlib`

```bash
pip install numpy scipy matplotlib
