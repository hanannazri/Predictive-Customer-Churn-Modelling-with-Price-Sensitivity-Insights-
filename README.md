# Predictive-Customer-Churn-Modelling-with-Price-Sensitivity-Insights

This project investigates whether price sensitivity is the primary driver of customer churn for an energy provider.
Our main goal is to model churn probabilities and understand the extent to which changes in electricity and gas prices influence customer behavior.

### Project Background

Customer churn, when a client stops doing business with a company, can be influenced by many factors, such as industry type, usage patterns, service experience, or price changes.
We aim to test the hypothesis:

### *"Customers with higher price sensitivity are more likely to churn."*

To do this, we:

1. Define price sensitivity and calculate it using the price elasticity of demand formula:

                Price Elasticity = % change in quantity demanded/ % change in price

Elastic (> 1) → Demand changes a lot when prices change.
Inelastic (< 1) → Demand changes little when prices change.

2. Prepare and engineer features from historical client, price, and churn data.

3. Train classification models Random Forest and XGboost to predict churn likelihood.

4. Identify how strongly price sensitivity affects churn compared to other factors.

### Key Data Sources

Customer Data – Characteristics such as industry, electricity consumption history, and join date.
Churn Data – Indicators showing whether a customer has churned.
Historical Price Data – Electricity and gas prices for each customer at granular time intervals.

### Why This Matters

Understanding whether churn is driven by price sensitivity helps the company:
Set better pricing strategies.
Identify at-risk customers earlier.
Focus retention efforts where they matter most.

### What This Notebook Does

1. Loads the Data
2. Reads in the CSV files for both client and price data.
3. Initial Exploration: Displays the first few rows of each dataset to understand the structure.
4. Descriptive Statistics: Summarizes the datasets with basic statistics (e.g., mean, min, max, distribution).
5. Data Visualization: Uses matplotlib and seaborn to create plots and identify patterns or trends.

### How to Use
Make sure you have Python installed with the following libraries



For More Clarity
Go through the notebook step-by-step — each code cell is followed by output or visualizations that explain what’s happening.
The comments in the code and section headings will guide you through the logic.
