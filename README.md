# E-Commerce Customer Churn Analysis

*Analyzing customer churn patterns to identify high-risk customer segments and improve retention strategies.*

## 📖 Table of Contents

* [Project Overview](#-project-overview)
* [Data Source](#-data-source)
* [Tools & Technologies](#-tools--technologies)
* [Data Cleaning & Preparation](#-data-cleaning--preparation)
* [Exploratory Data Analysis (EDA)](#-exploratory-data-analysis-eda)
* [Key Insights](#-key-insights)
* [Recommendations](#-recommendations)
* [How to Use](#-how-to-use)

## 📊 Project Overview

This project analyzes customer churn behavior for a digital commerce platform experiencing high customer attrition. Using MySQL and Power BI, the analysis focuses on customer demographics, order behavior, payment methods, satisfaction levels, inactivity periods, and product preferences.

The goal of this project was to identify the main drivers behind customer churn and provide actionable business recommendations to improve customer retention and long-term revenue.

### Business Problem

The platform lacked visibility into:

* Which customer segments contribute the highest churn
* Whether new or long-term customers are more likely to leave
* How payment methods, coupons, and satisfaction scores affect retention
* Why highly active app users still churn
* How inactivity and delivery distance influence churn risk

### Business Impact

* Total Customers: 5,630
* Total Churned Customers: 948
* Overall Churn Rate: 16.8%
* Highest Risk Segment: Customers with 0–6 months tenure
* Most Critical Product Category: Mobile Phones

## 🗂️ Data Source

The dataset contains 5,630 customer records..

### Key Variables Included

| Category      | Columns                                                             |
| ------------- | ------------------------------------------------------------------- |
| Demographic   | CustomerID, Gender, MaritalStatus, CityTier                         |
| Behavioral    | Tenure, HourSpendOnApp, NumberOfDeviceRegistered, PreferredOrderCat |
| Transactional | OrderCount, OrderAmountHikeFromlastYear, CouponUsed, CashbackAmount |
| Engagement    | DaySinceLastOrder, PreferredLoginDevice, PreferredPaymentMode       |
| Feedback      | SatisfactionScore, Complain                                         |
| Logistics     | WarehouseToHome                                                     |

Source: The dataset was obtained from a publicly available source and used only for educational analysis.

## 🛠️ Tools & Technologies

* **Database:** MySQL
* **Visualization:** Power BI
* **Analysis:** DAX Measures, Calculated Columns
* **Documentation:** PDF Reports, Markdown

## 🧹 Data Cleaning & Preparation

Several data cleaning and transformation steps were performed before analysis:

1. Handled missing values in numeric columns using average values.
2. Standardized inconsistent text categories.

   * 'Phone' → 'Mobile Phone'
   * 'CC' → 'Credit Card'
   * 'COD' → 'Cash on Delivery'
3. Fixed logical inconsistencies in customer tenure values.
4. Treated outliers in delivery distance, cashback, and tenure.
5. Created calculated groups for:

   * Tenure Groups
   * Days Since Last Order Groups
   * Churn Rate
6. Built DAX measures to calculate churn percentage, repeat purchases, inactive customers, and customer segmentation.

### Example SQL Cleaning Logic

```sql
UPDATE customer_churn
SET WarehouseToHome = (
    SELECT AVG(WarehouseToHome)
    FROM customer_churn
)
WHERE WarehouseToHome IS NULL;
```

```sql
UPDATE customer_churn
SET Tenure = 1
WHERE Tenure = 0
AND OrderAmountHikeFromlastYear > 0;
```

## 🔍 Exploratory Data Analysis (EDA)

The following business questions were explored during the analysis:

| Business Question | Visualization Used |
|-------------------|-------------------|
| Which login devices have the highest churn? | Bar chart by device type |
| How does satisfaction score affect churn? | Churn rate by satisfaction score |
| Do new customers churn more than loyal customers? | Churn by tenure group |
| Does coupon usage improve retention? | Churn rate by coupon usage |
| How does inactivity predict churn? | Order activity by days since last order |
| Does app engagement matter? | Churn rate by hours spent on app |
| Which payment methods retain customers best? | Churn by preferred payment mode |
| Which product categories contribute the highest churn? | Churn count by preferred order category |
| Which city tiers have the highest churn? | Churn count by city tier |
| Does order frequency affect churn? | Churn by order count group |
| Does warehouse distance influence churn? | Churn by warehouse-to-home distance |
| Which gender contributes more to churn? | Churn count by gender |

## 💡 Key Insights

* **Insight 1:** Customers with 0–6 months tenure had the highest churn count, with 778 churned customers.
* **Insight 2:** Customers with only 0–2 orders showed the highest churn risk, proving that repeat purchases improve retention.
* **Insight 3:** Mobile Phone users represented the largest customer base and also contributed the highest churn volume.
* **Insight 4:** Cash on Delivery users had the highest churn rate, while Credit Card and UPI users were more loyal.
* **Insight 5:** Customers with satisfaction score 2 had the highest churn rate, while customers with score 5 had the lowest.
* **Insight 6:** Customers who did not use coupons were much more likely to churn.
* **Insight 7:** Customers inactive for more than 10 days were highly unlikely to return.
* **Insight 8:** Tier 1 cities showed the highest churn volume due to stronger competition and higher customer expectations.
* **Insight 9:** High app usage combined with high churn suggests browsing behavior without completed purchases.

## 🚀 Recommendations

Based on the analysis, the following actions are recommended:

* Improve the mobile shopping experience with faster checkout and abandoned cart notifications.
* Launch onboarding campaigns for customers within their first 6 months.
* Reduce dependency on Cash on Delivery by promoting UPI and Credit Card payments with cashback offers.
* Run reactivation campaigns for customers inactive for more than 10 days.
* Monitor pricing strategies for Mobile Phones and Accessories.
* Introduce loyalty programs and membership benefits for repeat customers.
* Collect post-purchase feedback to improve satisfaction scores.
* Improve delivery speed for customers located far from warehouses.
* Create separate retention campaigns for Tier 1 city customers.

## ⚙️ How to Use

### Prerequisites

* MySQL
* Power BI Desktop
* Git

### Setup Instructions

```bash
git clone https://github.com/saranyasubramaniam9787-ship-it/FUTURE_DS_02.git

# Open the project folder (MUST match the repo name)
cd FUTURE_DS_02 
```

### Run the Analysis

1. Open Power BI Desktop.
2. Import the customer churn dataset.
3. Apply the required SQL cleaning script if needed.
4. Create DAX measures and calculated columns.
5. Recreate the dashboard visuals.

### Repository Structure

```text
ecommerce-churn-analysis/
├── README.md
├── Customer Churn Analysis Dashboard.pdf
├── Customer Churn Analysis Documentation.pdf
├── Customer Churn One Page Key Findings Summary.pdf
├── E-Commerce Customer churn db (1).sql
└── data/
    └── customer_churn.csv
```

## 📈 Key Metrics Summary

| Metric                  | Value                   |
| ----------------------- | ----------------------- |
| Total Customers         | 5,630                   |
| Total Churned Customers | 948                     |
| Overall Churn Rate      | 16.8%                   |
| Highest Churn Segment   | Tenure 0–6 Months       |
| Lowest Churn Segment    | Credit Card / UPI Users |
| Most Critical Category  | Mobile Phones           |
| Inactivity Warning      | More Than 10 Days       |

