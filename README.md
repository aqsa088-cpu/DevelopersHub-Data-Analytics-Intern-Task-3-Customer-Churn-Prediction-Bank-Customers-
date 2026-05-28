# 🏦 Task 3: Customer Churn Prediction (Bank Customers)

**DevelopersHub Corporation — Data Science & Analytics Internship**

---

## 📌 Task Objective

The objective of this task is to identify bank customers who are likely to leave (churn) using supervised machine learning. By analyzing customer demographics, account information, and banking behavior, a classification model is trained to predict churn and help the bank take proactive retention measures.

---

## 📂 Dataset Description

The **Churn Modelling Dataset** contains information about bank customers and whether they exited the bank.

| Property        | Details                                      |
|-----------------|----------------------------------------------|
| Total Samples   | 10,000 rows                                  |
| Features        | 14 columns (numeric + categorical)           |
| Target Variable | `Exited` (1 = Churned, 0 = Stayed)           |
| Class Balance   | ~20% churned, ~80% retained                  |
| Source          | Kaggle — Churn Modelling Dataset             |

### Key Features:
- `CreditScore` — Customer's credit score
- `Geography` — Country (France, Germany, Spain)
- `Gender` — Male / Female
- `Age` — Customer age
- `Tenure` — Years with the bank
- `Balance` — Account balance
- `NumOfProducts` — Number of bank products used
- `HasCrCard` — Whether customer has a credit card
- `IsActiveMember` — Whether customer is active
- `EstimatedSalary` — Estimated annual salary
- `Exited` — Target: 1 (churned), 0 (stayed)

---

## 🚀 My Approach

### 1. Data Cleaning & Preparation
- Dropped irrelevant columns: `RowNumber`, `CustomerId`, `Surname`
- Checked for and confirmed no missing values
- Verified data types and class distribution

### 2. Encoding Categorical Features
- Applied **Label Encoding** to `Gender` (Male=1, Female=0)
- Applied **One-Hot Encoding** to `Geography` to avoid ordinal bias
- Resulted in clean numeric feature matrix ready for modeling

### 3. Exploratory Data Analysis (EDA)
Visualizations created using `matplotlib` and `seaborn`:

| Visualization | Insight |
|---------------|---------|
| Churn count plot | Confirmed class imbalance (~20% churn rate) |
| Age vs Churn box plot | Older customers more likely to churn |
| Geography churn bar chart | Germany had the highest churn rate |
| Balance distribution | Churned customers tended to have higher balances |
| Correlation heatmap | Age and balance showed strongest correlation with churn |

### 4. Model Training
- Split dataset: 80% training / 20% testing
- Trained a **Random Forest Classifier** (also tested Logistic Regression)
- Used `scikit-learn` for model building and evaluation

### 5. Feature Importance Analysis
- Extracted and visualized feature importance scores from the Random Forest model
- Top features influencing churn: `Age`, `Balance`, `NumOfProducts`, `IsActiveMember`

---

## 📊 Results and Insights

| Metric        | Score       |
|---------------|-------------|
| Accuracy      | ~86%        |
| Precision     | ~75%        |
| Recall        | ~47%        |
| F1 Score      | ~58%        |

### Key Findings:
- **Age** is the strongest predictor — customers aged 40–60 are significantly more likely to churn
- **German customers** churn at nearly double the rate of French and Spanish customers
- **Inactive members** (`IsActiveMember = 0`) show much higher churn probability
- Customers with **only 1 product** or **3+ products** are more likely to churn than those with 2 products
- **Higher account balances** are associated with higher churn — possibly customers moving to competitors offering better returns

---

## 🛠️ Tools & Libraries Used

- **Python 3.x**
- **Pandas** — Data loading, cleaning, and manipulation
- **NumPy** — Numerical operations
- **Matplotlib** — Plotting and visualization
- **Seaborn** — Statistical visualizations
- **Scikit-learn** — Encoding, model training, and evaluation
- **Jupyter Notebook** — Development environment

---

## 📁 Repository Structure

```
DevelopersHub-Data-Analytics-Intern-Task-3-Customer-Churn-Prediction-Bank-Customers/
│
├── customer_churn_prediction.ipynb   # Main Jupyter Notebook with full analysis
├── Churn_Modelling.csv               # Dataset file
└── README.md                         # Project documentation
```

---

## ▶️ How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/aqsa088-cpu/DevelopersHub-Data-Analytics-Intern-Task-3-Customer-Churn-Prediction-Bank-Customers-.git
   ```

2. Navigate to the project folder:
   ```bash
   cd DevelopersHub-Data-Analytics-Intern-Task-3-Customer-Churn-Prediction-Bank-Customers-
   ```

3. Install required libraries:
   ```bash
   pip install pandas numpy matplotlib seaborn scikit-learn jupyter
   ```

4. Launch Jupyter Notebook:
   ```bash
   jupyter notebook
   ```

5. Open `customer_churn_prediction.ipynb` and run all cells.

---

## ✅ Conclusion

This task demonstrated how machine learning can help banks identify at-risk customers before they leave. The Random Forest model achieved ~86% accuracy, with `Age`, `Balance`, and `IsActiveMember` being the most influential factors in predicting churn. These insights can help banks design targeted retention campaigns — for example, offering loyalty rewards to older, high-balance, or inactive customers in Germany.

---

## 👩‍💻 Author

**Aqsa Irfan**  
Data Science & Analytics Intern — DevelopersHub Corporation
