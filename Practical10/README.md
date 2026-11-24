
# Practical 10: Exploratory Data Analysis & Principal Component Analysis (PCA) on the Wine Dataset

**Author:** Manish Thakur  
**Registration / ID:** GF202457170  
**Environment:** Google Colab (Python 3)  
**Dataset:** Built-in `sklearn.datasets.load_wine()` (`178` samples, `13` features, `3` wine classes)

## Overview

This practical explores chemical features across three wine cultivars (`class_0`, `class_1`, `class_2`) using **Pandas**, **NumPy**, **Scikit-Learn**, **Matplotlib**, and **Seaborn**. It covers summary statistics, class-wise distribution boxplots, bivariate scatter analysis, covariance matrix inspection, feature standardization via `StandardScaler`, and dimensionality reduction using **Principal Component Analysis (`PCA`)**.

## Workflow & Key Findings

### 1. Dataset Exploration & Descriptive Statistics
- **Dataset Shape:** `178` wine samples with `13` continuous chemical attributes (`alcohol`, `malic_acid`, `ash`, `alcalinity_of_ash`, `magnesium`, `total_phenols`, `flavanoids`, `nonflavanoid_phenols`, `proanthocyanins`, `color_intensity`, `hue`, `od280/od315_of_diluted_wines`, and `proline`).
- **Scale Variation:** Summary statistics (`.describe()`) highlight large scale differences across features—for example, `proline` ranges from `278.0` to `1680.0` (mean `746.893`, SD `314.907`), whereas `nonflavanoid_phenols` ranges from `0.13` to `0.66` (mean `0.362`, SD `0.124`).

### 2. Visual Exploration & Covariance Analysis
- **Class-Wise Boxplots:** Compared distributions across `class_0`, `class_1`, and `class_2` for `alcohol`, `malic_acid`, `color_intensity`, and `proline`, showing distinct median and spread differences (such as higher `proline` and `alcohol` in `class_0`, and higher `malic_acid` and `color_intensity` in `class_2`).
- **Bivariate Scatter Plot:** Plotted `alcohol` vs. `color_intensity` colored by wine class, illustrating partial clustering with some overlap in a two-feature space.
- **Covariance Matrix:** Computed `X.cov()` and visualized it as a heatmap (`sns.heatmap()`). Large values (e.g., `proline` variance and covariance with `magnesium` at `1769.16`) demonstrate why unscaled covariance is dominated by high-magnitude units.

### 3. Feature Standardization (`StandardScaler`)
- Standardized all `13` features to mean `0.0` and standard deviation `1.0` (`ddof=0`) prior to applying PCA so every chemical attribute contributes equally regardless of measurement units.

### 4. Principal Component Analysis (`PCA(n_components=2)`)

| Component | Explained Variance Ratio |
| :--- | :---: |
| **Principal Component 1 (`PC1`)** | **`36.20%`** |
| **Principal Component 2 (`PC2`)** | **`19.21%`** |
| **Combined (`PC1 + PC2`)** | **`55.41%`** |

- **Finding:** Projecting the 13-dimensional standardized dataset onto just the first two principal components captures **`55.41%`** of total variance and reveals clear, well-separated clusters for `class_0`, `class_1`, and `class_2` in the 2D scatter plot.

## Prerequisites

- Python 3.x
- `pandas`
- `numpy`
- `matplotlib`
- `seaborn`
- `scikit-learn`

```bash
pip install pandas numpy matplotlib seaborn scikit-learn
