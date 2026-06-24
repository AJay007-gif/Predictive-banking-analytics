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

This project pursues two primary analytical objectives:
####  Objective 1
Quantitative Analysis: Predicting Account Balance
To identify the demographic and campaign factors that significantly predict a customer's average account balance, and to determine which regression model best captures those relationships.

Which numerical variables: age, contact duration, campaign frequency, days since last contact, and prior interactions significantly predict account balance?
Do non-linear relationships exist between predictors and balance, and does accounting for them improve model performance?
Which model: Multiple Linear Regression, Lasso Tuned Regression, or GAM produces the most accurate balance predictions?

####  Objective 2 
Qualitative Analysis: Predicting Term Deposit Subscription
To identify the categorical and demographic factors that influence a customer's decision to subscribe to a term deposit, and to determine which classification model best predicts subscription likelihood.

Which factors; job type, marital status, housing loan status, personal loan status, and contact type most influence subscription decisions?
How does subscription likelihood vary across customer segments defined by employment, financial obligations, and communication history?
Which model: Logistic Regression, Tuned Random Forest, or Tuned Gradient Boosted Model most accurately classifies customers as likely subscribers?


##  Data Description

The dataset used in this project is the Bank Marketing Dataset sourced from the UCI Machine Learning Repository. It was collected from direct marketing phone campaigns conducted by a Portuguese banking institution between 2008 and 2013. The dataset contains 45,211 records and 17 variables capturing customer demographics, financial attributes, and campaign-related information. The outcome variables are account balance (continuous, used for regression) and subscription status (binary: yes/no, used for classification).

**Dataset Summary**

| Attribute | Description |
|------------|------------|
| Source | UCI Machine Learning Repository |
| Domain | Banking & Marketing |
| Records | 45,211 |
| Variables | 17 |
| Period | 2008–2013 |
| Regression Target | Balance (Account Balance) |
| Classification Target | y (Term Deposit Subscription) |


**Variable Description**

| Variable | Type | Description |
|----------|------|-------------|
| age | Numerical | Customer's age in years |
| balance | Numerical | Average annual account balance in euros (Regression Target) |
| duration | Numerical | Duration of the last contact in seconds |
| campaign | Numerical | Number of contacts made during the current campaign |
| previous | Numerical | Number of contacts made before the current campaign |
| day | Numerical | Day of the month of the last contact |
| job | Categorical | Type of employment |
| marital | Categorical | Marital status |
| education | Categorical | Education level |
| default | Categorical | Has credit in default? (Yes/No) |
| housing | Categorical | Has housing loan? (Yes/No) |
| loan | Categorical | Has personal loan? (Yes/No) |
| contact | Categorical | Communication type used |
| month | Categorical | Month of the last contact |
| poutcome | Categorical | Outcome of the previous marketing campaign |
| y | Categorical | Subscribed to term deposit? (Yes/No) – Classification Target |


**Target Variables**

| Analysis Type | Target Variable | Description |
|--------------|----------------|-------------|
| Multiple Linear Regression | balance | Predict customer account balance |
| Classification Models | y | Predict whether a customer subscribes to a term deposit |


###  Data Preparation & Cleaning

**Cleaning steps**

a. Checked for and confirmed no missing values across all variables
b. Removed duplicate records to ensure model integrity
c. Encoded categorical variables as factors for model compatibility
d. Identified and assessed outliers in the balance variable — extreme values were retained as they reflect real customer financial variation
e. Applied an 80/20 train/test split for model training and evaluation across both analytical tracks


## Exploratory Data Analysis & Visualization

####  Descriptive Statistics
Initial exploration of the dataset revealed several important patterns. The average account balance showed considerable variation across customers, with a small proportion holding significantly higher balances than the majority indicating a right-skewed distribution. Contact duration varied widely, suggesting that some campaign interactions were substantially more engaged than others. The majority of customers in the dataset did not subscribe to the term deposit, confirming a class imbalance in the outcome variable that was accounted for in the classification modeling strategy.


####  Key Visualizations & Insights

**Distribution of Account Balance**
The balance variable showed a strongly right-skewed distribution, with most customers holding modest balances and a small number holding very large balances. This pattern motivated the use of GAM alongside linear models, as non-linear modeling better captures such distributional characteristics.

**Subscription Rate by Job Type**
Subscription rates varied noticeably across job categories. Retired customers and students showed higher subscription rates relative to their proportion in the dataset, while blue-collar workers showed the lowest rates suggesting that occupation is a meaningful segmentation variable for campaign targeting.

**Correlation Heatmap**
The correlation analysis among numerical variables revealed moderate positive correlations between previous campaign contacts and subscription likelihood, and between contact duration and balance. No severe multicollinearity was detected among predictors, supporting the validity of the regression models.

**Balance by Subscription Status**
Customers who subscribed to the term deposit tended to have higher average account balances than non-subscribers, suggesting that financial stability may be a contributing factor in the subscription decision.

**Class Imbalance**
Approximately 88% of customers in the dataset did not subscribe, compared to 12% who did. This significant imbalance informed the choice of evaluation metrics prioritizing AUC, sensitivity, and optimal threshold analysis over simple accuracy and motivated the use of ensemble models better suited to imbalanced classification problems.



##  Quantitative Analysis — Predicting Account Balance

### Regression Models (Predicting Account Balance)
| Model | Purpose |
|---|---|
| Multiple Linear Regression | Baseline balance prediction |
| Lasso Regression (Tuned) | Regularized model with feature selection |
| Generalized Linear Model (GLM) | Non-normal distribution handling |

**Evaluation Metrics:** RMSE, R², Residual Diagnostics, VIF, Actual vs. Predicted plots, Variable Importance

####  Model 1 — Multiple Linear Regression
Multiple Linear Regression was used as the baseline model for predicting account balance. This model estimates the linear relationship between a set of demographic and campaign predictors and the continuous outcome variable average account balance. As the foundational regression approach, it provides an interpretable benchmark against which more complex models are evaluated.
The model was trained on the regression dataset using all available numerical predictors. Residual diagnostic plots were examined to assess assumptions of normality, homoscedasticity, and independence. Variable Inflation Factor (VIF) scores confirmed no severe multicollinearity among predictors.
**Key findings:** Contact duration and the number of previous campaign contacts emerged as statistically significant positive predictors of account balance. Campaign frequency showed a negative relationship, suggesting that customers contacted more frequently during the current campaign tended to have lower balances possibly indicating lower-value targeting.

####  Model 2 — Lasso Tuned Regression
Lasso Regression was applied to address the risk of overfitting present in the baseline model and to perform automatic feature selection. By adding a regularization penalty (lambda) that shrinks less important variable coefficients toward zero, Lasso identifies only the most influential predictors of account balance producing a leaner, more generalizable model.
The optimal lambda value was selected through cross-validation. Variables with low predictive contribution were removed from the model, reducing dimensionality and improving out-of-sample performance.
**Key findings:** Lasso confirmed the significance of duration and previous contacts while removing weaker predictors, producing a more parsimonious model with comparable or improved predictive accuracy relative to the MLR baseline.

###  Model 3 — Generalized Additive Model (GAM)
GAM was employed to capture non-linear relationships between predictors and account balance that the linear models could not accommodate. Rather than fitting straight lines, GAM fits smooth curves to each predictor, allowing the model to flexibly represent the true shape of each relationship.
This approach was particularly motivated by the right-skewed distribution of balance and the expectation that variables like age and campaign frequency would exhibit non-linear effects. for example, balance may increase with age up to a point before plateauing or declining.
**Key findings:** GAM smooth term plots revealed meaningful non-linear patterns in several predictors. Age showed a curved relationship with balance, and contact duration exhibited a non-linear positive effect. GAM produced improved fit statistics compared to the linear baseline, validating the non-linear modeling approach.


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


