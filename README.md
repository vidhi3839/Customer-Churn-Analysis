# Customer Churn Prediction: Decision Intelligence for Retention

## Project Overview
This project addresses a critical business question: **Which customers should we intervene on NOW, given limited retention budget?**

Rather than simply predicting churn, this analysis provides a complete decision framework that:
- Identifies high-risk customers before they leave
- Quantifies the ROI of intervention strategies  
- Delivers specific, actionable business recommendations

**Key Result:** Targeting the top 15% highest-risk customers can prevent ~430 annual churns, retaining $903K in customer value at a cost of $106K — generating an **8.6:1 ROI**.

---

## Business Context

### The Problem
A telecommunications company faces a **26.6% annual churn rate**, losing 1,869 customers from a base of 7,043. Without intervention, this represents:
- Lost lifetime value: **~$3.9M annually**
- Disrupted revenue streams
- Increased customer acquisition pressure

### The Decision Framework

**Cost-Benefit Analysis:**
- **Cost of missing a churner (False Negative):** $2,101 (lost customer lifetime value)
- **Cost of targeting loyal customer (False Positive):** $100 (wasted intervention)
- **Cost Ratio:** 21:1

**Strategic Implication:** This ratio justifies optimizing for **recall over precision** — it's better to over-target than miss high-risk customers.

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

## Key Findings

### Churn Drivers (Ranked by Impact)

| **Factor** | **High Risk Segment** | **Low Risk Segment** | **Risk Multiplier** |
|------------|----------------------|---------------------|---------------------|
| **Contract Type** | Month-to-month: 42.7% | Two-year: 2.8% | **15.3x** |
| **Customer Tenure** | 0-12 months: 47.7% | 36+ months: 11.9% | **4.0x** |
| **Payment Method** | Electronic check: 45.3% | Auto-pay: 15.3% | **3.0x** |
| **Online Security** | Without: 41.8% | With: 14.6% | **2.9x** |
| **Tech Support** | Without: 41.6% | With: 15.2% | **2.7x** |

### Feature Importance (Top 5)
1. **Tenure Months** — 17.0% importance
2. **Total Charges** — 13.1% importance  
3. **Contract Type (Two-year)** — 9.9% importance
4. **Monthly Charges** — 9.3% importance
5. **Dependents** — 8.0% importance

---

## Feature Importance
Feature importance analysis from the Random Forest model revealed that the most influential churn drivers are:
- Tenure Months
- Total Charges
- Contract Type (Two-year)
- Monthly Charges
- Dependents
- Internet Service (Fiber optic)
- Payment Method (Electronic check)

---

## Model Performance

### Approach
Two models were trained and compared:
- **Logistic Regression:** Interpretable baseline
- **Random Forest:** Captures non-linear relationships (selected as final model)

### Metrics (Random Forest)
- **ROC-AUC:** 0.844
- **Recall:** 0.770 (correctly identifies 77% of churners)
- **Precision:** 0.548 (55% of flagged customers actually churn)
- **F1-Score:** 0.640
- **Accuracy:** 0.770

**Why Recall Was Prioritized:**  
Given the 21:1 cost ratio, the business impact of missing a churner far exceeds the cost of a false positive. The model was intentionally tuned to maximize churn detection.

---

## ROI Analysis

### Targeting Strategy
**Approach:** Target top 15% highest-risk customers based on model probability scores

**Annual Projections:**
- **Customers targeted:** 1,056
- **Churners identified:** 717
- **Churns prevented (60% effectiveness):** 430
- **Customer value retained:** $903,376
- **Intervention cost:** $105,600
- **Net benefit:** $797,776
- **ROI:** 8.6:1

### Sensitivity Analysis

| **Intervention Effectiveness** | **Churns Prevented** | **Value Retained** | **Net Benefit** | **ROI** |
|-------------------------------|----------------------|-------------------|----------------|---------|
| 40% | 286 | $600,919 | $495,319 | 5.7:1 |
| 50% | 358 | $751,147 | $645,547 | 7.1:1 |
| **60%** | **430** | **$903,376** | **$797,776** | **8.6:1** |
| 70% | 501 | $1,053,605 | $948,005 | 10.0:1 |
| 80% | 573 | $1,205,834 | $1,100,234 | 11.4:1 |

**Key Insight:** Even under conservative assumptions (40% effectiveness), the model generates positive ROI, demonstrating robust business value.

---

## Business Recommendations

### **Priority 1: Contract Optimization**
- **Target:** Month-to-month customers in months 1-12
- **Action:** Automated email campaign offering 6-month contract upgrade with 15% discount
- **Expected Cost:** $45/customer
- **Impact:** Addresses the single largest churn driver (15x risk difference)

### **Priority 2: Value-Added Service Bundling**
- **Target:** Customers without online security or tech support
- **Action:** Auto-include online security in high-risk renewals (first 3 months free)
- **Impact:** 30-40% churn reduction in segment
- **Cost:** Low (incremental service cost ~$10/month after trial)

### **Priority 3: Payment Method Migration**
- **Target:** Electronic check users
- **Action:** Incentivize switch to credit card or bank auto-pay with $5/month discount for 6 months
- **Impact:** 45.3% → 15.3% churn reduction
- **Dual benefit:** Improves payment reliability

---

## Technical Implementation

### Technologies Used
- **Python 3.8+**
- **Data Processing:** pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Machine Learning:** scikit-learn
- **Models:** Logistic Regression, Random Forest

---
