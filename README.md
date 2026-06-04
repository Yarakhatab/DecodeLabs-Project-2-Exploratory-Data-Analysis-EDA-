# 📊 E-Commerce Exploratory Data Analysis (EDA)
**DecodeLabs | Data Analytics Internship — Project 2**

---

## 📌 Problem Statement

An e-commerce business recorded **1,200 orders across 3 years (2023–2025)**.  
The goal is to uncover patterns in revenue, customer behavior, and order performance — and translate raw numbers into **actionable business decisions**.

---

## 🗂️ Dataset Overview

| Field | Details |
|---|---|
| **File** | `Dataset for Data Analytics 4(Sheet1).csv` |
| **Rows** | 1,200 orders |
| **Columns** | 14 features |
| **Date Range** | 2023 → 2025 |
| **Missing Values** | CouponCode only (filled with `'No Coupon'`) |

### Columns Description

| Column | Type | Description |
|---|---|---|
| `OrderID` | String | Unique order identifier |
| `Date` | DateTime | Order date |
| `Product` | Category | Product name (Chair, Laptop, Phone…) |
| `Quantity` | Integer | Units ordered |
| `UnitPrice` | Float | Price per unit ($) |
| `TotalPrice` | Float | Final order value ($) |
| `OrderStatus` | Category | Delivered / Shipped / Pending / Returned / Cancelled |
| `PaymentMethod` | Category | Credit Card / Debit Card / Cash / Online / Gift Card |
| `ReferralSource` | Category | Instagram / Email / Google / Facebook / Referral |
| `CouponCode` | Category | Coupon applied (or `No Coupon`) |
| `ItemsInCart` | Integer | Total items in cart at checkout |

---

## 🔬 Methodology

```
RAW DATA  →  CLEAN  →  ANALYZE  →  VISUALIZE  →  INSIGHT
```

1. **Data Cleaning** — Handled missing CouponCode values
2. **Feature Engineering** — Extracted `Year`, `Month`, `YearMonth` from Date
3. **Descriptive Statistics** — Mean, Median, Std, Min/Max on numeric columns
4. **Outlier Detection** — IQR Method on `TotalPrice`
5. **Correlation Analysis** — Pearson r between `Quantity`, `UnitPrice`, `ItemsInCart` vs `TotalPrice`
6. **Segmentation** — Revenue by Product, Channel, Payment, Coupon, Status
7. **Trend Analysis** — Monthly revenue over 2023–2025

---

## 📁 Project Structure

```
project-2-eda/
│
├── P2.ipynb                  ← Main notebook (all code)
├── executive_summary.py      ← Business Insights + KPI Card
├── missing_plots.py          ← 5 additional visualizations
├── README.md                 ← This file
└── Dataset for Data Analytics 4(Sheet1).csv
```

---

## 📊 Visualizations Produced

| # | Chart | Insight |
|---|---|---|
| ① | TotalPrice Distribution (Histogram) | Right-skewed — high-value outliers present |
| ② | TotalPrice Boxplot by Product | Price spread varies significantly per product |
| ③ | Order Status Distribution | ~41% of orders are Cancelled or Returned |
| ④ | Total Revenue by Product (Horizontal Bar) | Chair leads in total revenue |
| ⑤ | Referral Source (Pie Chart) | Channels are evenly distributed (~20% each) |
| ⑥ | Correlation Heatmap | UnitPrice has strongest correlation with TotalPrice |
| ⑦ | Monthly Revenue Trend (2023–2025) | Volatile trend — peak in mid-2024 |
| ⑧ | Revenue by Product (Vertical Bar) | Chair & Printer top contributors |
| ⑨ | Payment Methods (Pie Chart) | All methods used almost equally |
| ⑩ | Revenue by Referral Source (Vertical Bar) | Instagram leads revenue generation |
| ⑪ | Avg Order Value by Product | Laptop has highest average order value |
| ⑫ | Coupon Code Usage | FREESHIP is the most-used coupon |

---

## 🔑 Key Findings

### 1. Revenue Distribution is Right-Skewed
- **Mean ($1,054) > Median ($824)** → A small group of high-value orders inflates the average
- **Business Impact:** Marketing to the "average" customer misses ~60% of the base
- ✅ **Action:** Segment customers into High / Mid / Low value tiers

### 2. Chair & Printer Drive the Most Revenue
- Chair alone contributes ~$196K — the top revenue product
- ✅ **Action:** Prioritize inventory and promotions for top products

### 3. ~41% of Orders Are Cancelled or Returned
- Cancelled + Returned = **497 orders** with significant revenue at risk
- ✅ **Action:** Investigate root causes; introduce return-reduction incentives

### 4. Instagram is the #1 Revenue Channel
- Instagram generates the highest revenue among all referral sources (~$275K)
- ✅ **Action:** Increase Instagram marketing budget allocation

### 5. Coupon Dependency is High
- Nearly **50% of orders** use a coupon — pricing strategy may be too discount-dependent
- ✅ **Action:** A/B test removing top coupon to measure revenue sensitivity

### 6. UnitPrice is the Strongest Revenue Predictor
- Pearson r(UnitPrice, TotalPrice) is the highest among all variables
- ✅ **Action:** Premium pricing strategy has a stronger revenue impact than volume

---

## 🛠️ How to Run

### Requirements
```bash
pip install pandas numpy matplotlib seaborn
```

### Steps
1. Place the CSV dataset in `/content/` (Google Colab) or update the path
2. Open `P2.ipynb` in Jupyter or Google Colab
3. Run all cells in order
4. Optionally run `executive_summary.py` for the business insights section

---

## ✅ Portfolio Checklist

- [x] **Narrative Structure** — Problem → Methodology → Findings → Recommendations
- [x] **Technical Evidence** — Clean, modular, well-commented code
- [x] **Data Forensics** — Missing values handled; outliers detected via IQR
- [x] **Business Impact** — Quantified findings with $ values and % metrics
- [x] **README** — Clear documentation for non-technical readers

---

## 👩‍💻 Author

**DecodeLabs Intern — Batch 2026**  
Data Analytics Track | Project 2 of 4

---

*"You are the translator between data and decision."* — DecodeLabs
