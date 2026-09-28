# Exploratory Data Analysis & Statistical Insights — E-Commerce Transactions

Comprehensive EDA of 10,503 cleaned e-commerce transactions (output of the prior data-cleaning
task): descriptive statistics, distributions, correlation structure, multivariate charts, three
tested business hypotheses, and a top-5 findings summary.

## Repo contents

| Path | What it is |
|---|---|
| `notebooks/EDA_Statistical_Insights.ipynb` | The full, already-executed notebook (main deliverable) |
| `data/clean_dataset.csv` | Input data |
| `data/distributions.png`, `correlation_heatmap.png`, `boxplots.png` | Univariate, correlation and outlier charts |
| `data/multivariate_1.png`, `multivariate_2.png` | Multivariate charts (price x margin x discount, category x region, seasonality) |
| `data/hypothesis1_retention_vs_discount.png` | Retention vs first-order discount |

## Task requirements -> where covered

| Requirement | Notebook section |
|---|---|
| Descriptive stats (mean, median, std, quartiles) | 1 |
| Correlation heatmap, histograms, box plots to detect anomalies | 2, 2.1, 3, 4 |
| Multivariate visualizations | 4b |
| 3 tested business hypotheses | 5 |
| Top 5 findings in markdown | 6 |

## Hypotheses tested

1. **Customer retention vs discount rate** — does a customer's first-order discount predict
   whether they return? (Welch t, Mann-Whitney, chi-square) -> **no significant link**
   (p = 0.34 / 0.43 / 0.79; ~91% return rate at every discount level).
2. **Profit margin across product categories** (one-way ANOVA) -> **significant**
   (p = 0.004), but the gap is only ~1.9 points (Grocery 34.6% vs Sports 32.7%).
3. **Payment method vs order status** (chi-square) -> **not significant** at 5% (p = 0.058).

## Methodological notes

- An implausible margin skewness (-30) was traced to 24 rows distorted by the earlier cleaning
  step (price capped, cost not); they are excluded and the reasoning is shown in Section 2.1.
- The retention test deliberately uses **first-order discount**, not average discount per
  customer; the latter produced a spurious "significant" result caused by regression to the mean
  and its dependence on order count (explained in Section 5).

## Reproduce

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter nbconvert --to notebook --execute notebooks/EDA_Statistical_Insights.ipynb
```
