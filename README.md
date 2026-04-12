# Customer Churn Analysis

A comprehensive **Power BI analysis of customer churn behavior** on a digital platform. This project identifies key drivers of attrition—ranging from demographic profiles to engagement metrics—to help the business design targeted retention strategies and reduce customer loss.

---

# 📖 Table of Contents
- [Project Overview](#-project-overview)
- [Problem Statement](#-problem-statement)
- [Data Source & Attributes](#-data-source--attributes)
- [Tools & Technologies](#-tools--technologies)
- [Data Cleaning & Transformation](#-data-cleaning--transformation)
- [Key Insights](#-key-insights)
- [Recommendations](#-recommendations)
- [Conclusion](#-conclusion)

---

# 📊 Project Overview

**Objective:**  
To analyze customer churn behavior on a digital platform using key behavioral and demographic metrics. The analysis aims to identify which factors—such as login device, satisfaction score, tenure, and order activity—are most strongly associated with customer attrition.

---

# 🔍 Problem Statement 

The digital commerce platform is experiencing a high churn rate (**~28%**), leading to reduced repeat purchases and a negative impact on long-term revenue growth. 

**Key Challenges addressed:**
*   Lack of visibility into which customer segments contribute to the highest churn.
*   Uncertainty regarding whether new or long-term customers are more likely to leave.
*   Unclear relationship between customer satisfaction scores and actual churn behavior.
*   Identifying if inactivity (days since last order) accurately predicts churn risk.

---

# 🗂️ Data Source & Attributes

The dataset consists of 1,500+ customer records capturing demographic and transactional attributes:


| Column Name | Description |
| :--- | :--- |
| **Churn** | Binary flag (1 if churned, 0 if active). |
| **Tenure** | Months the customer has been with the platform. |
| **PreferredLoginDevice** | Device used most often (Mobile, Tablet, Desktop). |
| **CityTier** | Tier classification of the customer’s city (1, 2, or 3). |
| **WarehouseToHome** | Distance (km) from delivery hub to home. |
| **SatisfactionScore** | Customer-reported score (1 = Very Dissatisfied, 5 = Very Satisfied). |
| **Complain** | Flag (1) if a complaint was filed in the last year. |
| **DaySinceLastOrder** | Number of days since the most recent purchase. |

---

# 🛠️ Tools & Technologies

*   **MySQL:** Data cleaning and initial transformation.
*   **Power BI:** Data modeling, DAX calculations, and interactive dashboard creation.
*   **Power Query:** ETL (Extract, Transform, Load) processes.

---

# 🧹 Data Cleaning & Transformation

Extensive preprocessing was performed to ensure data integrity and model accuracy:

## 1. Handling Missing Values
*   **Numeric Columns:** (Tenure, OrderCount, etc.) Filled with the **Mean**.
*   **Categorical Columns:** (Gender, MaritalStatus, etc.) Filled with the **Mode**.
*   **Satisfaction Score:** Filled with the **Median (3)**.

## 2. Standardization & Logic Fixes
*   **Text Unification:** Unified synonyms (e.g., 'CC' → 'Credit Card', 'Phone' → 'Mobile Phone').
*   **Outlier Treatment:** Capped `WarehouseToHome` at 100km and `Tenure` at 60 months to remove data entry errors.
*   **Logical Consistency:** Adjusted `Tenure` to 1 for new customers showing a year-over-year order hike.

## 3. Feature Engineering (DAX)
```DAX
-- Churn Rate Calculation
Churn Rate = DIVIDE(SUM(Total_Churn), SUM(Total_Customers))

-- Tenure Grouping
Tenure Group = SWITCH(TRUE(), 
    [Tenure] <= 6, "0-6 Months", 
    [Tenure] <= 12, "6-12 Months", 
    "12+ Months")
## 💡 Key Insights

### 🏆 Churn Drivers
- **The Critical Window:** New customers (0–6 months tenure) contribute the most to churn.
- **Order Frequency:** Customers with 0–2 orders show the highest attrition, meaning users drop off very early.
- **Device Friction:** Mobile users dominate the platform but also churn more, suggesting potential App UX/performance issues.

---

### 📉 Behavioral Patterns
- **The Satisfaction Paradox:** Churn is highest in scores 2 and 3, but even users with high satisfaction still leave, indicating strong competition.
- **Inactivity Risk:** Users inactive for 10+ days are significantly more likely to churn.
- **Category Stress:** Mobile Phones and Fashion categories experience the highest customer loss.
- **City Impact:** Tier 1 cities show the highest churn rates, likely due to a more competitive market.

---

### 🚀 Recommendations
- **Onboarding Strategy:**  
  Implement strong *first-purchase offers* and nurturing programs for customers in their first 6 months.

- **Proactive Complaint Recovery:**  
  Set up an automatic retention call-back within 24 hours for any customer complaint.

- **Stickiness Tactics:**
  - Introduce a **"Family Account"** feature for users with 3+ addresses.
  - Offer a **5% discount** for registering a second device (Tablet or Desktop).

- **Win-Back Campaigns:**  
  Identify customers with negative order trends and send targeted offers within 7 days.

- **Logistics Management:**  
  For customers located >30km from a warehouse, offer  
  **"Slower Delivery = Extra Cashback"** to manage expectations.

---

### 🏁 Conclusion
Customer churn is significantly high (~28%), with the **early stage (0–6 months)** being the most critical period for drop-offs.

