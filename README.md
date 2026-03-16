# 🛒 Retail Sales Analytics — Supermart Grocery
### EDA · RFM Customer Segmentation · Sales Forecasting

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-Data-150458?style=flat&logo=pandas&logoColor=white)
![seaborn](https://img.shields.io/badge/seaborn-Viz-4C72B0?style=flat)
![Status](https://img.shields.io/badge/Status-Complete-2ECC71?style=flat)

---

## 📌 Project Overview

End-to-end retail analytics on **9,993 grocery orders** from a supermart dataset (2015–2018).  
This project focuses on understanding business performance through EDA, customer segmentation using RFM analysis, and a linear sales trend forecast.

**The core questions:**
- *Where is revenue growing and where is it concentrated?*
- *Which customers are most valuable — and which are slipping away?*
- *Does discounting actually improve profitability?*

> ⚠️ **Dataset Note:** This is a synthetic/practice dataset. It exhibits artificial patterns — identical ~25% margins across all categories and only 50 unique customers — that wouldn't occur in real grocery retail. The analysis demonstrates real analytics techniques applied honestly to this data.

---

## 📊 Key Results at a Glance

| Metric | Value |
|--------|-------|
| Total Revenue | ₹14.9 Million |
| Date Range | January 2015 — December 2018 |
| Total Orders | 9,993 |
| Unique Customers | 50 (B2B-style accounts) |
| Revenue Growth | **+131%** — ₹2,03,014/month → ₹4,68,719/month |
| Monthly Growth Trend | **+₹5,462 per month** (linear) |
| Discount–Profit Correlation | **r = 0.00** (zero effect) |

---

## 🔍 Top 7 Findings

| # | Finding | Data |
|---|---------|------|
| 1 | **131% revenue growth in 4 years** | ₹2,03,014/month (Jan 2015) → ₹4,68,719/month (Dec 2018) |
| 2 | **Discount has ZERO effect on profit** | r = 0.00 — fixed markup pricing model revealed |
| 3 | **West region dominates** | 32.1% of total revenue |
| 4 | **Top 10 cities drive 44.1% of sales** | Kanyakumari #1 at ₹7,06,764 |
| 5 | **Champions (16%) drive 17.2% of revenue** | 8 accounts → ₹25,75,253 |
| 6 | **At Risk + Lost = ₹62L recoverable** | 22 accounts worth re-engaging |
| 7 | **Health Drinks leads sub-categories** | ₹10,51,439 — 7% of total revenue |

---

## 🗂️ Dataset

- **Source:** Synthetic practice dataset (educational purposes)
- **Size:** 9,993 rows × 11 columns (after removing 1 data error)
- **Columns:** `Order ID`, `Customer Name`, `Category`, `Sub Category`, `City`, `Order Date`, `Region`, `Sales`, `Discount`, `Profit`, `State`
- **Date range:** January 2015 — December 2018
- **Categories:** 7 | **Sub-categories:** 23 | **Cities:** varied across Tamil Nadu

---

## 🛠️ Tech Stack

```
Python 3.10+
├── pandas          — data loading, cleaning, groupby, RFM calculation
├── numpy           — numerical operations, linear trend fitting
├── matplotlib      — all chart creation
├── seaborn         — distribution plots, heatmap styling
├── dateutil        — parsing mixed date formats safely
└── scikit-learn    — LinearRegression for sales forecasting
```

---

## 📁 Project Structure

```
retail-sales-analytics/
│
├── supermart_analysis.py    ← main analysis file (12 sections)
├── README.md                ← this file
│
├── Section breakdown:
│   ├── Section 1  — Load Data
│   ├── Section 2  — Data Cleaning (6 steps)
│   ├── Section 3  — Understand Data Structure
│   ├── Section 4  — EDA: Distributions
│   ├── Section 5  — Category Performance
│   ├── Section 6  — KEY FINDING: Discount vs Profit
│   ├── Section 7  — Regional & Geographic Analysis
│   ├── Section 8  — Temporal Analysis (2015–2018)
│   ├── Section 9  — RFM Customer Segmentation
│   ├── Section 10 — Sub-Category Deep Dive
│   ├── Section 11 — Correlation Heatmap
│   └── Section 12 — Key Findings Summary
```

---

## ⚙️ How to Run

**1. Clone the repository**
```bash
git clone https://github.com/roshani-ahire-09/retail-sales-analytics.git
cd retail-sales-analytics
```

**2. Install dependencies**
```bash
pip install pandas numpy matplotlib seaborn python-dateutil scikit-learn
```

**3. Add the dataset**
Place the CSV file in the same folder as the `.py` file and rename it:
```
Supermart Grocery Sales - Retail Analytics Dataset.csv
```

**4. Run the analysis**
```bash
python supermart_analysis.py
```

**Output:** 8 chart images saved to `/images/` folder + printed findings summary.

---

## 🧹 Data Cleaning Steps

| Step | Issue Found | Fix Applied |
|------|-------------|-------------|
| Region filter | 1 lone 'North' record — data entry error | Removed (kept 9,993 rows) |
| State column | Only 1 unique value (Tamil Nadu) — zero variance | Dropped entirely |
| Order Date | Mixed date formats (DD-MM-YYYY and MM-DD-YYYY) | `dateutil.parser` with `dayfirst=True` |
| Date features | No Year/Month columns | Extracted `Year` and `Month` from parsed dates |
| Profit Margin | No margin column in raw data | Created: `Profit / Sales` |
| Validation | Checked for invalid Sales, Discounts, missing Profit | All 0 issues found |

---

## 🔬 The Headline Finding — Discount:Profit r = 0.00

This is the most analytically interesting finding in the dataset:

```
Discount ↔ Profit correlation  :  r = 0.00
Discount ↔ Margin correlation  :  r = 0.01
Sales    ↔ Profit correlation  :  r = 0.61
```

**What this means:**
Whether a customer gets 10% or 35% discount — the company's profit doesn't change.  
Profit is driven entirely by **sales volume**, not margin management.  
This reveals a **fixed-markup pricing model** — unusual in real grocery retail where heavy discounts typically compress margins.

> This finding also corrects the original analysis which recommended "reduce discounts to 18-20%" — a recommendation that has no data support when discount has zero correlation with profit.

---

## 👥 RFM Customer Segmentation

RFM (Recency · Frequency · Monetary) segments customers on three dimensions:

| Segment | Customers | Revenue | Revenue Share |
|---------|-----------|---------|--------------|
| Champions | 8 | ₹25,75,253 | 17.2% |
| Loyal | 9 | ₹27,82,476 | 18.6% |
| Potential Loyalists | 11 | ₹33,22,670 | 22.2% |
| At Risk | 11 | ₹32,13,208 | 21.5% |
| Lost | 11 | ₹30,62,121 | 20.5% |

> **Note:** 50 customers placing ~200 orders each over 4 years is not typical B2C retail behaviour. This is a synthetic data artifact — segments are interpreted as B2B-style wholesale accounts, not individual shoppers.

**Business priority:** The 22 At Risk + Lost accounts represent **₹62,75,329 in revenue** — the clearest re-engagement opportunity in the data.

---

## 📈 Sales Forecast

Simple linear regression on monthly aggregated sales:

```
Monthly growth rate  : +₹5,462 per month
Jan 2015 baseline   : ₹2,03,014/month
Dec 2018 actual     : ₹4,68,719/month
4-year growth       : +131%
```

> A 6-month forward forecast shows near-flat projections (~₹4,59,000/month) — the linear trend flattens as it approaches recent months. This is a baseline forecast only; a proper time-series model (ARIMA, Prophet) would handle seasonality better.

---

## ⚠️ Honest Limitations

| Limitation | Impact |
|------------|--------|
| Synthetic dataset with fixed margins | Category-level pricing insights are not real |
| Only 50 customers | RFM is valid methodologically but not B2C representative |
| Tamil Nadu only | Regional insights don't generalise nationally |
| No product cost data | Cannot calculate true profitability |
| No demographic data | Customer segmentation can't go deeper than RFM |

---

## 💡 Actionable Insights

**Revenue & Growth**
- 131% growth in 4 years — the business is healthy and scaling
- Nov–Dec are peak months; Feb is consistently lowest — seasonal inventory planning opportunity

**Geographic**
- West region at 32.1% creates concentration risk — disruption there hits ⅓ of revenue
- Top 10 cities at 44.1% — growth requires penetrating new cities

**Customer Strategy**
- Re-engage the 22 At Risk/Lost accounts (₹62L revenue at stake)
- Protect the 17 Champions + Loyal accounts (35.8% of revenue from 34% of customers)

---

## 👤 Author

**Roshani Dadaji Ahire**  
Data Analyst — Python · SQL · Tableau  
📧 roshaniahire1110@email.com  
🔗 [LinkedIn](https://linkedin.com/in/roshaniahire)  


---

*This is a portfolio project built on a synthetic practice dataset.*  
*Findings demonstrate analytical techniques and honest data interpretation.*
