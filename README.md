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
| `Product` | Category | Product name (Chair, Laptop, Phone, Printer, Tablet, Monitor, Desk) |
| `Quantity` | Integer | Units ordered (1–5) |
| `UnitPrice` | Float | Price per unit ($11 – $700) |
| `ShippingAddress` | String | Shipping address |
| `PaymentMethod` | Category | Credit Card / Debit Card / Cash / Online / Gift Card |
| `OrderStatus` | Category | Delivered / Shipped / Pending / Returned / Cancelled |
| `TrackingNumber` | String | Shipment tracking number |
| `ItemsInCart` | Integer | Total items in cart at checkout (1–10) |
| `CouponCode` | Category | Coupon applied: FREESHIP / WINTER15 / SAVE10 / No Coupon |
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
3. **Descriptive Statistics** — Mean, Median, Std, Min/Max on `Quantity`, `UnitPrice`, `ItemsInCart`, `TotalPrice`
4. **Outlier Detection** — IQR Method on `TotalPrice` → 8 outliers detected (orders > $3,330)
5. **Correlation Analysis** — Pearson r between `Quantity`, `UnitPrice`, `ItemsInCart` vs `TotalPrice`
6. **Segmentation** — Revenue by Product, Channel, Payment Method, Coupon, Order Status
7. **Trend Analysis** — Monthly revenue over Jan 2023 – Jun 2025

---

## 📁 Project Structure

```
project-2-eda/
│
├── P2.ipynb                  ← Main notebook (all code + outputs)
├── executive_summary.py      ← Business Insights + KPI Dashboard
├── missing_plots.py          ← 5 additional visualizations
├── README.md                 ← This file
└── Dataset for Data Analytics 4(Sheet1).csv   ← Raw data (not uploaded)
```

---

## 📊 Visualizations Produced

| # | Chart | Key Insight |
|---|---|---|
| ① | TotalPrice Distribution (Histogram + KDE) | Right-skewed — Mean ($1,054) > Median ($824) |
| ② | TotalPrice Boxplot by Product | Price spread varies per product; 8 high-value outliers |
| ③ | Order Status Distribution (Bar) | Cancelled leads (250), Delivered is lowest (231) |
| ④ | Total Revenue by Product (Horizontal Bar) | Chair & Printer top revenue (~$196K each) |
| ⑤ | Referral Source (Pie Chart) | All channels ~20% each — Instagram leads slightly |
| ⑥ | Correlation Heatmap | UnitPrice → TotalPrice: r=0.72 (strongest) |
| ⑦ | Monthly Revenue Trend (2023–2025) | Volatile trend; peak ~$68K in mid-2024 |
| ⑧ | Revenue by Product (Vertical Bar) | Chair $196K → Phone $152K |
| ⑨ | Payment Methods (Pie Chart) | Online leads (258 orders), all methods roughly equal |
| ⑩ | Revenue by Referral Source (Vertical Bar) | Instagram $275K → Referral $227K |
| ⑪ | Avg Order Value by Product | Laptop $1,111 highest; Phone $973 lowest |
| ⑫ | Coupon Code Usage (Bar) | FREESHIP most used (313); 309 orders used no coupon |

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

## 🔑 Key Findings & Business Impact

### 1. Revenue Distribution is Right-Skewed
- **Mean ($1,054) > Median ($824)** → skewness = right-skewed
- **Business Impact:** A small group of high-value orders inflates the average. Marketing to the "average" customer misses ~60% of the base.
- ✅ **Action:** Segment customers into High / Mid / Low value tiers.

### 2. 8 High-Value Outliers Detected (IQR Method)
- IQR = $1,168 → Threshold = $3,330 — 8 orders exceeded this
- All outliers had Quantity = 5 and UnitPrice > $666
- **Business Impact:** These are likely bulk/VIP orders — valid signals, not data errors.
- ✅ **Action:** Create a VIP customer segment and offer personalized deals.

### 3. Chair & Printer Drive the Most Revenue
- Chair: $195,620 | Printer: $195,613 — top 2 out of 7 products
- **Business Impact:** These 2 products alone contribute ~29% of total revenue.
- ✅ **Action:** Prioritize stock & promotions for Chair and Printer.

### 4. ~41% of Orders Are Cancelled or Returned
- Cancelled: 250 orders | Returned: 247 orders = 497 total (41.4%)
- **Business Impact:** Nearly 1 in 3 orders never completes — major revenue leakage.
- ✅ **Action:** Investigate root causes; introduce return-reduction incentives.

### 5. Instagram is the #1 Revenue Channel
- Instagram: $275K — highest among all referral sources
- **Business Impact:** Instagram delivers the best ROI of all channels.
- ✅ **Action:** Increase Instagram marketing budget allocation.

### 6. UnitPrice is the Strongest Revenue Predictor
- Pearson r(UnitPrice, TotalPrice) = **0.717** — strongest correlation
- r(Quantity, TotalPrice) = 0.615 | r(ItemsInCart, TotalPrice) = 0.393
- **Business Impact:** Premium pricing strategy has a stronger revenue impact than selling volume.
- ✅ **Action:** Focus on premium product placement rather than discount-driven volume.

### 7. Coupon Dependency is High
- 891 out of 1,200 orders (74%) used a coupon
- Most popular: FREESHIP (313 uses)
- **Business Impact:** Heavy discount dependency may be eroding profit margins.
- ✅ **Action:** A/B test removing top coupon to measure revenue sensitivity.

---

## 📋 Revenue Summary by Product

| Product | Total Revenue | Avg Order | Orders |
|---|---|---|---|
| Chair | $195,620 | $1,099 | 178 |
| Printer | $195,613 | $1,081 | 181 |
| Laptop | $192,127 | $1,111 | 173 |
| Tablet | $186,569 | $1,042 | 179 |
| Monitor | $175,651 | $1,078 | 163 |
| Desk | $167,460 | $985 | 170 |
| Phone | $151,722 | $973 | 156 |

---

## 📋 Revenue by Year

| Year | Revenue |
|---|---|
| 2023 | $552,643 |
| 2024 | $480,236 |
| 2025 (Jan–Jun) | $231,883 |

---

## 🛠️ How to Run

### Requirements
```bash
pip install pandas numpy matplotlib seaborn
```

### Steps
1. Upload the CSV dataset to Google Colab at `/content/`
2. Open `P2.ipynb` in Google Colab
3. Run all cells in order (Runtime → Run All)
4. Optionally run `executive_summary.py` for business insights
5. Optionally run `missing_plots.py` for additional visualizations

> **Note:** The dataset file is not included in this repository for privacy reasons.  
> Please contact the project supervisor to obtain the dataset.

---

## ✅ Portfolio Checklist

- [x] **Narrative Structure** — Problem → Methodology → Findings → Recommendations
- [x] **Technical Evidence** — Clean, modular, well-commented code
- [x] **Data Forensics** — Missing values handled; 8 outliers detected via IQR Method
- [x] **Business Impact** — All findings quantified with $ values, counts, and correlations
- [x] **README** — Clear documentation for non-technical readers

---

## 👩‍💻 Author

**DecodeLabs Intern — Batch 2026**  
Data Analytics Track | Project 2 of 4

---

*"You are the translator between data and decision."* — DecodeLabs
