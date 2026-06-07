# 📊 **Customer Churn Prediction: Evaluating Price Sensitivity as a Business Driver**

![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange)
![Random Forest](https://img.shields.io/badge/Model-RandomForest-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---

## **Business Context**

This project was completed as part of the **BCGX Data Science Virtual Experience Program**.

The business team was working with a straightforward assumption:

> **Customers may be leaving because they are sensitive to changes in pricing.**

If that assumption is correct, the company could potentially improve retention through pricing adjustments, targeted discounts, or promotional offers.

However, before recommending any business action, I wanted to answer an important question:

**Does the available data actually support the idea that price sensitivity is one of the major drivers of customer churn?**

Rather than treating this as a simple machine learning exercise, I approached it as a business investigation using data.

---

## **Executive Summary**

To evaluate the business hypothesis, I combined customer information with historical pricing records and performed a complete analytical workflow consisting of:

* Data understanding
* Exploratory Data Analysis
* Feature Engineering
* Machine Learning Model Development
* Business Interpretation

After building and evaluating multiple models, I found that pricing contributes to customer churn, but it does not appear to be the dominant factor.

Instead, the results suggest that churn is likely influenced by a broader combination of factors such as customer tenure, product engagement, sales channels, contract history, and behavioral variables that are not captured in the available dataset.

One of the most valuable outcomes of this project was realizing that limited model performance itself can become an important business insight.

---

## **Business Problem**

For subscription-based businesses such as energy and gas providers, customer retention directly impacts long-term profitability.

Reducing churn by even a small percentage can generate significant business value.

A common business assumption is that customers leave primarily because of pricing changes.

If true, management could focus on:

* Discount campaigns
* Promotional pricing
* Tariff restructuring

However, implementing these strategies without evidence can reduce revenue while having little effect on retention.

The goal of this project was to determine whether the available data supports that assumption.

---

## **Project Objective**

Through this analysis, I wanted to answer four practical questions:

* Can customer churn be predicted using the available data?
* Is price sensitivity actually a major contributor to churn?
* Which customer characteristics appear most associated with churn?
* What additional business data would improve prediction performance?

---

## **Dataset Overview**

The analysis combines two datasets.

### **Customer Dataset**

Approximately **14,600 customers** containing information related to:

* Customer tenure
* Product subscriptions
* Sales channels
* Energy consumption
* Margins
* Forecast pricing
* Contract dates
* Churn status

### **Historical Pricing Dataset**

Approximately **193,000 pricing records** containing:

* Variable tariffs
* Fixed tariffs
* Peak pricing
* Mid-peak pricing
* Off-peak pricing
* Historical monthly pricing information

**Dataset Characteristics**

* Highly imbalanced target variable
* Roughly 90% retained customers
* Mixed numerical and categorical features
* Strong skewness in consumption variables
* Multiple business entities requiring transformation

---

## **Exploratory Data Analysis**

Before building any predictive models, I wanted to understand whether the business assumption could already be observed through the data.

**1. Customer Churn Distribution**

The first observation was the severe class imbalance, with churn representing only a small portion of the customer base.

This immediately influenced my evaluation strategy, since overall accuracy would not be sufficient for measuring model quality.

**2. Customer Tenure**

I explored whether the length of the customer relationship influenced retention.

The analysis showed that lower-tenure customers were considerably more likely to churn, suggesting that onboarding and early customer engagement may play an important role.

**3. Consumption Behaviour**

I investigated both raw and log-transformed consumption values to better understand customer usage patterns.

Although churned customers showed slightly different distributions, there was substantial overlap between both groups, indicating that consumption alone was not a strong predictor.

**4. Pricing Behaviour**

Since the original business question focused on price sensitivity, I carefully explored pricing variables across historical records.

I examined forecast pricing, variable tariffs, fixed tariffs, and monthly pricing behaviour to determine whether pricing alone could clearly distinguish churners from retained customers.

The analysis suggested that pricing contributes useful information but does not independently explain customer churn.

**5. Customer Segmentation**

I also explored churn across:

* Product engagement levels
* Billing segments
* Sales channels
* Margin groups

This helped identify customer groups that may require different retention strategies.

---

## **Feature Engineering**

Rather than relying only on the original variables, I created additional business-oriented features designed to better represent customer behaviour.

**1. Consumption Features**

To reduce skewness and capture usage changes over time, I engineered:

* Log-transformed consumption
* Consumption change metrics
* Consumption ratios

These features help describe how customer behaviour evolves rather than simply measuring absolute usage.

**2. Customer Value Features**

To better represent the customer's financial relationship with the company, I created:

* Estimated billing values
* Discount estimates
* Cost pressure indicators
* Net value scores
* Value-to-cost ratios

The intention was to approximate how customers may perceive the value they receive from the service.

**3. Contract and Lifecycle Features**

Customer lifecycle often influences retention.

To capture this, I engineered features including:

* Customer tenure groups
* Days until contract renewal
* Days since product modification

These variables help represent the stage of the customer's journey.

**4. Customer Segmentation Features**

I transformed several continuous variables into business-friendly categories:

* Billing buckets
* Margin bins
* Product engagement groups
* Sales channel categories

This allows the models to better capture differences between customer segments.

---

## **Model Development**

After completing exploratory analysis and feature engineering, I trained two ensemble machine learning models.

### **Random Forest**

Random Forest was selected as a robust baseline model capable of capturing non-linear relationships while remaining relatively interpretable.

### **XGBoost**

XGBoost was used to model more complex interactions between engineered features and compare its performance against the Random Forest baseline.

---

## **Evaluation Strategy**

The dataset contains a significant class imbalance, making accuracy an unreliable metric.

Instead, I focused primarily on:

* Precision
* Recall
* F1-score
* Confusion Matrix

> Special emphasis was placed on recall, since failing to identify customers who are likely to churn can directly affect business retention efforts.

---

## **Model Performance**

| Model         | Precision | Recall | F1-Score |
| ------------- | --------- | ------ | -------- |
| Random Forest | 0.28      | 0.34   | 0.30     |
| XGBoost       | 0.33      | 0.30   | 0.31     |

---

## **Business Interpretation**

At first glance, these results may appear modest.

However, I believe they provide one of the most valuable findings from the project.

If price sensitivity were truly the dominant reason customers leave, I would expect pricing-related variables to allow the models to identify churners much more effectively.

Instead, the relatively low recall suggests that important aspects of customer behaviour are missing from the available dataset.

Potential missing factors include:

* Customer complaints
* Service quality issues
* Customer support interactions
* Satisfaction metrics
* Service disruptions
* Competitor offers

In other words,

> **Price sensitivity appears to be part of the story, but not the entire story.**

---

## **Business Recommendations**

Based on the analysis, I would recommend that the business:

**1. Improve Early Customer Engagement**

Lower-tenure customers appear more vulnerable to churn.

Strengthening onboarding and early relationship management may improve retention.

**2. Expand Data Collection**

Future predictive systems should include:

* Complaint history
* Support tickets
* Customer satisfaction surveys
* Service interruption records

**3. Combine Pricing with Behavioral Analytics**

Rather than relying solely on discounts, retention strategies should integrate both financial and customer experience factors.

---

## **Project Limitations**

* Severe class imbalance
* Limited behavioral information
* Absence of customer interaction data
* External market factors unavailable

---

## **Future Improvements**

Potential next steps include:

* Applying advanced resampling techniques
* Hyperparameter optimization
* SHAP-based model explainability
* Ensemble and stacking methods
* Streamlit deployment
* MLflow experiment tracking
* Building a complete end-to-end MLOps pipeline

---

## **Tech Stack**

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* XGBoost

---

## **Repository Structure**

```text
customer-churn-price-sensitivity/
│
├── notebooks/
│   └── analysis_and_modelling.ipynb
│
├── dataset/
│
├── outputs/
│
├── README.md
│
└── requirements.txt
```

---

## **Final Reflection**

What I found most interesting about this project was that the model itself became part of the business answer.

I started with the assumption that price sensitivity might explain why customers leave.

After exploring the data, engineering business-oriented features, and evaluating multiple machine learning models, the evidence suggested that churn is likely a much broader behavioral problem.

This project reinforced for me that data science is not only about building predictive models.

It is also about challenging assumptions, understanding the limitations of available data, and translating technical analysis into practical business decisions.

---

## **Connect**

**Hanan**

* LinkedIn: https://linkedin.com/in/hanan-nazri
* GitHub: https://github.com/hanannazri
* Email: [hanankp283@gmail.com](mailto:hanankp283@gmail.com)
