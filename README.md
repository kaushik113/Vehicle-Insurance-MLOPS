# 🚗 Vehicle Insurance Purchase Prediction

A Machine Learning project to predict whether an existing customer is interested in purchasing vehicle insurance.

---

## 📌 Problem Statement

Insurance companies run targeted marketing campaigns to convert existing customers into vehicle insurance buyers.  
This project builds a supervised classification model to predict:

- **Response = 1** → Customer is interested  
- **Response = 0** → Customer is not interested  

The objective is to assist in campaign targeting and lead prioritization.

---

## 📊 Dataset Overview

- **Total Records:** 381,109 customers  
- **Features:** 11 input features + 1 target  
- **Target Imbalance:** ~12% positive class  

### Key Features
- Gender  
- Age  
- Driving_License  
- Region_Code  
- Previously_Insured  
- Vehicle_Age  
- Vehicle_Damage  
- Annual_Premium  
- Policy_Sales_Channel  
- Vintage  

---

## 🔍 Exploratory Data Analysis (EDA)

- Checked class imbalance (highly skewed toward non-interested customers)
- Analyzed Age vs Annual Premium distribution
- Compared Vehicle_Age and Vehicle_Damage against Response
- Visualized demographic and behavioral patterns
- Investigated premium outliers

---

## 🛠 Data Preprocessing

- Mapped categorical variables (e.g., Gender → 0/1)
- Applied one-hot encoding to categorical features
- Scaled numerical features:
  - `StandardScaler` → Age, Vintage
  - `MinMaxScaler` → Annual_Premium
- Dropped ID column
- Train-test split

---

## 🤖 Model Development

### Model Used
- **Random Forest Classifier**

### Hyperparameter Tuning
Used `RandomizedSearchCV` (4-fold cross-validation) with:

- `n_estimators = 300`
- `max_depth ∈ [2,3,4,5,6,7,10]`
- `min_samples_leaf ∈ [4,6,8]`
- `min_samples_split ∈ [5,7,10]`
- `criterion ∈ {gini, entropy}`

### Best Parameters
```python
{
    'n_estimators': 300,
    'min_samples_split': 7,
    'min_samples_leaf': 6,
    'max_depth': 10,
    'criterion': 'entropy'
}
