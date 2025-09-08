# Home Credit Default Risk Analysis & Prediction

A machine learning project to predict loan default risk using alternative data sources, developed during Rakamin Academy Virtual Internship in collaboration with Home Credit.

## Problem Statement

Many loan applicants lack formal credit histories, making traditional credit scoring methods ineffective in assessing their repayment capacity. This creates the risk of unfairly rejecting creditworthy individuals while also increasing the likelihood of granting loans to those who may default.

## Objectives

**Primary Goal:** Develop a credit risk prediction model using alternative data that achieves an AUC above 0.75 within six months, reducing false rejections of creditworthy clients and supporting responsible lending.

**Success Metrics:**
- **AUC Score:** ≥ 0.75
- **Approval Rate:** ≥ 70% (minimum threshold to maintain healthy loan disbursement)
- **Default Rate:** ≤ 7% (target to reduce defaults)

## Dataset Overview

The dataset consists of 7 interconnected files providing comprehensive customer credit profiles:

### Core Files
- **application_train.csv**: Main loan application data (307,511 rows × 122 columns)
- **application_test.csv**: Test dataset (48,744 rows × 121 columns)
- **HomeCredit_columns_description.csv**: Column descriptions

### Historical Data
- **bureau.csv**: Credit history from other financial institutions
- **bureau_balance.csv**: Monthly balances of previous credits
- **previous_application.csv**: Historical loan applications to Home Credit

### Transaction Data
- **POS_CASH_balance.csv**: Monthly balances of POS and cash loans
- **credit_card_balance.csv**: Monthly credit card balances
- **installments_payments.csv**: Installment payment history

## Key Findings

### Job Categories & Default Risk
- **Low Risk Jobs**: Accountants, Core Staff, Managers, High Skill Tech
- **High Risk Jobs**: Low-skill Laborers, Waiters/Barmen, Drivers, Security/Laborers
- **Statistical Significance**: χ² = 1403.22, p < 0.001

### External Data Impact
- External financial data is **3x more predictive** than demographics
- **5x risk gap** between low and high external scores
- Missing external data signals elevated risk

## Data Preprocessing

### Data Cleaning
- Removal of redundant columns
- Handling high-missing value columns
- Median imputation and 'Unknown' category assignment

### Feature Engineering
- **Feature Construction**: Created domain-specific features
- **Outlier Handling**: Log transformation and IQR capping
- **Feature Scaling**: RobustScaler for numerical features
- **Feature Selection**: SelectFromModel for optimal feature subset

### Key Engineered Features
- `CREDIT_ANNUITY_RATIO`
- `PREV_AMT_APP_MEAN` / `PREV_AMT_CREDIT_MEAN`
- `INST_PAYMENT_RATIO_MEAN`
- `DEBT_CREDIT_RATIO`

## Model Development

### Algorithm Selection
**CatBoost Classifier** was chosen for its:
- Automatic categorical feature handling
- Superior performance with mixed data types
- Built-in overfitting protection

### Model Configuration
- **Class Imbalance**: Handled using `scale_pos_weight` based on class ratio
- **Hyperparameter Tuning**: RandomizedSearchCV with 3-fold stratified cross-validation
- **Threshold Optimization**: Optimal threshold of 0.69 for maximum F1-score (0.3313)

### Top Feature Importance
1. `EXT_SOURCE_3` (Highest importance)
2. `EXT_SOURCE_1`
3. `CREDIT_ANNUITY_RATIO`
4. `EXT_SOURCE_2`

## Results

### Model Performance
- **AUC Score**: 0.7807 (Target: ≥ 0.75)

### Business Impact
- **Default Rate**: 5.42% (Target: ≤ 7%, Previous: 8.07%)
- **Approval Rate**: 88.19% (Target: ≥ 70%)

### Confusion Matrix
```
                 Predicted
Actual    Negative  Positive
Negative   51,299    5,239
Positive    2,939    2,026
```

## Business Recommendations

### 1. Data Quality Enhancement
- Prioritize `EXT_SOURCE` completeness
- Monitor top 10 feature stability
- Implement robust data validation pipelines

### 2. Risk-Based Product Development
- **B2B Payroll-Integrated Financing**: Auto-deducted repayments for stable income sectors
- **Profession-Specific Micro-Insurance**: Risk-adjusted premiums based on occupation

### 3. Partnership Expansion
- **Strategic Partnership Program**: Collaborate with banks, fintechs, and credit bureaus
- Expand alternative data sources for thin-file applicants

## Contact

**Az-Zukhrufu Fi Silmi Suwondo**
- Email: afsilmis@gmail.com
- LinkedIn: [linkedin.com/in/afsilmis](https://linkedin.com/in/az-zukhrufu-fi-silmi-suwondo/)
- Project Link: [https://github.com/afsilmis/home-credit-score-predictor](https://github.com/afsilmis/home-credit-score-predictor)

---

*This project was completed as part of Rakamin Academy Virtual Internship program in collaboration with Home Credit Indonesia.*
