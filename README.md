# 📊 E-Commerce Exploratory Data Analysis (EDA)
**DecodeLabs | Data Analytics Internship — Project 2**

---

## 📌 Problem Statement

An e-commerce business recorded **1,200 orders across 2.5 years (Jan 2023 – Jun 2025)**.  
The goal is to uncover patterns in revenue, customer behavior, and order performance — and translate raw numbers into **actionable business decisions**.

---

## 🗂️ Dataset Overview

| Field | Details |
|---|---|
| **File** | `Dataset for Data Analytics 4(Sheet1).csv` |
| **Rows** | 1,200 orders |
| **Columns** | 17 columns (14 original + 3 engineered) |
| **Date Range** | Jan 2023 → Jun 2025 |
| **Missing Values** | `CouponCode` only — 309 blanks filled with `'No Coupon'` |

### Columns Description

| Column | Type | Description |
|---|---|---|
| `OrderID` | String | Unique order identifier |
| `Date` | DateTime | Order date |
| `CustomerID` | String | Unique customer identifier |
| `Product` | Category | Chair / Laptop / Phone / Printer / Tablet / Monitor / Desk |
| `Quantity` | Integer | Units ordered (1–5) |
| `UnitPrice` | Float | Price per unit ($11 – $700) |
| `ShippingAddress` | String | Shipping address |
| `PaymentMethod` | Category | Credit Card / Debit Card / Cash / Online / Gift Card |
| `OrderStatus` | Category | Delivered / Shipped / Pending / Returned / Cancelled |
| `TrackingNumber` | String | Shipment tracking number |
| `ItemsInCart` | Integer | Total items in cart at checkout (1–10) |
| `CouponCode` | Category | FREESHIP / WINTER15 / SAVE10 / No Coupon |
| `ReferralSource` | Category | Instagram / Email / Google / Facebook / Referral |
| `TotalPrice` | Float | Final order value ($11 – $3,456) |
| `Year` | Integer | Extracted from Date |
| `Month` | Integer | Extracted from Date |
| `YearMonth` | Period | Extracted from Date (e.g. 2023-01) |

---

## 🔬 Methodology

```
RAW DATA  →  CLEAN  →  ANALYZE  →  VISUALIZE  →  INSIGHT
```

1. **Data Cleaning** — Handled missing `CouponCode` values (309 blanks → `'No Coupon'`)
2. **Feature Engineering** — Extracted `Year`, `Month`, `YearMonth` from `Date`
3. **Descriptive Statistics** — Mean, Median, Std, Min/Max on numeric columns
4. **Outlier Detection** — IQR Method on `TotalPrice` → 8 outliers detected
5. **Correlation Analysis** — Pearson r between `Quantity`, `UnitPrice`, `ItemsInCart` vs `TotalPrice`
6. **Segmentation** — Revenue by Product, Channel, Payment Method, Coupon, Order Status
7. **Trend Analysis** — Monthly revenue over Jan 2023 – Jun 2025

---

## 📊 Visualizations in the Notebook

| # | Chart | Key Insight |
|---|---|---|
| ① | TotalPrice Distribution (Histogram + KDE) | Right-skewed — Mean ($1,054) > Median ($824) |
| ② | TotalPrice Boxplot by Product | 8 high-value outliers detected |
| ③ | Order Status Distribution | Cancelled leads (250), Delivered is lowest (231) |
| ④ | Total Revenue by Product | Chair & Printer top revenue (~$196K each) |
| ⑤ | Referral Source (Pie Chart) | All channels ~20% — Instagram leads slightly |
| ⑥ | Correlation Heatmap | UnitPrice → TotalPrice: r=0.72 (strongest) |
| ⑦ | Monthly Revenue Trend | Volatile trend; peak ~$68K in mid-2024 |

---

## 📊 Descriptive Statistics

| Metric | Quantity | UnitPrice | ItemsInCart | TotalPrice |
|---|---|---|---|---|
| **Mean** | 2.95 | $356 | 5.48 | $1,054 |
| **Median** | 3 | $364 | 5 | $824 |
| **Std** | 1.41 | $197 | 2.28 | $820 |
| **Min** | 1 | $11 | 1 | $11 |
| **Max** | 5 | $700 | 10 | $3,456 |

---

## 🔑 Key Findings

### 1. Revenue Distribution is Right-Skewed
- Mean ($1,054) > Median ($824) — high-value orders inflate the average
- ✅ **Action:** Segment customers into High / Mid / Low value tiers

### 2. 8 High-Value Outliers (IQR Method)
- All had Quantity = 5 and UnitPrice > $666 — likely bulk/VIP orders
- ✅ **Action:** Create a VIP segment and offer personalized deals

### 3. Chair & Printer Lead Revenue
- Chair: $195,620 | Printer: $195,613 — top 2 out of 7 products
- ✅ **Action:** Prioritize stock and promotions for these products

### 4. ~41% of Orders Are Cancelled or Returned
- Cancelled: 250 | Returned: 247 = 497 total orders lost
- ✅ **Action:** Investigate root causes; add return-reduction incentives

### 5. Instagram is the #1 Revenue Channel
- Instagram: $275K — highest among all referral sources
- ✅ **Action:** Increase Instagram marketing budget

### 6. UnitPrice is the Strongest Revenue Predictor
- r(UnitPrice, TotalPrice) = **0.717** | r(Quantity) = 0.615 | r(ItemsInCart) = 0.393
- ✅ **Action:** Focus on premium pricing over discount-driven volume

### 7. High Coupon Dependency
- 891 out of 1,200 orders (74%) used a coupon — FREESHIP is the most used
- ✅ **Action:** A/B test coupon removal to protect profit margins

---

## 🛠️ How to Run

### Requirements
```bash
pip install pandas numpy matplotlib seaborn
```

### Steps
1. Upload the CSV dataset to Google Colab at `/content/`
2. Open `P2.ipynb` in Google Colab
3. Run all cells (Runtime → Run All)

> **Note:** The dataset is not included in this repository for privacy reasons.  
> Please contact the project supervisor to obtain it.

---

## ✅ Portfolio Checklist

- [x] **Narrative Structure** — Problem → Methodology → Findings → Recommendations
- [x] **Technical Evidence** — Clean, modular, well-commented code
- [x] **Data Forensics** — Missing values handled; outliers detected via IQR
- [x] **Business Impact** — Findings quantified with $ values and correlations
- [x] **README** — Clear documentation for non-technical readers

---

## 👩‍💻 Author

**DecodeLabs Intern — Batch 2026**  
Data Analytics Track | Project 2 of 4

---

*"You are the translator between data and decision."* — DecodeLabs
