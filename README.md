# 📊 Customer Churn Prediction & Business Insights

![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python)
![ML](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange)
![Random Forest](https://img.shields.io/badge/Model-RandomForest-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

This project analyzes customer churn for an energy and gas service provider by combining customer information with historical pricing data.

The project started with a clear business hypothesis:

> **Price sensitivity may be one of the major reasons customers are leaving the company.**

From a business perspective, this is a realistic assumption. When customers leave after changes in pricing, managers may naturally suspect that price is the main reason behind churn.

However, as a data scientist, my role was not to accept that assumption directly. My goal was to test whether the available data actually supported it.

To do this, I explored customer behavior, pricing patterns, contract-related features, consumption trends, and churn distribution. I then engineered additional features and built machine learning models to understand how well churn could be predicted.

The final model performance was limited, with an F1-score of around 0.30 and recall around 0.30. Instead of treating this only as a weak model result, I interpreted it as an important business signal.

The analysis suggests that pricing may influence churn, but price sensitivity alone does not fully explain why customers leave. Churn is more likely affected by a broader combination of factors such as customer tenure, sales channel, product engagement, contract history, consumption behavior, and customer experience factors that were not available in the dataset.

This project helped me understand that machine learning is not only about building a predictive model. It is also about testing business assumptions, identifying data limitations, and translating technical results into business decisions.

---

## 💼 **1. Business Problem**

For subscription-based businesses such as energy and gas providers, retaining existing customers is often more cost-effective than acquiring new ones. Even a small increase in customer churn can have a significant impact on long-term revenue and profitability.

When customers decide to leave, businesses naturally try to understand the underlying reason so that appropriate retention strategies can be developed.

One common assumption is that customers leave because they become sensitive to pricing changes. If this assumption is correct, the business could potentially reduce churn through pricing adjustments, discounts, or targeted promotional offers.

However, acting on an incorrect assumption can be costly. Reducing prices across the customer base without understanding the true drivers of churn may lower revenue without significantly improving retention.

This creates an important business question:

> **Is price sensitivity actually a major driver of customer churn, or are customers leaving because of a broader combination of behavioural and operational factors?**

This project approaches that question from a data science perspective by combining customer information with historical pricing records to evaluate whether the available data supports the business hypothesis.

---
## 🎯 **2. Project Objectives**

I wanted to answer four questions:

Can churn be predicted from the available data?
Is price sensitivity actually a major churn driver?
Which customer characteristics are associated with churn?
What additional data would improve churn prediction?

---

##⚡**3. Key Findings**

- Low-tenure customers churn more.
- Consumption is a weak predictor.
- Pricing contributes but is not dominant.
- Models achieve limited recall.
- The results suggest missing behavioural factors.

> Business Insight: **Price sensitivity alone does not fully explain customer churn.**

---

## 📂 **5. Dataset Description**

The Multiple datasets includes:
- ~14,600 customers  
- ~193,000 pricing records  

Key Characteristics:
- Highly imbalanced dataset (~90% non-churn)  
- Mix of numerical and categorical features  
- Presence of skewness and outliers  

---

## 🔬 Methodology

To investigate whether price sensitivity could explain customer churn, I followed a structured data science workflow.

### 1. Data Understanding

- Examined customer and pricing datasets.
- Understood feature definitions.
- Identified missing values and data quality issues.

### 2. Exploratory Data Analysis

- Analyzed churn distribution.
- Studied customer tenure.
- Investigated energy consumption patterns.
- Explored pricing behaviour.

### 3. Feature Engineering

- Log transformations.
- Consumption change metrics.
- Cost pressure features.
- Tenure groups.
- Product engagement features.

### 4. Model Development

- Random Forest
- XGBoost

### 5. Model Evaluation

- Precision
- Recall
- F1-score
- Confusion Matrix

> ⚠️ Special emphasis was placed on recall because of the severe class imbalance.

## 📊 **7. Results & Model Performance**

| Model          | Precision (Churn) | Recall (Churn) | F1-score |
|----------------|------------------|----------------|----------|
| Random Forest  | 0.28             | 0.34           | 0.30     |
| XGBoost        | 0.33             | 0.30           | 0.31     |

**Key Insight:**  
- Both models struggle to effectively identify churners due to severe class imbalance.  
- While XGBoost slightly improves precision, recall remains low (~30%), meaning many churn cases are still missed.  
- Indicates difficulty in capturing minority class  

---

## 💡 **8. Business Interpretation**

- If pricing alone were the dominant churn driver, stronger predictive performance would be expected. 
- The relatively low recall suggests that important customer behaviours are not represented in the available data.

---

## 📋 **9. Business Recommendations**

What should the company do?

Focus on new customers.
Improve onboarding.
Collect complaint history.
Combine pricing with behavioural analytics.

---

## ⚠️ **10. Limitations**
- Severe class imbalance affects model performance  
- Low recall indicates many churners are still missed  
- Limited behavioral features in dataset  

---

## 🔮 **11. Future Improvements**
- Apply advanced resampling techniques (e.g., SMOTE)  
- Experiment with ensemble and stacking models  
- Incorporate customer behavior and interaction data  
- Deploy model using a web app (Streamlit)  

---

## 🛠 **Tech Stack**
- Python  
- Pandas
- NumPy  
- Matplotlib
- Seaborn  
- Scikit-learn  
- XGBoost  

---

## 📁 Project Structure
                      customer-churn-prediction/
                      │
                      ├── notebooks/
                      │ └── analysis_and_modelling.ipynb
                      │
                      ├── dataset/
                      ├── outputs/
                      │
                      ├── README.md
                      └── requirements.txt

---

## 🌟 15. Final Takeaway

> This project taught me that data science is not only about building accurate models. It is also about testing business assumptions, understanding data limitations, and translating analytical findings into actionable business decisions.

---

### 🔗 **Connect**

- Name: Hanan
- LinkedIn: https://linkedin.com/in/hanan-nazri
- GitHub: https://github.com/hanannazri 
- Email: hanankp283@gmail.com 
