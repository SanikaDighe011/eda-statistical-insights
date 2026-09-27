# Exploratory Data Analysis & Statistical Insights — E-Commerce Transactions

Internship task: comprehensive EDA — descriptive statistics, correlation structure,
distribution/outlier visuals, and three tested business hypotheses, summarized as markdown
commentary for a business audience.

## What's in this repo

| Path | What it is |
|---|---|
| `data/clean_dataset.csv` | Input data — 10,503 cleaned e-commerce transactions (output of the prior Data Cleaning task) |
| `notebooks/EDA_Statistical_Insights.ipynb` | Full, already-executed EDA notebook |
| `data/distributions.png` | Histograms of revenue, profit margin, quantity, discount |
| `data/correlation_heatmap.png` | Correlation matrix of all numeric order fields |
| `data/boxplots.png` | Profit margin by category, and revenue by order status |

## What the notebook covers

1. **Descriptive statistics** — mean/median/std/quartiles for every numeric field, plus
   categorical value counts.
2. **Distributions** — histograms for revenue, profit margin, quantity, discount, with
   skewness reported.
3. **Anomaly check** — investigates an implausible skew value found in step 2, traces it to a
   cleaning-pipeline artifact from the prior task (unit_price was outlier-capped but unit_cost
   wasn't), and excludes the 24 affected rows from further analysis with the reasoning shown.
4. **Correlation heatmap** — all numeric order fields, strongest pairs called out.
5. **Box plots** — profit margin by product category, revenue by order status, plus an
   IQR-based outlier count per category.
6. **Three tested business hypotheses**, each with a stated H₀/H₁, the test used, and the
   result:
   - **H1:** discount % and order outcome (completed vs. cancelled/returned) — Welch's t-test
   - **H2:** profit margin % across product categories — one-way ANOVA
   - **H3:** payment method and order status — chi-square test of independence
7. **Top 5 critical findings** in markdown commentary, grounded in the actual computed
   results above (not fixed/hardcoded numbers).

## How to reproduce

```bash
pip install pandas numpy matplotlib seaborn scipy jupyter
jupyter nbconvert --to notebook --execute notebooks/EDA_Statistical_Insights.ipynb
```

## Headline results (last run)

- Hypothesis 1 (discount % vs. order outcome): **not significant** (p ≈ 0.24) — discount level
  does not predict whether an order completes or gets cancelled/returned.
- Hypothesis 2 (profit margin by category): **significant** (p ≈ 0.004) — category is a real
  driver of margin, once the cleaning-artifact rows are excluded.
- Hypothesis 3 (payment method vs. order status): **not significant** (p ≈ 0.06) — visible
  differences in cancellation rate by payment method are within the range of chance.

Exact statistics are in the notebook's Section 5 output cells, since they can shift slightly
between re-runs of the upstream random data generator.
