# 📊 **Customer Churn Prediction: Evaluating Price Sensitivity as a Business Driver**

![Python](https://img.shields.io/badge/Python-3.9-blue?logo=python)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange)
![Random Forest](https://img.shields.io/badge/Model-RandomForest-blue)
![XGBoost](https://img.shields.io/badge/Model-XGBoost-green)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)

---
## **Executive Summary**

In this project, I investigated whether **price sensitivity is a major driver of customer churn for an energy provider.**

To evaluate this hypothesis, I combined customer information with historical pricing records and performed a complete analytical workflow consisting of:

* Exploratory Data Analysis
* Feature Engineering
* Feature Validation & Selection
* Machine Learning Modelling
* Business Interpretation

The results suggest that pricing contributes to customer churn but does not fully explain it. Instead, churn appears to be influenced by a broader combination of factors such as customer tenure, product engagement, contract history, and behavioural variables that were not available in the dataset.

One of the key insights from this project was that limited model performance itself became an important business finding, indicating that critical churn drivers may be missing from the available data.

---

## **Business Context & Problem**

This project was completed as part of the **BCGX Data Science Virtual Experience Program**, where I was presented with a business problem involving customer churn for an energy provider.

The client wanted to understand whether price sensitivity was a major factor influencing customer churn. From a business perspective, this is an important question because if pricing is the primary reason customers leave, retention strategies could focus on pricing adjustments, discounts, and promotional offers.

Before recommending any business action, I needed to determine whether the available data actually supported that assumption.

For subscription-based businesses such as energy providers, customer retention directly impacts long-term profitability. Even small increases in churn can result in significant revenue loss, making it important to understand the factors influencing customer behaviour.

In this project, I analysed customer and historical pricing data to investigate the client's hypothesis, identify patterns associated with churn, and evaluate whether price sensitivity alone could explain customer attrition.

Rather than treating the task as a purely machine learning problem, I approached it as a business investigation, starting with exploratory analysis, validating assumptions through data, engineering business-oriented features, and ultimately translating the modelling results into actionable business insights.

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

* Customer churn status
* Customer tenure
* Number of active products
* Electricity and gas consumption
* Gross and net margins
* Sales channels
* Forecast energy pricing
* Contract activation dates
* Contract renewal dates
* Product modification history

### **Historical Pricing Dataset**

Approximately **193,000 pricing records** containing:

* Variable tariffs
* Fixed tariffs
* Peak pricing
* Mid-peak pricing
* Off-peak pricing
* Historical monthly pricing information

### **Dataset Characteristics**

* Highly imbalanced target variable
* Roughly 90% retained customers
* Mixed numerical and categorical features
* Strong skewness in consumption variables
* Multiple business entities requiring transformation

---

## **Client Exploratory Data Analysis**

To investigate the business hypothesis, I performed exploratory analysis on both the client dataset and the historical pricing dataset.

### **Client Dataset Features**

The client dataset contains operational, contractual, pricing, and consumption-related information for approximately 14,600 customers.

These variables form the foundation for analysing customer behaviour and investigating whether price sensitivity contributes to churn.

### **Data Quality Assessment**

Before beginning the analysis, I evaluated the overall quality of the dataset.

The client dataset contains a mixture of numerical and categorical variables. Several consumption-related features exhibited strong right-skewness and extreme observations, motivating later transformations during feature engineering.

### **1. Data Understanding**

### **1.1 Churn Distribution**

The first step was to understand the scale of the churn problem itself.

The dataset is highly imbalanced, with approximately 90% of customers remaining with the company and only around 10% leaving.

This imbalance is common in real-world churn prediction problems and immediately influenced the modelling strategy adopted later in the project. Rather than relying on overall accuracy, greater emphasis would eventually be placed on Precision, Recall, and F1-score.

### **1.2 Energy Consumption Distribution**

I explored the distribution of annual electricity consumption to understand customer usage behaviour.

The analysis showed that energy consumption is heavily right-skewed, with a relatively small number of customers consuming significantly more energy than the majority of the population.

This observation suggested that raw consumption values might not be ideal for modelling directly and motivated the creation of `cons_12m_log` during the feature engineering stage.

### **1.3 Last Month Energy Consumption**

In addition to annual consumption, I also explored customer energy usage during the most recent month.

Comparing recent consumption with long-term behaviour provides useful insight into whether changing consumption patterns may be associated with churn.

Although some differences were observed across customers, the distributions still showed substantial overlap between churned and retained groups, suggesting that recent consumption alone was unlikely to fully explain customer churn.

### **1.4 Gas Consumption Distribution**

Gas consumption was analysed separately from electricity consumption to determine whether it provided additional information regarding customer behaviour.

Similar to electricity usage, gas consumption displayed a highly skewed distribution. After examining both the raw and transformed distributions, it became evident that gas consumption alone was unlikely to serve as a strong standalone predictor of churn.

### **2. Customer Behaviour Analysis**

### **2.1 Comparison of Energy Consumption with Churn**

After understanding the overall consumption distributions, I compared the distributions of annual electricity consumption for churned and retained customers to determine whether usage behaviour alone could explain customer attrition.

Although churned customers exhibited slightly different consumption patterns, the overlap between both groups remained considerable. This suggests that while consumption contributes some information, it does not independently explain customer churn.

### **2.2 Comparison of Gas Consumption with Churn**

A similar comparison was performed using gas consumption.

The analysis revealed only modest differences between churned and retained customers, reinforcing the idea that customer behaviour is influenced by factors beyond simple energy usage.

### **2.3 Product Engagement with Churn**

I investigated the relationship between the number of active products and customer churn.

Rather than assuming that customers with more products are automatically more loyal, this analysis explored how churn rates changed across different levels of product engagement.

The results provided additional context regarding customer behaviour and highlighted the importance of considering engagement alongside pricing variables.

### **2.4 Tenure with Churn**

Customer tenure was one of the most informative variables explored during the EDA process.

The analysis showed that customers with shorter relationships to the company were generally more likely to churn, while long-term customers tended to exhibit greater stability.

From a business perspective, this suggests that customer onboarding and early-stage relationship management may play an important role in reducing churn.

---

## **Price Exploratory Data Analysis**

Since the original business hypothesis centered around price sensitivity, I performed a separate exploratory analysis on the historical pricing dataset.

The objective was to determine whether pricing behaviour alone could provide a strong explanation for customer churn.

### **Price Dataset Features**

The pricing dataset contains approximately **193,000 historical pricing records**, including:

- Off-peak variable pricing
- Peak variable pricing
- Mid-peak variable pricing
- Off-peak fixed pricing
- Peak fixed pricing
- Mid-peak fixed pricing

These records capture how customer pricing evolves over time and provide the foundation for evaluating the business hypothesis.

### **Data Quality Assessment**

The pricing dataset was reviewed to understand its completeness and overall structure before further analysis.

Since pricing information spans multiple periods, maintaining consistency across historical records was important for later feature engineering.

### **3. Price Sensitivity Analysis**

### **3.1 Time-Based Analysis**

Since pricing records were collected across multiple time periods, I first analysed how variable and fixed pricing components evolved over time. This helped determine whether consistent pricing trends or seasonal patterns existed that could potentially influence customer churn.

### **3.2 Distribution of Variable Price Analysis**

The distribution of variable pricing components was analysed to understand their overall behaviour across the customer base.

The analysis showed natural variation in customer pricing, but no immediately obvious separation between churned and retained customers.

### **3.3 Distribution of Fixed Price Analysis**

Fixed pricing components were also explored independently.

Comparing the distributions of fixed and variable prices provided additional context regarding how pricing structures are represented within the dataset.

### **3.4 Relationship Between Pricing Features**

To better understand interactions between different pricing variables, I explored the relationships between pricing variables to understand how different pricing components interacted and whether certain features provided redundant information. This analysis also provided insight into how different pricing components move together across the customer base.

### **3.5 Fixed vs Variable Price Analysis**

Finally, I compared the behaviour of fixed and variable pricing structures to determine whether one appeared to have a stronger association with customer churn. Although both contributed useful information, neither independently provided a clear separation between churned and retained customers.

---

### **Key Insights from Exploratory Data Analysis**

The exploratory analysis produced several important observations:

- The dataset exhibits significant class imbalance.
- Electricity and gas consumption variables are highly skewed.
- Logarithmic transformations are appropriate for several consumption features.
- Customer tenure appears to have a stronger relationship with churn than raw consumption measures.
- Product engagement provides useful customer segmentation information.
- Historical pricing contributes valuable information but does not independently explain customer churn.
- No single variable appeared capable of explaining churn independently, suggesting that customer attrition is likely driven by multiple interacting factors.
  
Overall, the EDA phase suggested that:

> Price sensitivity may influence customer decisions, but customer churn is likely driven by a broader combination of behavioural, operational, and contractual factors.

---

## **Feature Engineering**

The exploratory analysis suggested that customer churn could not be fully explained by any single variable. Although pricing contributed useful information, the EDA indicated that customer decisions were likely influenced by a combination of consumption behaviour, customer value, contract history, and pricing dynamics.

To better capture these underlying relationships, I engineered additional features that transform raw operational data into more meaningful business indicators.

### **1. Numerical Data Transformation**

Several consumption-related variables exhibited strong right-skewness during the exploratory analysis. Rather than using these raw values directly, I applied logarithmic transformations to stabilize the distributions while preserving the relative differences between customers.

The transformed variables include:

* `cons_12m_log`
* `cons_last_month_log`

These transformations reduce the influence of extreme observations and provide a more balanced representation of customer consumption behaviour.

### **2. Categorical Data Transformation**

Several categorical variables contained multiple sparse categories that could reduce model interpretability.

To improve consistency while preserving their business meaning, I grouped and transformed a number of categorical variables, including:

* `tenure_group`
* `renewal_bin`
* `modif_bin`
* `bill_bucket`
* `bill_bucket_no_discount`
* `margin_bin`
* `prod_group`

The `channel_sales` variable was also simplified by grouping less frequent categories together, allowing the models to focus on broader customer acquisition patterns.

### **3. Business-Oriented Feature Creation**

While the original dataset provides operational information, many business relationships are not directly represented by individual variables.

To better capture customer behaviour and price sensitivity, I engineered several additional features.

### **3.1 Consumption Behaviour Features**

Rather than relying only on absolute consumption values, I created variables that describe how customer usage changes over time.

The following features were engineered:

* `cons_change`
* `cons_ratio`

These variables help capture whether recent customer activity differs significantly from long-term consumption behaviour.

### **3.2 Estimated Billing and Discount Features**

Since pricing is central to the business hypothesis, I engineered estimated customer billing behaviour by combining pricing and consumption information.

The following features were created:

* `estimated_bill`
* `estimated_bill_no_discount`

To further improve interpretability, these values were later grouped into:

* `bill_bucket`
* `bill_bucket_no_discount`

These features help investigate whether customers experiencing different estimated billing levels exhibit different churn behaviour.

### **3.3 Cost Pressure and Customer Value Features**

One of the main objectives of this project was to evaluate whether customers become sensitive to pricing.

To better represent this relationship, I engineered variables that combine pricing information with customer usage characteristics. The following features were created:

* `cost_pressure`
* `cost_per_year`
* `net_value_score`

Rather than measuring pricing alone, these variables attempt to capture the balance between the costs customers incur and the value they receive from the service.

### **3.4 Contract Timeline Features**

Customer lifecycle events often influence retention decisions.

To incorporate these effects, I engineered contract-related timeline variables:

* `days_from_modif`
* `days_from_renewal`

These features provide additional information about where a customer is positioned within their contractual relationship with the company.

### **3.5 Price Change Features: January vs December**

Since the central business hypothesis focuses on price sensitivity, I investigated whether changes in pricing between different periods could provide additional predictive information.

Using the historical pricing dataset, I created the following price change features:

* `off_var`
* `off_fix`
* `peak_var`
* `peak_fix`
* `mid_var`
* `mid_fix`

These variables capture the differences between January and December pricing observations.

### **3.6 Monthly Price Difference Features**

In addition to the January versus December comparison, I engineered features describing the maximum monthly differences across the pricing history.

The following variables were created:

* `mon_off_peak_var_max`
* `mon_peak_mid_var_max`
* `mon_off_mid_var_max`
* `mon_off_peak_fix_max`
* `mon_peak_mid_fix_max`
* `mon_off_mid_fix_max`

These features provide a broader representation of how customer pricing evolves over time.

### **3.7 Margin Redundancy Check**

Before finalising the modelling dataset, I evaluated the relationship between existing margin-related variables and the newly engineered customer value features.

This step helped identify potential redundancy and ensured that the engineered features contributed additional business information rather than duplicating existing variables.

---

## **Feature Validation & Selection**

Engineering new features does not automatically improve a machine learning model. Before moving to the modelling stage, I wanted to verify that the engineered variables contributed meaningful information and did not simply duplicate existing patterns within the dataset.

This stage focused on validating the usefulness of the newly created features and identifying unnecessary redundancy before model training.

### **1. Validation of Energy Consumption Features**

During feature engineering, I introduced transformed and behaviour-based consumption variables, including:

* `cons_12m_log`
* `cons_last_month_log`
* `cons_change`
* `cons_ratio`

These engineered features were evaluated to determine whether they provided a better representation of customer consumption behaviour and captured additional information that could be useful for churn prediction.

### **2. Validation of Estimated Billing Features**

To better represent the customer's pricing experience, I engineered:

* `estimated_bill`
* `estimated_bill_no_discount`

along with their corresponding grouped variables:

* `bill_bucket`
* `bill_bucket_no_discount`

These features were validated to determine whether combining pricing and consumption information produced more meaningful business indicators than the original variables alone.

### **3. Correlation Analysis of Engineered Pricing Features**

Several pricing-related features were created during the feature engineering stage, including:

* January vs December price change features
* Monthly price difference features
* Cost pressure and customer value features

I analysed the relationships between these engineered pricing variables to identify potential redundancy before model development.

### **4. Global Correlation Analysis**

After combining the original and engineered variables, I performed a broader correlation analysis across the modelling dataset.

The purpose of this step was to better understand the relationships between the available features and remove unnecessary overlap where multiple variables captured similar information.

### **5. Feature Importance Analysis**

Before training the final models, I also examined the relative importance of the available features.

This analysis helped identify which variables contributed meaningful predictive information while reducing the influence of negligible predictors within the final modelling dataset.

---

## **Model Training & Evaluation**

After validating the engineered features, I moved to the modelling stage.

Since the dataset is highly imbalanced, the objective was not simply to maximise accuracy. Instead, the focus was on identifying customers who are likely to churn while maintaining a reasonable balance between false positives and false negatives.

For this reason, model performance was evaluated primarily using:

* Precision
* Recall
* F1-score
* Confusion Matrix Analysis

Particular emphasis was placed on **Recall**, since failing to identify customers who are likely to leave can directly impact retention efforts.

### **1. Train-Test Split**

Before model development, the dataset was divided into training and testing subsets.

This ensures that model performance is evaluated on unseen data and provides a realistic assessment of how the models would perform in a real-world business setting.

### **2. Random Forest**

Random Forest was selected as the first modelling approach because of its ability to capture non-linear relationships while remaining relatively robust to noisy and complex business data.

### **Baseline Random Forest**

The baseline Random Forest model was trained using the engineered feature set without additional optimisation.

This provided an initial benchmark for understanding how effectively the available data could identify churned customers.

### **Threshold Optimization**

Because churn prediction is a highly imbalanced classification problem, the default classification threshold may not provide the best balance between Precision and Recall.

To improve churn detection performance, I evaluated different probability thresholds and selected the threshold that produced a stronger balance between identifying churners and controlling false positives.

### **SMOTE with Threshold Optimization**

To further address class imbalance, I applied SMOTE (Synthetic Minority Oversampling Technique) to the training data.

The objective was to increase the representation of churned customers and evaluate whether additional minority-class examples could improve Recall performance.

Threshold optimisation was then repeated on the resampled dataset.

### **Random Forest Summary**

The Random Forest experiments demonstrated that both threshold optimisation and class balancing techniques can improve the model's ability to identify churners.

However, overall performance remained limited, suggesting that important drivers of churn may not be fully represented within the available dataset.

### **3. XGBoost**

Following the Random Forest experiments, I trained an XGBoost model to evaluate whether a gradient boosting approach could better capture complex interactions between customer behaviour, pricing dynamics, and contract information.

### **Baseline XGBoost**

The baseline XGBoost model was trained using the same engineered feature set and evaluation framework used for Random Forest.

This provided a consistent basis for comparing both modelling approaches.

### **Threshold Optimization**

Similar to the Random Forest workflow, threshold optimisation was applied to improve the balance between Precision and Recall.

The objective was to identify a classification threshold that better aligned with the business goal of detecting customers who are likely to churn.

### **Tuned XGBoost Model**

After evaluating the baseline model, hyperparameter tuning was performed to further improve predictive performance.

This stage focused on optimising model complexity and learning behaviour while maintaining generalisation performance on unseen data.

### **XGBoost Summary**

Across the different experiments, XGBoost demonstrated slightly stronger predictive performance than Random Forest and showed a greater ability to identify churned customers.

This made it the strongest candidate for final model selection.

### **4. Final Model Comparison & Selection**

| Model Configuration | Precision (Churn) | Recall (Churn) | F1-score (Churn) | Accuracy |
|-----------------------|------------------|----------------|------------------|----------|
| Random Forest + Threshold (0.20) | 0.28 | 0.31 | 0.30 | 0.85 |
| Tuned XGBoost | 0.28 | 0.32 | 0.30 | 0.85 |

Both models achieved similar overall performance, but the tuned XGBoost model achieved slightly higher churn recall.

The comparison shows that churn prediction remains challenging, highlighting the limitations of the available dataset and the absence of behavioural variables that may influence customer retention.

### **5. Business-focused Confusion Matrix Analysis**

Although the overall evaluation metrics were similar, the confusion matrix analysis revealed an important difference.

| Model | Churn Customers Correctly Identified |
|--------|--------|
| Best Random Forest | 84 |
| Tuned XGBoost | 93 |

The tuned XGBoost model correctly identified nine additional churn customers compared to the best-performing Random Forest model.

From a business perspective, each correctly identified churn customer represents an opportunity for targeted retention efforts. For this reason, the additional churn detection capability provided by XGBoost was considered more valuable than the slight increase in false positives.

### **6. Final Model Selection**

After comparing all modelling approaches, the tuned XGBoost model was selected as the final model.

The decision was based not only on evaluation metrics but also on its stronger ability to identify churned customers during confusion matrix analysis.

More importantly, the modelling results reinforced one of the central findings of this project:

> The available pricing and customer data contain useful information, but they are not sufficient to fully explain customer churn.

This suggests that additional behavioural and customer experience variables are likely required to significantly improve churn prediction performance.

---

## **Business Implications & Recommendations**

The original business hypothesis suggested that customer churn may be primarily driven by price sensitivity.

While the analysis showed that pricing-related variables contribute useful information, the modelling results indicate that pricing alone is not sufficient to fully explain customer churn.

Several customer characteristics appeared to provide stronger signals than pricing variables alone, particularly customer tenure, product engagement, contract history, and broader behavioural patterns.

Based on these findings, the following recommendations can be considered:

### **1. Focus on Early Customer Retention**

The analysis suggests that customers with shorter tenure are more likely to churn.

Improving onboarding experiences, customer engagement during the early stages of the customer lifecycle, and proactive support programs may help reduce customer attrition.

### **2. Move Beyond Pricing-Only Retention Strategies**

Although pricing influences customer behaviour, reducing prices alone is unlikely to significantly improve retention.

Customer retention initiatives should incorporate a broader understanding of customer behaviour, engagement, and service experience.

### **3. Improve Data Collection**

The relatively modest model performance suggests that important churn drivers are not fully represented in the available dataset.

Additional information such as:

* Customer complaints
* Customer support interactions
* Service quality metrics
* Customer satisfaction indicators
* Marketing engagement data

could significantly improve future churn prediction efforts.

### **4. Develop Behaviour-Based Retention Programs**

Future retention strategies should combine pricing information with behavioural indicators to identify customers who are genuinely at risk of leaving.

---

## **Project Limitations**

- **Severe class imbalance:** Only a small proportion of customers had churned, making churn detection challenging.
- **Limited behavioural information:** The dataset did not include complaints, service quality, customer satisfaction, or support interaction history.
- **Moderate predictive performance:** Despite feature engineering and model optimisation, Recall and F1-score remained modest.
- **Hypothesis scope:** The project focused on evaluating price sensitivity, but churn is likely influenced by multiple interacting factors.

---

## **Future Improvements**

Potential next steps include:

- Exploring additional resampling strategies to further address class imbalance.
- Incorporating behavioural data such as complaints, support interactions, service interruptions, satisfaction scores, and engagement indicators.
- Testing additional ensemble or stacking approaches.
- Deploying the final model through a Streamlit application for business users.
- Monitoring model performance over time to detect changes in customer behaviour.

---

## **Tech Stack**

### **Programming & Data Processing**

* Python
* Pandas
* NumPy

### **Data Visualization**

* Matplotlib
* Seaborn

### **Machine Learning**

* Scikit-learn
* XGBoost

### **Feature Engineering & Model Evaluation**

* SMOTE
* Precision, Recall, F1-score Analysis
* Confusion Matrix Analysis
* Feature Importance Analysis

---

## **Repository Structure**

```text
customer-churn-price-sensitivity/
│
├── dataset/
│   ├── client_data.csv
│   └── price_data.csv
│
├── notebooks/
│   └── analysis_and_modelling.ipynb
│
├── outputs/
│   ├── visualizations/
│   ├── feature_analysis/
│   └── model_evaluation/
│
├── README.md
│
└── requirements.txt
```

---

## **Final Takeaway**

This project began with a simple business question:

> **Is price sensitivity a major driver of customer churn?**

Through exploratory analysis, feature engineering, feature validation, and machine learning modelling, the results suggest that pricing contributes to customer churn but does not fully explain it.

More importantly, the project demonstrated that limited model performance can itself become a valuable business insight.

The findings indicate that customer churn is likely influenced by a broader combination of behavioural, operational, and customer experience factors that were not captured within the available data.

For me, the most valuable lesson from this project was understanding that data science is not only about building predictive models. It is also about testing business assumptions, identifying data limitations, and translating analytical findings into actionable business decisions.

---

## **Connect**

**Hanan**

Aspiring Data Scientist | Machine Learning Enthusiast

* LinkedIn: https://linkedin.com/in/hanan-nazri
* GitHub: https://github.com/hanannazri
* Email: [hanankp283@gmail.com](mailto:hanankp283@gmail.com)
