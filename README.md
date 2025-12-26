## Problem Statement

Customer churn is the number of existing customers lost, for any reason at all, over a given period of time. It provides companies with an understanding of customer satisfaction and customer loyalty, and can identify potential changes in a company’s bottom line. (IBM)

---

The goal of this project is to:
- Analyze customer behavior
- Identify factors contributing to churn
- Build a predictive model to identify high-risk customers
- Provide data-driven retention strategies

---

## Dataset
**Source:** Telco Customer Churn Dataset  
**Size:** 7,043 customers, 33 features  

**Target Variable:**
- `Churn Value` (1 = Churned, 0 = Not Churned)

**Feature Types:**
- **Demographic:** Gender, Senior Citizen, Dependents
- **Service-related:** Internet Service, Online Security, Tech Support, Streaming Services
- **Account & Billing:** Contract Type, Payment Method, Monthly Charges, Total Charges
- **Tenure-based:** Tenure Months

---
## Exploratory Data Analysis (EDA)
- Analyzed churn distribution and class imbalance
- Identified strong relationships between churn and:
  - Contract type
  - Tenure duration
  - Monthly and total charges
- Visualized correlations and key trends using plots and heatmaps

---

## Feature Engineering & Preprocessing
- Removed identifier and leakage columns
- Converted `Total Charges` to numeric format
- Applied **One-Hot Encoding** to categorical features
- Standardized numerical features using **StandardScaler**
- Performed stratified train-test split to preserve churn distribution

---

## Modeling Approach
Two models were trained and compared:

### 1. Logistic Regression (Baseline)
- Provides interpretability
- Serves as a strong baseline for churn prediction

### 2. Random Forest Classifier
- Captures non-linear relationships and feature interactions
- Achieved improved performance over the baseline model

**Evaluation Metrics:**
- ROC-AUC
- Recall
- Precision
- F1-score

ROC-AUC and Recall were prioritized due to the business importance of identifying churn-prone customers.

---

## Feature Importance
Feature importance analysis from the Random Forest model revealed that the most influential churn drivers are:
- Total Charges
- Tenure Months
- Monthly Charges
- Contract Type
- Payment Method
- Value-added services such as Online Security

---

## Business Insights
- Customers on **month-to-month contracts** are significantly more likely to churn
- **Early-tenure customers** show higher churn risk
- Higher **monthly charges** increase churn probability
- Customers with **online security and support services** churn less frequently

---

## Business Recommendations
- Incentivize customers to switch from month-to-month to long-term contracts
- Focus retention campaigns on customers within their first year
- Introduce personalized pricing or loyalty discounts for high-paying customers
- Bundle value-added services to improve customer retention

---

## Tools & Technologies
- Python
- pandas, NumPy
- scikit-learn
- Matplotlib
- Jupyter Notebook
