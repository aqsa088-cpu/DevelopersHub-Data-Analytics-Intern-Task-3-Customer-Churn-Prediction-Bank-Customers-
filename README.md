# Customer Churn Prediction

## Task Objective

The goal of this project is to predict whether a bank customer will churn (leave the bank) based on demographic and account-level features. This is a **binary classification** problem where the target variable `Exited` indicates churn (1) or retention (0). Accurately identifying at-risk customers enables the bank to take proactive retention measures before losing them.

---

## Approach

### 1. Data Loading & Exploration
- Loaded the dataset (`Churn_Modelling.csv`) containing 10,000 customer records with 14 features.
- Explored the class distribution, revealing a significant **class imbalance**: the majority of customers did not churn.

### 2. Data Cleaning & Preprocessing
- Dropped irrelevant identifier columns: `RowNumber`, `CustomerId`, and `Surname`.
- Applied **one-hot encoding** to categorical features (`Geography`, `Gender`), converting them to numeric indicators.
- Applied **StandardScaler** to normalize numerical features (e.g., `Age`, `Balance`, `EstimatedSalary`).
- Split the data into **80% training / 20% testing** sets using stratified sampling to preserve class proportions.

### 3. Handling Class Imbalance with SMOTE
- Used **SMOTE (Synthetic Minority Oversampling Technique)** on the training set to synthetically balance the churn vs. non-churn classes, preventing models from being biased toward the majority class.

### 4. Model Training & Evaluation
Three classifiers were trained and compared on the SMOTE-balanced training data:

| Model | Key Characteristic |
|---|---|
| Logistic Regression | Linear baseline model (`liblinear` solver) |
| Random Forest | Ensemble of decision trees (bagging) |
| Gradient Boosting | Sequential boosting ensemble |

All models were evaluated on the **original (unbalanced) test set** using accuracy and a full classification report (precision, recall, F1-score).

### 5. Feature Importance Analysis
- Extracted feature importances from the best-performing model (Gradient Boosting).
- Visualized the ranked importance of all features using a horizontal bar chart.

---

## Results & Insights

### Model Performance

The **Gradient Boosting Classifier** was the best-performing model, achieving the strongest balance between overall accuracy and recall for the minority churn class. Random Forest followed closely, while Logistic Regression served as a solid but weaker baseline.

### Key Insights

- **Age** was the single most important predictor of churn — older customers were significantly more likely to leave.
- **Number of Products** (`NumOfProducts`) was the second most influential feature. Customers holding only one product had a higher churn risk, while those with two products were more loyal.
- **Balance** and **EstimatedSalary** also contributed meaningfully, suggesting that high-balance inactive customers are a churn risk.
- **Geography** mattered — German customers showed a noticeably higher churn rate compared to French and Spanish customers.
- **IsActiveMember** was a strong negative predictor: active members churned far less frequently.
- Features like `HasCrCard` and `Tenure` had relatively low predictive power.

### Business Takeaway

Retention efforts should be prioritized for **older customers**, those with **only one product**, **German geography**, and **inactive account holders** — these segments represent the highest churn risk according to the model.
