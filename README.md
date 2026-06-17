# 🍽️ Chills Restaurant Group — Q1 2026 Sales Performance Dashboard

![Dashboard Preview](./Dashboard/Chill%20Restaurant%20Analysis%20Dashboard.jpg)

---

## 📌 Project Overview

This project covers the end-to-end data analysis workflow for **Chills Restaurant Group**, a multi-branch Nigerian restaurant chain operating across **Lekki, Ikeja, Abuja, and Victoria Island**. The analysis examines sales performance, profitability, and operational metrics across the first quarter of 2026 using transactional data from 458 orders.

The work was split into two clear phases: **data cleaning** and **dashboard development**. Both were done entirely in Excel and Power Query — no external BI tools, no scripts, just Excel done properly.

---

## 📑 Table of Contents

- [🗂️ Project Structure](#-project-structure)
- [⚠️ The Data Problem](#️-the-data-problem)
- [🧹 Case Study 1 — Data Cleaning](#-case-study-1--data-cleaning)
- [📊 Case Study 2 — Sales Performance Dashboard](#-case-study-2--sales-performance-dashboard)
- [📈 Dashboard Sections & Key Findings](#-dashboard-sections--key-findings)
  - [🔢 KPI Summary Cards](#-kpi-summary-cards)
  - [📅 Monthly Revenue & Profit Trend](#-monthly-revenue--profit-trend)
  - [🍛 Revenue by Menu Category](#-revenue-by-menu-category)
  - [🏢 Revenue by Branch](#-revenue-by-branch)
  - [🍝 Top 10 Selling Dishes by Revenue](#-top-10-selling-dishes-by-revenue)
  - [👨‍🍳 Revenue by Waiter](#️-revenue-by-waiter)
  - [💸 Average Discount by Branch](#-average-discount-by-branch)
- [🛠️ Tools & Techniques Used](#️-tools--techniques-used)
- [💡 Recommendations from the Analysis](#-recommendations-from-the-analysis)
- [🚀 How to Use This Project](#-how-to-use-this-project)
- [👤 About the Analyst](#-about-the-analyst)
- [📄 License](#-license)

---

## 🗂️ Project Structure

```
chills-restaurant-q1-2026/
│
├── data/
│   ├── Chills_Restaurant_Raw_Data.xlsx        # Original messy dataset
│   └── Chills_Restaurant_Data_Cleaned.xlsx    # Cleaned & transformed dataset
│
├── dashboard/
│   └── Chills_Restaurant_Q1_Dashboard.xlsx    # Final Excel dashboard
│
├── assets/
│   └── dashboard_preview.png                  # Dashboard screenshot
│
└── README.md
```

---

## ⚠️ The Data Problem

Before anything else, the raw dataset needed serious work. It was not analysis-ready — there were multiple quality issues that would have thrown off any calculations or visuals if left untreated.

Here is what was found and fixed:

| Issue | Example | Fix Applied |
|---|---|---|
| Inconsistent branch names | `LEKKI`, `lekki`, `Lekki` | Standardised to proper case across all entries |
| Date stored as Excel serial number | `46105` instead of `03/01/2026` | Converted to `DD/MM/YYYY` short date format |
| Waiter name inconsistencies | `Amaka O` vs `Amaka O.` | Unified naming convention applied |
| Missing punctuation in names | `Amaka O` (no full stop) | Corrected for consistency |
| Discount stored as decimal | `0.05` instead of `5%` | Formatted as percentage for readability |
| Blank and null fields | Missing dish sub-categories | Filled appropriately or flagged |

---

## 🧹 Case Study 1 — Data Cleaning

**Tools Used:** Microsoft Excel, Power Query

The raw file came in as a single flat table with 11 columns and close to 460+ transaction rows covering all four branches across the three months. Power Query was used as the primary cleaning engine, and all transformations were saved as a reusable query rather than one-off edits.

**Steps Taken:**

1. **Loaded raw data into Power Query** — kept the original sheet untouched as a backup reference
2. **Standardised text fields** — used *Transform > Format > Capitalise Each Word* to fix branch names, waiter names, and category labels
3. **Converted date serial numbers** — changed the data type of the Order Date column from whole number to date, which automatically resolved the Excel serial date issue
4. **Trimmed whitespace** — removed leading and trailing spaces that were causing mismatches in pivot tables
5. **Verified data types** — ensured numeric columns (Unit Price, Cost Per Dish, Discount Rate, Qty Sold) were set to the correct types
6. **Added calculated columns** — created three helper columns directly in Power Query:
   - `Total Revenue` = Unit Price × Qty Sold × (1 - Discount Rate)
   - `Total Cost` = Cost Per Dish × Qty Sold
   - `Total Profit` = Total Revenue - Total Cost
7. **Extracted Month Name** from Order Date for monthly trend slicing
8. **Closed and loaded** the clean query to a new sheet for dashboard use

The cleaned dataset was structured, consistent, and ready for pivot analysis with no further manual intervention needed.

---

## 📊 Case Study 2 — Sales Performance Dashboard

**Tool Used:** Microsoft Excel (PivotTables, PivotCharts, Slicers, Dashboard Layout)

The dashboard was built on top of the cleaned dataset using PivotTables and PivotCharts, with slicers for interactive filtering by **Month** (Jan, Feb, Mar) and **Branch** (Abuja, Ikeja, Lekki, Victoria Island). The layout was designed to fit on a single screen, making it easy to share as a standalone view. No pivot table is directly visible on the dashboard — all charts and KPI cards are fed from them, giving a polished, business-ready appearance.

---

## 📈 Dashboard Sections & Key Findings

### 🔢 KPI Summary Cards

| Metric | Q1 2026 Value |
|---|---|
| Orders Served | 458 |
| Total Revenue | ₦4.47M |
| Total Profit | ₦919K |
| Profit Margin | 20.6% |
| Average Discount | 5.6% |

A 20.6% profit margin across 458 orders in a single quarter is a reasonable baseline, but there is room to push this higher — particularly by reviewing the discount structure at high-traffic branches and identifying cost-saving opportunities at lower-performing locations.

---

### 📅 Monthly Revenue & Profit Trend

The line chart tracking monthly revenue and profit shows a reasonably consistent performance across January, February, and March. Revenue stayed in the ₦1.4M–₦1.6M range each month with no significant dips or seasonal spikes during this quarter, suggesting stable underlying demand.

---

### 🍛 Revenue by Menu Category

| Category | Revenue Share |
|---|---|
| Main Course | 57% |
| Starters | 28% |
| Beverages | 15% |

Main Course drives more than half of total revenue — which makes sense given the price points of dishes like Spaghetti Bolognese, Grilled Tilapia, and Suya Platter. Beverages at only 15% is worth investigating; a modest upselling push here could move the needle.

---

### 🏢 Revenue by Branch

| Branch | Revenue |
|---|---|
| Lekki | ₦1.27M |
| Ikeja | ₦1.17M |
| Abuja | ₦1.07M |
| Victoria Island | ₦0.96M |

Lekki leads the pack, but the spread between the top (Lekki) and the bottom (Victoria Island) is about ₦310K — not a massive gap, but it points to Victoria Island underperforming relative to its peers.

---

### 🍝 Top 10 Selling Dishes by Revenue

| Rank | Dish | Revenue |
|---|---|---|
| 1 | Spaghetti Bolognese | ₦331K |
| 2 | Seafood Pasta | ₦300K |
| 3 | Grilled Tilapia | ₦287K |
| 4 | Suya Platter | ₦275K |
| 5 | Ofe Onugbu | ₦237K |
| 6 | Banga Stew | ₦217K |
| 7 | Egusi Soup & Pounded Yam | ₦210K |
| 8 | Jollof Rice | ₦203K |
| 9 | Grilled Prawns | ��197K |
| 10 | Coconut Rice | ₦186K |

The interesting story here is the mix — both continental dishes (Spaghetti Bolognese, Seafood Pasta) and Nigerian staples (Ofe Onugbu, Banga Stew, Egusi Soup) are performing strongly. The top ten dishes account for a significant portion of total revenue, so consistency and quality control for these items are critical.

---

### 👨‍🍳 Revenue by Waiter

| Waiter | Revenue Generated |
|---|---|
| Emeka S. | ₦853K |
| Ngozi A. | ₦850K |
| Fatima B. | ₦764K |
| Bayo K. | ₦715K |
| Amaka O. | ₦646K |
| Chidi N. | ₦642K |

Emeka S. and Ngozi A. are essentially neck-and-neck at the top, each pulling in around ₦850K. The ₦200K+ gap between the top two and the bottom two (Amaka O. and Chidi N.) is worth investigating — it may reflect experience, shift allocation, or upselling skill.

---

### 💸 Average Discount by Branch

| Branch | Avg. Discount (%) |
|---|---|
| Lekki | 7.75% |
| Ikeja | 6.25% |
| Abuja | 6.05% |
| Victoria Island | 5.45% |

Lekki has both the highest revenue *and* the highest average discount. This raises a question: is the Lekki branch relying on discounting to drive volume, and if so, is that sustainable? Tightening the discount policy there could improve margins without losing too much volume.

---

## 🛠️ Tools & Techniques Used

| Tool | Purpose |
|---|---|
| **Microsoft Excel** | Dashboard layout, PivotTables, PivotCharts, KPI cards, formatting |
| **Power Query** | Data cleaning, transformation, calculated columns, date formatting |
| **Excel Slicers** | Interactive month and branch filtering on the dashboard |
| **Conditional Formatting** | Visual cues on KPI cards and bar charts |

---

## 💡 Recommendations from the Analysis

Based on what the dashboard surfaces, here are a few things worth acting on:

1. **Review the discount policy at Lekki** — 7.75% average discount is the highest across all branches. If this is a blanket promotional practice rather than targeted offers, it is likely eroding margins.

2. **Investigate Victoria Island's underperformance** — it is the lowest revenue branch and the lowest discount branch. Low discounting with low revenue suggests demand-side issues, not a cost structure problem.

3. **Double down on the top dishes** — Spaghetti Bolognese and Seafood Pasta are clear revenue leaders. Ensuring consistent availability, quality, and portion accuracy for these two dishes specifically will protect and grow revenue.

4. **Beverage upselling opportunity** — at 15% revenue contribution, beverages are underperforming relative to their potential. Training staff to pair beverage recommendations with food orders could boost this category by 3–5%.

5. **Understand the waiter performance gap** — the ₦200K+ difference between the top and bottom waiters is worth a structured conversation. If it comes down to upselling behaviour, targeted training for the lower performers could narrow the gap.

---

## 🚀 How to Use This Project

1. Download the Excel files from this repository
2. Open `Chills_Restaurant_Data_Cleaned.xlsx` to review the cleaned dataset and Power Query steps
3. Open `Chills_Restaurant_Q1_Dashboard.xlsx` to interact with the dashboard
4. Use the **Month** and **Branch** slicers on the dashboard to filter views by time period or location
5. All KPI cards and charts update automatically based on slicer selection

---

## 👤 About the Analyst

This project was done by **Favour Chidozie Chukwu**, a Data and Credit Risk Analyst with hands-on experience in financial data analysis, reporting, and business intelligence across Nigerian financial institutions.

- 📧 Email: [favour.chukwu@aol.com](mailto:favour.chukwu@aol.com)
- 💼 LinkedIn: [linkedin.com/in/chidozie-chukwu-145690162](https://www.linkedin.com/in/chidozie-chukwu-145690162)
- 📸 Instagram: [@chidozie_favor](https://www.instagram.com/chidozie_favor?igsh=aG94eWNnbzR4NzA=)

---

## 📄 License

This project is open for reference and learning purposes. If you use or adapt any part of it, a mention would be appreciated.

---

*Built with Microsoft Excel · Power Query · A lot of coffee ☕*
