#  Predictive Customer Analytics for Banking Campaigns

> **Predicting Bank Customer Behavior: A Data-Driven Approach to Campaign Effectiveness and Customer Segmentation**

[![R](https://img.shields.io/badge/Language-R-276DC3?style=flat&logo=r&logoColor=white)](https://www.r-project.org/)
[![Quarto](https://img.shields.io/badge/Report-Quarto-4A90D9?style=flat)](https://quarto.org/)
[![ML Models](https://img.shields.io/badge/Models-Regression%20%7C%20Classification-brightgreen?style=flat)]()


---

##  Introduction

Direct marketing campaigns are one of the primary tools banks use to acquire new customers and promote financial products. However, without data-driven targeting, these campaigns are costly and inefficient. Reaching thousands of customers who are unlikely to respond while missing those who would. The ability to predict customer behavior before launching a campaign is therefore a significant competitive advantage.
This project applies predictive analytics to a real-world banking dataset collected from direct marketing phone campaigns conducted by a Portuguese bank. Using a combination of regression and classification models, this project investigates two core dimensions of customer behavior: what drives a customer's account balance, and what predicts their likelihood of subscribing to a term deposit product.
The analysis is structured across two analytical tracks. The first track is the quantitative analysis; using Multiple Linear Regression, Lasso Tuned Regression, and Generalized Additive Models (GAM) to identify and predict the factors influencing individual account balances. The second track is the qualitative analysis using Logistic Regression, Tuned Random Forest, and Tuned Gradient Boosted Models to classify customers likely to subscribe to a term deposit. Together, these two tracks provide a comprehensive, data-driven view of customer behavior that can directly inform campaign strategy, customer segmentation, and resource allocation.


##  Problem Statement

Banks operating direct marketing campaigns frequently struggle to answer critical performance questions in real time. Which customers are financially valuable? Who is likely to respond to a product offer? Without predictive modeling, marketing teams rely on broad demographic assumptions, historical averages, and manual segmentation; approaches that are slow, inconsistent, and increasingly inadequate in a data-rich environment.
The core problem this project addresses is twofold. First, the bank lacks a reliable model to predict individual account balances from customer demographic and campaign data thus limiting its ability to identify and prioritize high-value customers. Second, without a classification model, the bank cannot efficiently predict which customers are likely to subscribe to a term deposit, resulting in wasted campaign resources and missed revenue opportunities. This project addresses both gaps through rigorous statistical modeling and machine learning.


##  Project Objectives & Business Questions



---

##  Data Description





---

## Exploratory Data Analysis & Visualization

a. Descriptive statistics and dataset summaries
b. Correlation analysis and heatmaps
c. Pairwise plots for multicollinearity assessment
d. Histograms and bar plots for variable distributions


---

##  Quantitative Analysis — Predicting Account Balance

### Regression Models (Predicting Account Balance)
| Model | Purpose |
|---|---|
| Multiple Linear Regression | Baseline balance prediction |
| Lasso Regression (Tuned) | Regularized model with feature selection |
| Generalized Linear Model (GLM) | Non-normal distribution handling |

**Evaluation Metrics:** RMSE, R², Residual Diagnostics, VIF, Actual vs. Predicted plots, Variable Importance

##  Qualitative Analysis — Predicting Term Deposit Subscription

### Classification Models (Predicting Term Deposit Subscription)
| Model | Purpose |
|---|---|
| Logistic Regression | Baseline classification |
| Random Forest (Tuned) | Ensemble method with feature importance |
| Gradient Boosted Trees (Tuned) | High-performance boosting model |

**Evaluation Metrics:** Accuracy, ROC-AUC, Sensitivity, Specificity, Precision, F1-Score, Optimal Threshold (Best Cutoff)

a. **Regression:** Identified contact duration, campaign frequency, and prior interactions as top predictors of account balance
b. **Classification:** Random Forest and Gradient Boosted Trees outperformed Logistic Regression in predicting term deposit subscriptions
c. **ROC-AUC analysis** with optimal threshold tuning improved model sensitivity for identifying high-probability subscribers
d. **Variable Importance Plots** revealed job type, housing loan status, and contact duration as the most influential classification features

---

##  Discussion


---

##  Conclusion

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


