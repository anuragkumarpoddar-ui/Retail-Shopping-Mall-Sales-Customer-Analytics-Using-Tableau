# 📊 Retail Customer Shopping & Multi-Mall Sales Performance Analysis (Tableau BI)

![Tableau](https://img.shields.io/badge/Tableau-v2026.3-E97627?style=for-the-badge&logo=tableau&logoColor=white)
![Data Analytics](https://img.shields.io/badge/Domain-Retail%20Analytics%20%26%20BI-0A66C2?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Dataset-99%2C457%20Invoices-2EA44F?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

> **Developed By:** **Anurag Kumar Poddar** — *Data Analyst / Business Analyst*  
> 📞 **Phone:** +91 9748748405 | 📧 **Email:** [anuragkumarpoddar@gmail.com](mailto:anuragkumarpoddar@gmail.com)

---

## 📌 Project Overview

This Business Intelligence project delivers an end-to-end, interactive executive diagnostic of retail customer shopping transactions across **10 major shopping malls in Istanbul** (`Jan 1, 2021 – Mar 8, 2023`). Built in **Tableau Desktop / Public (v2026.3)** using a validated dataset of **99,457 commercial invoices**, the **Sales Dashboard** transforms raw point-of-sale records into actionable retail intelligence across five core operational dimensions:

1. **Spatial Performance:** Revenue and footfall hierarchy across 10 shopping centers.
2. **Temporal & Seasonal Trends:** Monthly sales velocity and multi-year aggregation diagnostics.
3. **Product Portfolio Mix:** Pareto concentration and Average Order Value (AOV) across 8 retail categories.
4. **Customer Demographics:** Gender split and age-cohort purchasing behavior.
5. **Payment Channel Preferences:** Cash vs. digital card (Credit & Debit) transaction share.

---

## 🖥️ Interactive Dashboard Preview

<img width="1647" height="848" alt="Screenshot 2026-10-26 223509" src="https://github.com/user-attachments/assets/8eb6c476-2e4a-42e1-b420-a4987bb61810" />

*Figure 1: Complete Interactive Tableau Sales Dashboard developed by Anurag Kumar Poddar.*

---

## 🎯 Executive KPI Summary

| Metric | Value | Analytical Context |
| :--- | :---: | :--- |
| **Total Revenue (Sales)** | **251,505,794** | Gross sales across all 10 shopping malls |
| **Total Quantity Sold** | **298,712** | Average of **3.00 units** per transaction |
| **Average Order Value (AOV)** | **2,529** | Exact portfolio mean: **2,528.79** per invoice |
| **Total Valid Invoices** | **99,457** | 100% unique customer transactions (2 null records filtered) |

<img width="1442" height="162" alt="Screenshot 2026-10-26 223738" src="https://github.com/user-attachments/assets/4f39dc33-6df7-4453-a648-9478413d0fb9" />


---

## 🛠️ Data Architecture & Tableau Technical Implementation

The workbook (`Sales Dashboard.twb`) connects to `customer_shopping_data.csv` via Tableau's high-performance **Hyper in-memory extract engine**. Prior to aggregation, a shared categorical filter removes 2 corrupted/null rows from the raw 99,459-row dataset to guarantee 100% calculation accuracy across all 99,457 valid invoices.

### 1. Dataset Schema & Custom Calculated Fields

| Field / Calculation | Tableau Role & Type | Formula / Expression | Business Purpose |
| :--- | :--- | :--- | :--- |
| `invoice_no` | Dimension (`String`) | `COUNT([invoice_no])` | Unique transaction identifier driving **Total Invoices** (`99,457`) |
| **Sales** *(Calculated)* | Measure (`Real`) | `[price] * [quantity]` | Computes line-item gross revenue per transaction |
| **AOV** *(Calculated)* | Measure (`User Calc`) | `SUM([Sales]) / COUNT([invoice_no])` | Dynamic Average Order Value that recalculates across all active filters |
| `invoice_date` | Dimension (`Date`) | `MONTH([invoice_date])` | Aggregates multi-year transactions by calendar month |
| `shopping_mall` / `category` | Dimension (`String`) | Shared Filter: Exclude `%null%` | Segments revenue across 10 malls and 8 retail categories |
| `gender` / `payment_method` | Dimension (`String`) | Table Calc: `% of Total Sales` | Powers proportional pie chart wedge encodings |

### 2. Bi-Directional Dashboard Interactivity & Mobile Layout
* **5 Dynamic Filter Actions (`Action1` – `Action5`):** Every visual sheet (*Sales by Malls*, *Sales by Category*, *Sales by Gender*, *Sales by Payment Method*, and *Sales By Invoice Month*) is configured as an **On-Select Interactive Filter** targeting the entire dashboard with automatic clearing on deselection.
* **Responsive Device Layout:** Includes a dedicated **Phone Layout** (`1200px` vertical scroll container) for mobile executive viewing.

---

## 📈 Key Analytical Findings & Deep-Dive Diagnostics

### 1. Spatial Performance: Three-Tier Shopping Mall Hierarchy
<img width="1437" height="346" alt="Screenshot 2026-10-26 223616" src="https://github.com/user-attachments/assets/b47bd096-8529-4cf8-9b91-0e99d4a57539" />


| Shopping Mall | Tier Classification | Total Sales | Revenue Share | Units Sold | Total Invoices | Mall AOV |
| :--- | :--- | ---: | ---: | ---: | ---: | ---: |
| **Mall of Istanbul** | Tier 1: Co-Flagship | 50,872,481.68 | 20.23% | 60,114 | 19,943 | 2,550.89 |
| **Kanyon** | Tier 1: Co-Flagship | 50,554,231.10 | 20.10% | 59,457 | 19,823 | 2,550.28 |
| **Metrocity** | Tier 2: Core Regional | 37,302,787.33 | 14.83% | 44,894 | 15,011 | 2,485.03 |
| **Metropol AVM** | Tier 2: Core Regional | 25,379,913.19 | 10.09% | 30,530 | 10,161 | 2,497.78 |
| **Istinye Park** | Tier 2: Core Regional | 24,618,827.68 | 9.79% | 29,465 | 9,781 | 2,517.01 |
| **Zorlu Center** | Tier 3: Secondary | 12,901,053.82 | 5.13% | 15,234 | 5,075 | 2,542.08 |
| **Cevahir AVM** | Tier 3: Secondary | 12,645,138.20 | 5.03% | 14,949 | 4,991 | 2,533.59 |
| **Viaport Outlet** | Tier 3: Secondary | 12,521,339.72 | 4.98% | 14,716 | 4,914 | 2,548.10 |
| **Emaar Square Mall** | Tier 3: Secondary | 12,406,100.29 | 4.93% | 14,501 | 4,811 | 2,578.69 |
| **Forum Istanbul** | Tier 3: Secondary | 12,303,921.24 | 4.89% | 14,852 | 4,947 | 2,487.15 |

* **Diagnostic Insight:** **Mall of Istanbul** and **Kanyon** generate **40.33%** of total company revenue. Crucially, **AOV remains tightly bounded between `2,485` and `2,579` across all 10 malls**, proving that the 4x revenue gap between Tier-1 (~50.7M) and Tier-3 (~12.5M) malls is driven entirely by **customer footfall and transaction volume** (~19,900 bills vs. ~4,950 bills), not basket size.

---

### 2. Product Portfolio Mix: Extreme Pareto Concentration (94.79% in Top 3)
<img width="1442" height="762" alt="Screenshot 2026-10-26 223651" src="https://github.com/user-attachments/assets/78dfdb99-b501-4629-9f8d-2dcb93f03ef7" />


| Category | Total Sales | Revenue Share | Units Sold | Total Invoices | Invoice Share | Avg Unit Price | Category AOV |
| :--- | ---: | ---: | ---: | ---: | ---: | ---: | ---: |
| **Clothing** | 113,996,791.04 | **45.33%** | 103,558 | 34,487 | 34.68% | 901.08 | 3,305.50 |
| **Shoes** | 66,553,451.47 | **26.46%** | 30,217 | 10,034 | 10.09% | 1,807.39 | 6,632.79 |
| **Technology** | 57,862,350.00 | **23.01%** | 15,021 | 4,996 | 5.02% | 3,156.94 | **11,581.74** |
| **Cosmetics** | 6,792,862.90 | 2.70% | 45,465 | 15,097 | 15.18% | 122.45 | 449.95 |
| **Toys** | 3,980,426.24 | 1.58% | 30,321 | 10,087 | 10.14% | 107.73 | 394.61 |
| **Food & Beverage** | 849,535.05 | 0.34% | 44,277 | 14,776 | 14.86% | 15.67 | 57.49 |
| **Books** | 834,552.90 | 0.33% | 14,982 | 4,981 | 5.01% | 45.57 | 167.55 |
| **Souvenir** | 635,824.65 | 0.25% | 14,871 | 4,999 | 5.03% | 34.89 | 127.19 |

* **Volume Anchor vs. Ticket Multiplier:** **Clothing**, **Shoes**, and **Technology** generate **94.79%** of total revenue (`238.41M`). While **Clothing** drives the highest footfall (`34.68%` of all bills), **Technology** commands an extraordinary AOV of **`11,581.74`** (4.6x the portfolio average).
* **Cross-Sell Opportunity:** **Cosmetics** (`15.18%` of bills) and **Food & Beverage** (`14.86%` of bills) represent **30.04% of all customer checkouts** but contribute just `3.04%` of revenue due to low unit prices, making them ideal triggers for cross-category voucher bundling.

---

### 3. Temporal & Seasonal Dynamics: Sales by Invoice Month
<img width="1440" height="762" alt="Screenshot 2026-10-26 223701" src="https://github.com/user-attachments/assets/3abceb4d-3c84-4fe5-b575-045ef5dd0179" />


* **Apparent Q1 Peak vs. Underlying Multi-Year Coverage:** Aggregated monthly sales peak in **January (`28.89M`)** and **February (`26.63M`)**, taper in **March (`21.96M`)**, and stabilize between **`18.21M` and `20.55M`** from April through December.
* **Root-Cause Audit:** The dataset spans two full calendar years (**2021:** `114.56M` across `45,382` bills; **2022:** `115.44M` across `45,551` bills) plus **Q1 2023 through March 8, 2023** (`21.51M` across `8,524` bills). Because `MONTH(Invoice Date)` aggregates across years, January and February stack **3 calendar years of transactions**, whereas April–December stack **2 years**. Normalized annually, monthly demand is highly stable (~`9.5M–10.3M`/month), with true single-year seasonal peaks in **October** (`10.27M`/yr; highest AOV at `2,646.20`) and **July** (`10.19M`/yr).

---

### 4. Customer Demographics & Payment Channel Mix

| Payment Method Breakdown | Customer Gender Split |
| :---: | :---: |
<img width="1175" height="672" alt="Screenshot 2026-10-26 223625" src="https://github.com/user-attachments/assets/ab5c4708-84a8-42f4-96ce-3e3466bfc8f0" />
<img width="1111" height="660" alt="Screenshot 2026-10-26 223639" src="https://github.com/user-attachments/assets/17c19ae7-c086-46e5-af38-c65b3480eb19" />



* **Gender Segmentation:** **Female shoppers** generate **59.72% of revenue** (`150,207,136` across `59,482` bills; AOV `2,525.25`), while **Male shoppers** account for **40.28%** (`101,298,658` across `39,975` bills; AOV `2,534.05`). Because AOV is nearly identical between genders, higher Female revenue is purely a function of **1.49x higher shopping frequency**.
* **Payment Preferences:** **Cash** is the single largest payment method at **44.86%** (`112.83M` / `44,447` bills), but combined digital card payments (**Credit Card `35.02%`** + **Debit Card `20.12%`**) account for **55.14%** (`138.67M`) of total sales.

---

## 💡 Strategic Business & BI Recommendations

1. **Cross-Category Voucher Bundling (Cosmetics & F&B → Apparel):** Issue automated POS discount vouchers (e.g., *10% off Clothing or Shoes on Cosmetics/F&B bills above 150*) across the `29,873` high-frequency impulse transactions to lift portfolio AOV by **+5% to +8%**.
2. **Cash-to-Digital Card Migration:** Partner with issuing banks to offer instant 3% cashback or zero-cost EMI on Credit/Debit transactions in **Technology** (`AOV 11,582`) and **Shoes** (`AOV 6,633`), reducing physical cash-handling overhead (`44.86%` share) by **15%–20%**.
3. **Tier-3 Mall Footfall Activation:** Since Tier-3 malls (*Zorlu Center, Cevahir AVM, Viaport Outlet, Emaar Square, Forum Istanbul*) already match flagship AOV (≈ `2,535`), reallocate localized weekend event marketing and Female loyalty campaigns to boost footfall by **12%–15%** (≈ `9M+` incremental revenue).
4. **Dashboard v2.0 Roadmap:** Introduce a `YEAR(Invoice Date)` context filter and YoY Growth % KPI cards to separate full-year comparisons (2021 vs. 2022) from partial-year 2023 data.

---


## 📂 Repository File Structure

```text
├── customer_shopping_data.csv                              # Raw retail transaction dataset (99,457 valid rows)
├── Sales Dashboard.twb                                     # Tableau Desktop / Public Workbook (v2026.3)
├── Screenshot 2026-10-26 223509.png                        # Full Interactive Sales Dashboard Screenshot
├── Screenshot 2026-10-26 223738.png                        # KPI Summary Banner Screenshot
├── Screenshot 2026-10-26 223616.png                        # Sales by Malls Bar Chart Screenshot
├── Screenshot 2026-10-26 223701.png                        # Sales by Invoice Month Line Chart Screenshot
├── Screenshot 2026-10-26 223651.png                        # Sales by Category Packed Bubble Chart Screenshot
├── Screenshot 2026-10-26 223639.png                        # Sales by Gender Pie Chart Screenshot
├── Screenshot 2026-10-26 223625.png                        # Sales by Payment Method Pie Chart Screenshot
├── Tableau_Sales_Dashboard_Project_Report_Anurag_Kumar_Poddar.pdf   # Executive Project Report (PDF)
├── Tableau_Sales_Dashboard_Project_Report_Anurag_Kumar_Poddar.docx  # Executive Project Report (MS Word)
└── README.md                                               # Project Documentation

