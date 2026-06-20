# 🏦 Predictive Customer Analytics for Banking Campaigns

> **Predicting Bank Customer Behavior: A Data-Driven Approach to Campaign Effectiveness and Customer Segmentation**

[![R](https://img.shields.io/badge/Language-R-276DC3?style=flat&logo=r&logoColor=white)](https://www.r-project.org/)
[![Quarto](https://img.shields.io/badge/Report-Quarto-4A90D9?style=flat)](https://quarto.org/)
[![ML Models](https://img.shields.io/badge/Models-Regression%20%7C%20Classification-brightgreen?style=flat)]()


---

##  Project Overview

Banks invest heavily in direct marketing campaigns to acquire term deposit subscribers, yet most outreach efforts are inefficient, contacting customers who are unlikely to convert. This project addresses that gap by building **dual predictive models** that:

1. **Predict customer account balances** using demographic and campaign variables (Regression)
2. **Classify customers likely to subscribe** to a term deposit (Classification)

The insights enable data-driven **customer segmentation**, **targeted campaign design**, and **smarter resource allocation** ; reducing wasted outreach and improving conversion rates.

---

##  Business Questions

### Quantitative Analysis (Regression)
a. Which numerical demographic and campaign factors significantly predict a customer's average account balance?
b. How do age, contact duration, campaign frequency, days since last contact, and prior interactions influence bank balances?
c. Can we accurately predict a customer's bank balance using quantitative variables from demographic profiles and past campaign data?

### Qualitative Analysis (Classification)
a. What categorical factors most influence a customer's decision to subscribe to a term deposit?
b. How do loan status, housing status, marital status, and job type impact subscription likelihood?
c. Can we accurately classify customers as likely subscribers based on categorical demographic and campaign attributes?

---

##  Dataset

The dataset contains **demographic, financial, and campaign-related attributes** for bank customers contacted during direct marketing campaigns.

| Variable | Description |
|---|---|
| `Age` | Customer's age |
| `Balance` | Average annual account balance (target for regression) |
| `Duration` | Duration of last contact (seconds) |
| `Campaign` | Number of contacts during current campaign |
| `Previous` | Number of contacts before current campaign |
| `Day` | Day of month of last contact |
| `Job` | Type of employment |
| `Marital` | Marital status |
| `Education` | Education level |
| `Default` | Has credit in default? (binary) |
| `Housing` | Has housing loan? (binary) |
| `Loan` | Has personal loan? (binary) |
| `Contact` | Communication type |
| `y` | Subscribed to term deposit? (classification target) |

**Three analytical datasets were prepared:**
a. `Fin_data` : full financial dataset
b. `regression_df` : cleaned dataset for balance prediction models
c. `classification_df` : cleaned dataset for subscription classification models

---

##  Methodology

### Exploratory Data Analysis
a. Descriptive statistics and dataset summaries
b. Correlation analysis and heatmaps
c. Pairwise plots for multicollinearity assessment
d. Histograms and bar plots for variable distributions

### Regression Models (Predicting Account Balance)
| Model | Purpose |
|---|---|
| Multiple Linear Regression | Baseline balance prediction |
| Lasso Regression (Tuned) | Regularized model with feature selection |
| Generalized Linear Model (GLM) | Non-normal distribution handling |

**Evaluation Metrics:** RMSE, R², Residual Diagnostics, VIF, Actual vs. Predicted plots, Variable Importance

### Classification Models (Predicting Term Deposit Subscription)
| Model | Purpose |
|---|---|
| Logistic Regression | Baseline classification |
| Random Forest (Tuned) | Ensemble method with feature importance |
| Gradient Boosted Trees (Tuned) | High-performance boosting model |

**Evaluation Metrics:** Accuracy, ROC-AUC, Sensitivity, Specificity, Precision, F1-Score, Optimal Threshold (Best Cutoff)

---

##  Key Results

a. **Regression:** Identified contact duration, campaign frequency, and prior interactions as top predictors of account balance
b. **Classification:** Random Forest and Gradient Boosted Trees outperformed Logistic Regression in predicting term deposit subscriptions
c. **ROC-AUC analysis** with optimal threshold tuning improved model sensitivity for identifying high-probability subscribers
d. **Variable Importance Plots** revealed job type, housing loan status, and contact duration as the most influential classification features

---

##  Business Impact

| Insight | Actionable Recommendation |
|---|---|
| Contact duration is a strong predictor | Prioritize longer, quality engagements over volume |
| Job type and loan status drive subscription | Segment campaigns by employment and financial profile |
| High campaign frequency reduces conversion | Reduce contact frequency; focus on high-probability leads |
| Prior interactions signal interest | Re-target customers with previous positive engagements |

---

## 🛠️ Tools & Technologies

| Tool | Use |
|---|---|
| **R** | Core analysis and modeling |
| **tidyverse** | Data wrangling and visualization |
| **tidymodels** | Model training, tuning, and evaluation |
| **randomForest / xgboost** | Ensemble and boosted models |
| **glmnet** | Lasso regularization |
| **ggplot2** | Data visualization |
| **Quarto** | Reproducible reporting |

---


