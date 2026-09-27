# Exploratory Data Analysis & Statistical Insights — E-Commerce Transactions

Internship task: comprehensive EDA — descriptive statistics, correlation structure,
distribution/outlier visuals, and three tested business hypotheses, summarized as markdown
commentary for a business audience.

## What's in this repo

| Path | What it is |
|---|---|
| `data/clean_dataset.csv` | Input data — 10,503 cleaned e-commerce transactions (output of the prior Data Cleaning task) |
| `notebooks/EDA_Statistical_Insights.ipynb` | Full, already-executed EDA notebook |
| `data/correlation_heatmap.png`, `distribution_histograms.png`, `boxplots_by_category_region.png`, `hypothesis2_discount_vs_retention.png` | Chart snapshots referenced in the notebook |

## What the notebook covers

1. **Descriptive statistics** — mean/median/std/quartiles/skew for every numeric field, plus
   categorical value counts.
2. **Correlation heatmap** — all numeric order fields, with the strongest pairs called out.
3. **Distribution histograms** — quantity, price, discount, revenue, profit, margin.
4. **Box plots** — profit margin by category, revenue by region, plus an IQR-based outlier
   count and a look at loss-making orders.
5. **Three tested hypotheses** (α = 0.05):
   - **H1 (Welch's t-test):** does discount level predict order cancellation/return? →
     **not significant** (p = 0.228)
   - **H2 (Pearson correlation):** does average discount predict customer order frequency
     (retention)? → **not significant** (r = 0.018, p = 0.321)
   - **H3 (one-way ANOVA):** does profit margin differ by product category? →
     **not significant** (F = 0.73, p = 0.600)
6. **Top 5 critical findings** in markdown, written honestly against the actual test results
   above (including the negative results — a "no effect found" result is still a real,
   useful finding, not something to be talked around).

## How to reproduce

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter nbconvert --to notebook --execute notebooks/EDA_Statistical_Insights.ipynb
```
