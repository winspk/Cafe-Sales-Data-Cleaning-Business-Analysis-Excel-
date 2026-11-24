# Cafe-Sales-Data-Cleaning-Business-Analysis-Excel-# Cafe Sales Data Cleaning & Business Analysis (2023)

This project covers data cleaning and business sales analysis for a cafe dataset in 2023 (`cafe_project.xlsx`), based on the cleaning formulas in the **`Cleaning_data`** sheet and summary tables in the **`Business`** sheet, prepared as a **Data Analyst** internship portfolio.

---

## 1. Executive Summary

* **Analyzed Transactions (After Cleaning):** 9,540 records (from 10,000 raw records in `dirty_cafe_sales`)
* **Total Annual Revenue (`Grand Total`):** **85,121**
* **Total Quantity Sold (`Grand Total`):** **28,834** units
* **Average Monthly Revenue (`Avg`):** **7,093.42**

---

## 2. Data Cleaning Process



Based on **`Cleaning_data`** (`Table2`) and **`Data analysis`**:

* **Unit Price (`fixed_price_per_units`):** Keeps numeric values when available; otherwise derives price from `Total Spent / Quantity` or looks up by `Item` via `VLOOKUP` (`$P$3:$Q$9`), with a fallback value of `3`.
* **Item Name (`fixed_item`):** Keeps existing item names when present; otherwise looks up item by unit price via `VLOOKUP` (`$P$21:$Q$26`), with a fallback value of `"Coffee"`.
* **Quantity (`fixed_quantity`) & Total Spent (`fixed_total_spent`):** Estimates missing quantities using `ROUND(Total Spent / fixed_price_per_units, 0)` (fallback `3`), then recalculates `fixed_total_spent` as `fixed_quantity * fixed_price_per_units`.
* **Payment Method & Location:** Populates category values (`Digital Wallet`, `Cash`, `Credit Card` and `Takeaway`, `In-store`) and pulls cleaned fields into `Data analysis` via `VLOOKUP`.

<img width="1421" height="532" alt="Screenshot 2026-11-24 213209" src="https://github.com/user-attachments/assets/c9300057-0123-4147-b27d-1a80b30da4c7" />

---

## 3. Revenue & Quantity by Item

| Item | Price_Tier | Sum of Total Spent | Income Ratio (%) | Sum of Quantity | Quantity Ratio (%) |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Salad** | 5 | 18,224 | 21.41% | 3,646 | 12.64% |
| **Sandwich** | 4 | 15,640 | 18.37% | 3,910 | 13.56% |
| **Smoothie** | 4 | 12,796 | 15.03% | 3,202 | 11.10% |
| **Juice** | 3 | 12,054 | 14.16% | 4,018 | 13.93% |
| **Cake** | 3 | 9,843 | 11.56% | 3,281 | 11.38% |
| **Coffee** | 2 | 8,014 | 9.41% | 3,937 | 13.65% |
| **Tea** | 1.5 | 5,130 | 6.03% | 3,420 | 11.86% |
| **Cookie** | 1 | 3,420 | 4.02% | 3,420 | 11.86% |
| **Total** | — | **85,121** | **100.00%** | **28,834** | **100.00%** |
<img width="557" height="243" alt="image" src="https://github.com/user-attachments/assets/46d42cde-9653-4f14-8296-27227be99037" />
<img width="587" height="297" alt="image" src="https://github.com/user-attachments/assets/3186de88-7288-4825-bacf-4788bf0308eb" />

---

## 4. Analysis by Price Tier (`Price_Tier`)

| Price_Tier | Item | Total_Revenue | Income Ratio (%) | Total_Quantity | Quantity Ratio (%) |
| :---: | :--- | :---: | :---: | :---: | :---: |
| **4 $** | Smoothie, Sandwich | 28,436 | 33.41% | 7,112 | 24.67% |
| **3 $** | Cake, Juice | 21,897 | 25.72% | 7,299 | 25.31% |
| **5 $** | Salad | 18,224 | 21.41% | 3,646 | 12.64% |
| **1-1.5 $** | Cookie, Tea | 8,550 | 10.04% | 6,840 | 23.72% |
| **2 $** | Coffee | 8,014 | 9.41% | 3,937 | 13.65% |
| **Total** | — | **85,121** | **100.00%** | **28,834** | **100.00%** |
<img width="771" height="462" alt="image" src="https://github.com/user-attachments/assets/52289389-0d0b-47c8-9851-e8d6084155ff" />

---

## 5. Monthly Revenue Trend (`Jan` – `Dec`)

* **Jan:** 7,281
* **Feb:** 6,656 *(Lowest)*
* **Mar:** 7,223
* **Apr:** 7,203
* **May:** 7,009.5
* **Jun:** 7,359 *(Highest)*
* **Jul:** 6,885
* **Aug:** 7,112.5
* **Sep:** 6,889
* **Oct:** 7,326
* **Nov:** 6,967
* **Dec:** 7,210
* **Grand Total:** **85,121** | **Avg:** **7,093.42**
<img width="656" height="400" alt="image" src="https://github.com/user-attachments/assets/4fbddfe7-9585-4fd5-9c8d-5fbefc294259" />

---

## 6. Business Insights & Actionable Recommendations

### 6.1 Price Tier Analysis (`4–5 $`, `2–3 $`, `1–1.5 $`)
* **Price Tier `4–5 $`:** Core items of the cafe such as Salad, Smoothie, and Sandwich account for only **37.31%** of total sales volume, yet generate **54.82%** of total revenue.
  * **Action:** Highlight this menu group as **Hero Products** to encourage customers to order items with higher bill value.
* **Price Tier `2–3 $`:** Items focused on high sales volume such as Coffee, Cake, and Juice account for **38.96%** of total sales volume and generate **35.13%** of total revenue.
  * **Action:** Coffee sales volume is at **13.65%**, the second highest after Juice at **13.93%**. From this high purchase volume, consider testing a **+1 $ price increase** to push revenue contribution higher.
* **Price Tier `1–1.5 $`:** Cookie sales volume is **11.86%** while generating **4.02%** of total revenue; Tea sales volume is **11.86%** and revenue share is **6.03%**. Total sales volume is **23.72%** and total revenue is **10.04%**.
  * **Action:** Focus on selling **Cookie** as a special-priced **add-on** paired with drinks to help boost sales.

### 6.2 Monthly Revenue Strategy (`February`)
* **February:** In February, run a promotion to buy **Juice (3 $)** paired with **Sandwich (4 $)** at a special price of **6.5 $**, since Juice is the #1 best-selling item in the beverage category and Sandwich is the #1 best-selling item in the snack/food category, in order to help stimulate order volume in February.
---

## 7. Tools Used
* **Microsoft Excel** (Data Cleaning Formulas, `VLOOKUP`, PivotTables, Ratio Calculations)
