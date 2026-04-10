# 📊 Customer Churn Prediction & Business Insights

## 🚀 Overview
This project focuses on predicting customer churn and uncovering actionable business insights using real-world, imbalanced data.

The goal is not just to build a machine learning model, but to understand why customers churn and how businesses can reduce it.

## 🎯 Objective
- Predict customers who are likely to churn  
- Identify key drivers behind churn behavior  
- Translate data insights into business recommendations  

## ⚡ Key Insights (TL;DR)
- Customers with low tenure are significantly more likely to churn  
- Energy consumption has weak correlation with churn  
- Pricing variables show limited predictive power  
- Severe class imbalance impacts model performance  
- XGBoost slightly outperforms Random Forest, but recall remains low  

👉 **Business Focus:** Improve early-stage customer experience to reduce churn  

## 📂 Dataset Description
The project uses multiple datasets including:
- Customer information  
- Energy consumption data (electricity & gas)  
- Pricing-related features  

### Key Characteristics:
- Highly imbalanced dataset (~90% non-churn)  
- Mix of numerical and categorical features  
- Presence of skewness and outliers  

## 🔍 Exploratory Data Analysis (EDA)

### Key Findings:
- 📉 Class Imbalance: Majority of customers do not churn  
- ⏳ Tenure: Strong inverse relationship with churn  
- ⚡ Consumption: Weak predictor of churn  
- 💰 Pricing: Limited direct impact on churn behavior  

---

## 🧠 Feature Engineering
- Handling skewed distributions  
- Outlier treatment  
- Encoding categorical variables  
- Feature selection and redundancy reduction  

---

## 🤖 Model Development

### Models Used:
- Random Forest Classifier  
- XGBoost Classifier  

### Key Approach:
- Addressed class imbalance  
- Tuned decision thresholds  
- Compared models using multiple evaluation metrics  

---

## 📈 Model Evaluation

Metrics used:
- Precision  
- Recall  
- F1-score  
- ROC-AUC  

### Key Observation:
- Models struggle with low recall for churn class  
- Indicates difficulty in capturing minority class  

---

## 💡 Business Recommendations
- 🎯 Focus on new customers (low tenure) for retention strategies  
- 🚀 Improve onboarding experience to reduce early churn  
- ⚡ Avoid relying solely on consumption-based targeting  
- 💰 Pricing adjustments alone may not significantly reduce churn  

---

## ⚠️ Limitations
- Severe class imbalance affects model performance  
- Low recall indicates many churners are still missed  
- Limited behavioral features in dataset  

---

## 🔮 Future Improvements
- Apply advanced resampling techniques (e.g., SMOTE)  
- Experiment with ensemble and stacking models  
- Incorporate customer behavior and interaction data  
- Deploy model using a web app (Streamlit)  

---

## 🛠 Tech Stack
- Python  
- Pandas, NumPy  
- Matplotlib, Seaborn  
- Scikit-learn  
- XGBoost  

---

## 📁 Project Structure
customer-churn-prediction/
│
├── notebooks/
│ └── churn_analysis.ipynb
│
├── data/
├── outputs/
│
├── README.md
└── requirements.txt

-----


---

## ▶️ How to Run
```bash
git clone https://github.com/YOUR_USERNAME/customer-churn-prediction.git
cd customer-churn-prediction
pip install -r requirements.txt
jupyter notebook

-----------------

## 🌟 Key Takeaway

This project demonstrates the ability to:
- Work with real-world, messy, imbalanced data
- Perform deep exploratory data analysis
- Build and evaluate machine learning models
- Translate technical results into business insights
