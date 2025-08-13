# Predictive-Customer-Churn-Modelling-with-Price-Sensitivity-Insights

This project investigates whether price sensitivity is the primary driver of customer churn for an energy provider.
Our main goal is to model churn probabilities and understand the extent to which changes in electricity and gas prices influence customer behavior.

## Project Background

Customer churn, when a client stops doing business with a company, can be influenced by many factors, such as industry type, usage patterns, service experience, or price changes.
We aim to test the hypothesis:

### *"Customers with higher price sensitivity are more likely to churn."*

To do this, we:

1. Define price sensitivity and calculate it using the price elasticity of demand formula:

                Price Elasticity = % change in quantity demanded/ % change in price

   a.Elastic (> 1) → Demand changes a lot when prices change. 
   b.Inelastic (< 1) → Demand changes little when prices change.

2. Prepare and engineer features from historical client, price, and churn data.
3. Train classification models Random Forest and XGboost to predict churn likelihood.
4. Identify how strongly price sensitivity affects churn compared to other factors.

## Key Data Sources

Customer Data – Characteristics such as industry, electricity consumption history, and join date.
Churn Data – Indicators showing whether a customer has churned.
Historical Price Data – Electricity and gas prices for each customer at granular time intervals.

## Why This Matters

Understanding whether churn is driven by price sensitivity helps the company:
Set better pricing strategies.
Identify at-risk customers earlier.
Focus retention efforts where they matter most.

## What This Notebook Does

### *Exploratory Data Analysis and Data Visualisation*
This file contains a Jupyter Notebook for analyzing customer churn and price sensitivity in the energy sector.

It walks through:
1. Loading client and price data from CSV files.
2. Exploring the datasets with descriptive statistics and previews.
3. Visualizing trends (e.g., seasonal price changes, differences between months) to find patterns related to churn.
4. Laying groundwork for feature engineering and model building for churn prediction.

### *Feature Engineering* 
This file contains a Jupyter Notebook focused on feature engineering for a customer churn and price sensitivity project.

What it does:

1. Data Loading – Reads client and price datasets using pandas.
2. Feature Creation – Builds new variables such as:
2.1 Monthly and yearly price changes.
2.2 Off-peak vs. peak price differences (e.g., December vs. January).
2.3 Date-derived fields like year, month, and season.
3. Data Cleaning – Handles missing values and formats data for analysis.
4. Visualization – Uses matplotlib and seaborn to check feature distributions and relationships.

These engineered features are intended to be inputs for churn prediction models, helping test whether price sensitivity is a major factor in customer churn.
 
### *Model Training and Evaluation*
This file contains a Jupyter Notebook for building and evaluating a machine learning classification model.

The workflow includes:

1. Model Training – Trains classification models with scikit-learn Random Forest and XGBoost.
2. Evaluation – Uses metrics such as confusion matrix, accuracy, precision to assess performance.

The notebook is intended as a complete reference for preprocessing, model building, and evaluation in a predictive analytics project.

## How To Use this

1️. Unzip the whole repository and make it your current working directory.

If downloaded as a ZIP:

                                          unzip repository.zip
                                          cd repository-folder

Or clone directly from Git:

                                           git clone <repo-link>
                                           cd repository-folder

2. Install all the required dependencies using the requirements.txt file: Open a terminal in your OS (Command Prompt, PowerShell, or Terminal on Linux/Mac) and type:   

                                       pip install -r requirements.txt

3️. Open the Jupyter Notebook: In the terminal, type:

                                              jupyter notebook
This will open the Jupyter interface in your browser.

4. Run the Notebook:
Open the provided .ipynb file from the repository. Click Run All to execute all cells sequentially.

The notebook will:
Load and preprocess the dataset.
Perform data visualization and exploratory analysis.
Train machine learning models.
Output performance metrics and graphs.

## Hybrid Observations – Random Forest vs. XGBoost

1. Consumption & Net Margin Dominate

*Random Forest*: cons_12m, net_margin, and margin_net_pow_ele are the strongest churn indicators, pointing to profitability and annual consumption as key drivers.

*XGBoost*: Confirms the same dominance but with slightly higher weight given to combined effects of consumption and margin. XGBoost detects more nuanced thresholds where consumption changes cause churn.

Interpretation:
Extreme consumption (very high or low) and profitability margins correlate with dissatisfaction or higher operational costs, leading to churn.

2. Contract Behavior & Timing Are Crucial

*Random Forest*: months_active, months_modif_prod, months_renewal, and tenure show strong influence, signaling loyalty and commitment patterns.

*XGBoost*: Places equal emphasis but also identifies interaction effects (e.g., how tenure combined with consumption impacts churn probability).

Interpretation:
Time-based behavioral patterns — engagement, contract modifications, renewal proximity — heavily influence churn likelihood.

3. Feature Engineering Validated

*Random Forest*: Engineered price-difference and peak usage variants outperform their raw counterparts but rank mid-tier.

*XGBoost*: Gives slightly higher importance to engineered interaction features, proving boosted trees leverage derived metrics more effectively.

Interpretation:
Thoughtful feature engineering improves prediction quality for both models, especially for non-linear models like XGBoost.

4. Price Sensitivity = Weak Contributor

*Random Forest*: Price-related features rank in the lower-middle, playing a supporting role.

*XGBoost*: Same trend, but with better integration into interaction effects (e.g., price × contract length).

Interpretation:
Price changes alone do not drive churn — they matter more when combined with other stressors like low margins or long tenure.

## Hybrid Conclusion

### *Both models pinpoint Consumption, Profitability Margins, and Contract Timing as the dominant churn predictors, with Price Sensitivity playing a secondary role.*

### For More Clarity
Go through the notebook step-by-step, each code cell is followed by output or visualizations that explain what’s happening.
The comments in the code and section headings will guide you through the logic.
