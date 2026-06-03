# Project 2 — Exploratory Data Analysis (EDA)
### DecodeLabs | Data Analytics Internship | Batch 2026

---

# Overview

This project is the **discovery phase** of the data analytics pipeline. Building on the cleaned dataset from Project 1, this EDA uncovers hidden patterns, trends, distributions, and outliers in an orders dataset. The goal is not just to report numbers — it is to translate raw data into actionable business insight using the forensic IPO framework: **Input → Process → Output**.

---

## Objectives

- Calculate **descriptive statistics** (mean, median, std, five-number summary)
- Analyse **distributions** and identify skewness
- Identify **trends** over time (order volume and revenue)
- Break down data by **categories** (product, payment, referral, status)
- Detect **outliers** using IQR and Z-Score methods
- Map **correlations** between numeric variables
- Summarise findings as **business insights**

---

## Project Files

| File | Description |
|---|---|
| `cleaned_dataset.csv` | Input — cleaned dataset from Project 1 |
| `EDA_Project2_DecodeLabs.ipynb` | Main Jupyter Notebook (fully executed with plots) |
| `eda_summary.csv` | Output — top-line KPI summary table |
| `README_Project2_EDA.md` | This file |

---

## Dataset

| Property | Value |
|---|---|
| Source | Orders Analytics Dataset (cleaned) |
| Shape | 1,200 rows × 14 columns |
| Date Range | Jan 2024 – Dec 2024 |
| Key Numeric Columns | `Quantity`, `UnitPrice`, `TotalPrice`, `ItemsInCart` |
| Key Categorical Columns | `Product`, `OrderStatus`, `PaymentMethod`, `ReferralSource`, `CouponCode` |

---

## Visualisations Produced

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

## Tools & Libraries

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

## How to Run

1. Ensure `cleaned_dataset.csv` (output from Project 1) is in the same folder as the notebook.
2. Open `EDA_Project2_DecodeLabs.ipynb` in Jupyter.
3. Run all cells top-to-bottom (`Kernel → Restart & Run All`).
4. All plots and `eda_summary.csv` will be generated automatically.

```bash
# Install dependencies if needed
pip install pandas numpy matplotlib seaborn scipy
```
*DecodeLabs | Batch 2026 | Project 2 of the Data Analytics Internship Track*
