# Credit Risk Score Prediction for NBFCs

### Project Overview
The goal of this project is to help **financial analysts in an NBFC** (Non-Banking Financial Company) **predict the credit risk score** of customers **before disbursing loans**.  
By evaluating a customer’s risk profile, the model aims to minimize default rates while ensuring faster and fairer credit decisions.

---

### Dataset Summary
- **Period Covered:** February 2022 – May 2024  
- **Total Records:** ~50,000 customers  
- **Data Sources:**  
  - `customers.csv` — Customer demographic information  
  - `loans.csv` — Loan details and repayment data  
  - `bureau.csv` — Bureau and credit history data  

All three datasets were merged on unique customer identifiers to create a unified dataset for modeling.

---

### Workflow Summary

#### 1. Data Cleaning & Preparation
- Handled missing values, inconsistent formats, and outliers  
- Split data into **Train (75%)** and **Test (25%)** before any analysis to **avoid data leakage**

#### 2. Exploratory Data Analysis (EDA)
- Explored customer and loan distributions  
- Analyzed relationships between key numeric and categorical features  
- Identified patterns of defaults and repayment behavior  

#### 3. Feature Engineering
- Created derived variables:
  - **Loan-to-Income Ratio**
  - **Delinquency Ratio**
  - **Credit Utilization Ratio**
- Encoded categorical features using **One-Hot Encoding**
- Scaled numeric features to standardize inputs

#### 4. Feature Selection
- Checked **multicollinearity using VIF**; removed highly correlated features  
- Calculated **Weight of Evidence (WoE)** and **Information Value (IV)**  
- Selected features with **IV > 0.02** for modeling  

#### 5. Model Building
Models evaluated:
- Logistic Regression  
- Random Forest  
- XGBoost  

Techniques used:
- **RandomizedSearchCV** for initial hyperparameter tuning  
- **Optuna** for automated optimization  

#### 6. Model Evaluation
Business requirement → **Recall ≥ 90%** (to capture maximum defaulters)

| Metric | Score | Interpretation |
|--------|-------:|----------------|
| **AUC** | 0.98 | Excellent separation between default & non-default |
| **Gini Coefficient** | 0.96 | Strong predictive power |
| **KS Statistic** | 86.09% (in Decile 8) | Meets business decile requirement |
| **Recall** | > 0.90 | Captures majority of default cases |
| **Accuracy** | ~0.93 | Overall robust classification |

Selected final model: **Logistic Regression**  
- Chosen for **high explainability** and business interpretability  
- XGBoost achieved similar results but was less interpretable  

---

### Model Explainability
- Used Logistic Regression coefficients to understand feature impact  
- Features such as **Credit Utilization Ratio**, **Delinquency Ratio**, and **Loan-to-Income Ratio** were found to be the strongest drivers of default risk  
- Ensured model transparency for financial analysts and regulators  
- [Video Walkthrough](https://youtu.be/VKNXrhRMcJ4)
---

### AI Governance & Fairness
To ensure model reliability, a full **AI Governance process** was conducted:
- Verified **model stability** and **performance consistency**  
- Checked **fairness and bias** — no sensitive attributes used  
- Ensured **responsible AI practices** aligned with **RBI guidelines**  
- Implemented **monthly monitoring plan** for drift detection and retraining triggers  

The model is **interpretable**, **fair**, and **business-aligned**

---

### Tech Stack
| Category | Tools / Libraries |
|-----------|------------------|
| **Programming Language** | Python 3.12 |
| **Data Handling** | Pandas, NumPy |
| **EDA & Visualization** | Matplotlib, Seaborn |
| **Feature Engineering** | Scikit-learn, Featuretools |
| **Modeling** | Logistic Regression, Random Forest, XGBoost |
| **Hyperparameter Tuning** | RandomizedSearchCV, Optuna |
| **Evaluation Metrics** | AUC, Gini, KS, Recall, Accuracy |
| **Deployment** | Streamlit |
| **AI Governance** | Custom Governance Framework (Performance + Fairness checks) |

---

### Key Business Insights
- Customers with **high loan-to-income** and **credit utilization ratios** show significantly higher default probability  
- **Residence type** and **loan purpose** also play moderate roles in default behavior  
- The model assists analysts in **ranking customer risk** rather than auto-rejecting applications, ensuring human oversight  

---

### Outcome
A robust, interpretable model achieving:
- **AUC:** 0.98  
- **Gini:** 0.96  
- **Recall:** > 90%  
- **KS Statistic:** 86.09% (within top deciles)  
- **Business ready**, aligned with NBFC credit governance standards

---

### Author
**Shijin Ramesh**  
Data Scientist | ML Engineer
Passionate about bridging business strategy and data-driven decision making.  
[LinkedIn](https://www.linkedin.com/in/shijinramesh/) | [Portfolio](https://www.shijinramesh.co.in/)


