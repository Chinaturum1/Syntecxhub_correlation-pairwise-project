# Correlation Heatmap & Pairwise Relationships

A Python-based exploratory data analysis project that computes and visualizes Pearson correlations between numeric features in a housing dataset, using a masked correlation heatmap and a pairplot to uncover key variable relationships.

---

## Table of Contents
- [Overview](#overview)
- [Dataset](#dataset)
- [Tools & Libraries](#tools--libraries)
- [Project Structure](#project-structure)
- [Key Steps](#key-steps)
- [Summary of Findings](#summary-of-findings)

---

## Overview

This project explores pairwise relationships between numeric housing features using:
- A **masked Pearson correlation heatmap** (lower triangle only, to eliminate redundancy)
- A **pairplot with hue** to visualize how the number of stories influences relationships across key features

The goal is to identify which features are most strongly related to house price, and whether any variables move independently of each other.

---

## Dataset

**Housing Dataset** — contains 545 records across 13 columns covering property features and price.

Numeric features used for correlation analysis:
| Feature | Description |
|---|---|
| `price` | Sale price of the property |
| `area` | Total area of the property (sq ft) |
| `bedrooms` | Number of bedrooms |
| `bathrooms` | Number of bathrooms |
| `stories` | Number of floors |
| `parking` | Number of parking spaces |

---

## Tools & Libraries

- Python 3
- `pandas` — data loading and correlation computation
- `seaborn` — heatmap and pairplot visualization
- `matplotlib` — figure rendering and export
- `numpy` — upper triangle mask generation

---

## Project Structure

```
project3-correlation-analysis/
│
├── data/
│   └── Housing.csv
├── notebooks/
│   └── CorrelationHeatmap.ipynb
├── outputs/
│   ├── heatmap.png
│   └── pairplot.png
└── README.md
```

---

## Key Steps

1. **Load & inspect** the dataset using `df.head()` and `df.info()`
2. **Select numeric features** and drop null values
3. **Compute Pearson correlation matrix** using `.corr()`
4. **Mask the upper triangle** using `np.triu` and `np.ones_like` to remove redundant values
5. **Plot the heatmap** with annotations, coolwarm colormap, and proper formatting
6. **Generate a pairplot** with `stories` as the hue variable to reveal group-level patterns across key features

---

## Summary of Findings

- **Price and area** show the strongest positive correlation (r = 0.54), suggesting larger properties command higher prices.
- **Bathrooms, bedrooms, and parking** all correlate positively with price (r = 0.52, 0.42, and 0.38 respectively), indicating that more of each feature generally pushes the price higher.
- The **pairplot reveals** that houses with more stories tend to have higher prices regardless of bedroom count, a pattern not immediately visible from the heatmap alone.
- **Stories and parking** show the weakest correlation, meaning they change largely independently of each other. Similar weak relationships are observed between parking and bedrooms, parking and bathrooms, and stories and area.
- All numeric features correlate **positively** with one another — there are no competing variables in this dataset where an increase in one feature corresponds to a decrease in another.
