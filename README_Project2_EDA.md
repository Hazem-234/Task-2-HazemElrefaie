# 📊 Project 2 — Exploratory Data Analysis (EDA)
### DecodeLabs | Data Analytics Internship | Batch 2026

---

## 📌 Overview

This project is the **discovery phase** of the data analytics pipeline. Building on the cleaned dataset from Project 1, this EDA uncovers hidden patterns, trends, distributions, and outliers in an orders dataset. The goal is not just to report numbers — it is to translate raw data into actionable business insight using the forensic IPO framework: **Input → Process → Output**.

---

## 🎯 Objectives

- Calculate **descriptive statistics** (mean, median, std, five-number summary)
- Analyse **distributions** and identify skewness
- Identify **trends** over time (order volume and revenue)
- Break down data by **categories** (product, payment, referral, status)
- Detect **outliers** using IQR and Z-Score methods
- Map **correlations** between numeric variables
- Summarise findings as **business insights**

---

## 📁 Project Files

| File | Description |
|---|---|
| `cleaned_dataset.csv` | Input — cleaned dataset from Project 1 |
| `EDA_Project2_DecodeLabs.ipynb` | Main Jupyter Notebook (fully executed with plots) |
| `eda_summary.csv` | Output — top-line KPI summary table |
| `README_Project2_EDA.md` | This file |

---

## 📊 Dataset

| Property | Value |
|---|---|
| Source | Orders Analytics Dataset (cleaned) |
| Shape | 1,200 rows × 14 columns |
| Date Range | Jan 2024 – Dec 2024 |
| Key Numeric Columns | `Quantity`, `UnitPrice`, `TotalPrice`, `ItemsInCart` |
| Key Categorical Columns | `Product`, `OrderStatus`, `PaymentMethod`, `ReferralSource`, `CouponCode` |

---

## 🔍 Analysis Sections

### Section 1 — Dataset Overview
Load the cleaned CSV and apply Project 1 fixes inline. Print shape, date range, and a full column type/null report.

### Section 2 — Descriptive Statistics
Compute the **five-number summary** (min, Q1, median, Q3, max) plus mean and standard deviation for all numeric columns. Histograms overlay Mean vs. Median to reveal skew.

| Column | Mean | Median | Std | Min | Max |
|---|---|---|---|---|---|
| Quantity | 3.02 | 3.0 | 1.41 | 1 | 5 |
| UnitPrice | $249.43 | $229.99 | $152.49 | $9.99 | $599.99 |
| TotalPrice | $1,053.97 | $823.62 | $846.70 | $9.99 | $2,999.95 |
| ItemsInCart | 5.49 | 5.0 | 2.88 | 1 | 10 |

> `TotalPrice` is **right-skewed** (Mean > Median) — a small number of high-value orders pull the average up. Use Median ($823.62) as the typical order value benchmark.

### Section 3 — Monthly Trend Analysis
Line charts for order volume and revenue across all 12 months.

| Metric | Value |
|---|---|
| Peak orders month | June 2024 — 53 orders |
| Lowest orders month | August 2024 — 28 orders |
| Total Revenue | $1,264,761.96 |

### Section 4 — Category Breakdowns
Four-panel horizontal bar charts covering:
- **Revenue by Product** — Printer and Chair lead (~$195K each)
- **Orders by Status** — Evenly spread; ~41% Cancelled + Returned (risk signal)
- **Orders by Payment Method** — Online and Cash are most popular
- **Orders by Referral Source** — Instagram (259), Email (250), Google (241)

### Section 5 — Outlier Detection

**IQR Method** (robust; best for business data):

| Metric | Value |
|---|---|
| Q1 (25th pct) | $349.95 |
| Q3 (75th pct) | $1,499.95 |
| IQR | $1,149.99 |
| Lower Fence | -$1,375.04 |
| Upper Fence | $3,224.94 |
| **Outliers Found** | **8 orders** (all above $3,224) |

> These 8 outliers are **signals, not noise** — they represent premium bulk orders and are likely VIP customers worth investigating further.

**Z-Score Method** (sensitive; best for normal distributions):

| Metric | Value |
|---|---|
| Threshold | \|z\| > 3 |
| **Outliers Found** | **0** |

> No extreme statistical outliers. The dataset's spread is within normal bounds — data quality is high.

Boxplots visualise the IQR fences across all four numeric columns.

### Section 6 — Correlation Analysis

Pearson Correlation Coefficient (r) matrix:

| Pair | r | Strength |
|---|---|---|
| UnitPrice ↔ TotalPrice | **0.72** | Strong positive |
| Quantity ↔ TotalPrice | **0.62** | Moderate positive |
| Quantity ↔ ItemsInCart | **0.65** | Moderate positive |
| UnitPrice ↔ Quantity | **0.01** | Negligible |

> Price is the **primary revenue driver**. Customers who browse more items (ItemsInCart) also tend to buy more (Quantity).

### Section 7 — Segment Deep-Dive
- **Product × OrderStatus heatmap** — average order value by product and status combination
- **Coupon Code impact** — bar chart showing average order value per coupon code

### Section 8 — Key Observations & Business Insights

| # | Insight | Business Implication |
|---|---|---|
| 1 | 41% of orders are Cancelled or Returned | Highest-priority operational problem to investigate |
| 2 | TotalPrice is right-skewed | Use Median, not Mean, for customer value benchmarks |
| 3 | Instagram is the top acquisition channel | Increase Instagram marketing budget |
| 4 | 8 IQR outlier orders (>$3,224) detected | Flag and reward potential VIP customers |
| 5 | UnitPrice drives revenue (r = 0.72) | Pricing strategy has greater revenue impact than volume |

### Section 9 — Export
Saves `eda_summary.csv` with top-line KPIs for stakeholder reporting.

---

## 📈 Visualisations Produced

| Plot | File |
|---|---|
| Distribution histograms (Mean vs Median) | `plot_distributions.png` |
| Monthly order & revenue trend lines | `plot_trends.png` |
| Category breakdown bar charts (4-panel) | `plot_categories.png` |
| Boxplots for all numeric columns | `plot_boxplots.png` |
| Correlation heatmap + UnitPrice scatter | `plot_correlation.png` |
| Product × Status average order heatmap | `plot_segment_heatmap.png` |
| Coupon code average order value bar chart | `plot_coupon.png` |

---

## 🛠️ Tools & Libraries

| Tool | Purpose |
|---|---|
| Python 3.12 | Core language |
| pandas | Data manipulation and grouping |
| numpy | Numeric operations |
| matplotlib | Base plotting |
| seaborn | Statistical visualisations |
| scipy.stats | Z-Score calculation |
| Jupyter Notebook | Interactive environment |

---

## ▶️ How to Run

1. Ensure `cleaned_dataset.csv` (output from Project 1) is in the same folder as the notebook.
2. Open `EDA_Project2_DecodeLabs.ipynb` in Jupyter.
3. Run all cells top-to-bottom (`Kernel → Restart & Run All`).
4. All plots and `eda_summary.csv` will be generated automatically.

```bash
# Install dependencies if needed
pip install pandas numpy matplotlib seaborn scipy
```

---

## 💡 Key Learnings

- **Mean vs Median** — always compare both before choosing a central tendency metric. Right-skewed data (like revenue) is better represented by the median.
- **IQR is more robust than Z-Score** for real-world business data because it is not influenced by the extreme values it is trying to detect.
- **Correlation ≠ Causation** — a high r between UnitPrice and TotalPrice is expected by design (they are mathematically related). Always interrogate what a correlation means in business context.
- **Cancellation and return rates** are as important as revenue metrics — a 41% rate is a red flag that no chart title alone would reveal without careful category analysis.
- Outliers can be **noise** (data entry errors → clean/remove) or **signals** (VIP customers, fraud, rare events → investigate). Always classify before acting.

---

*DecodeLabs | Batch 2026 | Project 2 of the Data Analytics Internship Track*
