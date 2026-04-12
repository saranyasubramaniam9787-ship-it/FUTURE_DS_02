# 📊 Customer Churn Analysis

A comprehensive **Power BI analysis of customer churn behavior** on a digital platform. This project identifies key drivers of attrition—ranging from demographic profiles to engagement metrics—to help the business design targeted retention strategies and reduce customer loss.

---

## 📖 Table of Contents
- [Project Overview](#-project-overview)
- [Problem Statement](#-problem-statement)
- [Data Source & Attributes](#-data-source--attributes)
- [Tools & Technologies](#-tools--technologies)
- [Data Cleaning & Transformation](#-data-cleaning--transformation)
- [Key Insights](#-key-insights)
- [Recommendations](#-recommendations)
- [Conclusion](#-conclusion)

---

## 📊 Project Overview

**Objective:**  
To analyze customer churn behavior using behavioral and demographic metrics such as login device, satisfaction score, tenure, and order activity.

**Goal:**  
Identify key churn drivers and provide actionable insights to improve customer retention and lifetime value.

---

## 🔍 Problem Statement 

The digital commerce platform is experiencing a high churn rate (**~28%**), impacting repeat purchases and long-term revenue.

## Key Challenges:
- Lack of clarity on which customer segments contribute most to churn  
- Uncertainty about whether new or existing customers churn more  
- Weak understanding of how satisfaction scores relate to churn  
- Difficulty identifying inactivity as a churn predictor  

---

## 🗂️ Data Source & Attributes

The dataset contains **1500+ customer records** with demographic and transactional features:

| Column Name | Description |
|------------|------------|
| **Churn** | 1 = churned, 0 = active |
| **Tenure** | Customer lifetime (months) |
| **PreferredLoginDevice** | Mobile / Tablet / Desktop |
| **CityTier** | Tier 1, 2, or 3 |
| **WarehouseToHome** | Distance from warehouse (km) |
| **SatisfactionScore** | 1 (low) to 5 (high) |
| **Complain** | Complaint raised (1/0) |
| **DaySinceLastOrder** | Days since last purchase |

---

## 🛠️ Tools & Technologies

- **MySQL** → Data cleaning & preprocessing  
- **Power BI** → Dashboard & visualization  
- **Power Query** → ETL process  
- **DAX** → Calculated measures & KPIs  

---

## 🧹 Data Cleaning & Transformation

## 1. Handling Missing Values
- Numeric columns → Filled with **Mean**
- Categorical columns → Filled with **Mode**
- Satisfaction Score → Filled with **Median (3)**

## 2. Standardization & Fixes
- Unified inconsistent labels (e.g., *Phone → Mobile*)
- Outliers capped:
  - `WarehouseToHome` ≤ 100 km  
  - `Tenure` ≤ 60 months  
- Logical corrections applied for inconsistent records

## 3. Feature Engineering (DAX)
-- Churn Rate
Churn Rate = DIVIDE(SUM(Total_Churn), SUM(Total_Customers))

-- Tenure Group
Tenure Group = SWITCH(TRUE(), 
    [Tenure] <= 6, "0-6 Months", 
    [Tenure] <= 12, "6-12 Months", 
    "12+ Months")

## 💡 Key Insights

### 🏆 Churn Drivers
- **The Critical Window:** New customers (0–6 months tenure) contribute the most to churn.
- **Order Frequency:** Customers with 0–2 orders show the highest attrition.
- **Device Friction:** Mobile users churn more → possible UX issues.

### 📉 Behavioral Patterns
- **Satisfaction Paradox:** Even satisfied users churn.
- **Inactivity Risk:** 10+ days inactivity = high churn risk.
- **Category Stress:** Mobile Phones & Fashion show high churn.
- **City Impact:** Tier 1 cities have higher churn.

### 🚀 Recommendations
- Strong onboarding for first 6 months
- 24-hour complaint callback
- Family account feature
- Win-back campaigns

