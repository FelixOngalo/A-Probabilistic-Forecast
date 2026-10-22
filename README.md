# Probabilistic Customer Lifetime Value Forecasting in R

## Project Overview

This project develops a probabilistic **Customer Lifetime Value (CLV)** forecasting pipeline in R using the **BG/NBD** and **Gamma-Gamma** models.

The analysis estimates future customer purchasing behaviour and monetary value, validates model performance using **calibration and holdout periods**, and identifies high-priority customers for **win-back campaigns** based on predicted customer value and probability of churn.

## Objectives

- Estimate customer purchasing frequency and future transaction behaviour.
- Predict the probability that customers remain active.
- Estimate expected monetary value for individual customers.
- Calculate probabilistic Customer Lifetime Value.
- Validate model predictions using calibration and holdout periods.
- Identify customers with high potential value but elevated churn risk.
- Develop a data-driven target list for customer win-back campaigns.

## Methodology

### 1. Data Preparation

Customer transaction data is transformed into the format required for probabilistic modelling. Key variables include:

- Customer ID
- Transaction date
- Transaction value
- Purchase frequency
- Recency
- Customer observation period

The data is divided into **calibration** and **holdout** periods to evaluate how well the models predict future behaviour.

### 2. BG/NBD Model

The **Beta-Geometric/Negative Binomial Distribution (BG/NBD)** model is used to estimate customer purchasing behaviour.

It models:

- Expected future transactions
- Customer activity
- Probability that a customer is still active

This allows the analysis to distinguish between customers who are genuinely inactive and those who may simply be between purchases.

### 3. Gamma-Gamma Model

The **Gamma-Gamma model** estimates the expected monetary value of future transactions.

Combined with BG/NBD predictions, it provides an estimate of each customer's future economic value.

### 4. Customer Lifetime Value

The models are combined to estimate **probabilistic CLV**, providing a forward-looking measure of customer value rather than relying solely on historical spending.

### 5. Calibration and Holdout Validation

Model performance is evaluated by comparing predicted customer behaviour against actual transactions observed during the holdout period.

This provides an assessment of how effectively the models generalise to future customer behaviour.

### 6. Win-Back Targeting

Customers are segmented using predicted CLV and probability of churn/activity.

A priority group is identified consisting of customers who have:

- High predicted future value
- Higher probability of becoming inactive
- Sufficient historical purchasing behaviour to justify re-engagement

These customers represent potential targets for targeted **win-back campaigns**.

## Analytical Workflow

```text
Transaction Data
       ↓
Data Cleaning & Preparation
       ↓
Calibration / Holdout Split
       ↓
BG/NBD Model
       ↓
Expected Future Transactions
       ↓
Gamma-Gamma Model
       ↓
Expected Monetary Value
       ↓
Probabilistic CLV
       ↓
Model Validation
       ↓
Churn / Activity Analysis
       ↓
Win-Back Customer Targeting
```

## Technologies Used

- **R**
- `dplyr`
- `ggplot2`
- `tidyr`
- `lubridate`
- `readr`
- BG/NBD modelling
- Gamma-Gamma modelling
- Probabilistic customer analytics

## Key Outputs

The project produces:

- Customer-level predicted transactions
- Probability of customer activity/churn
- Expected average monetary value
- Predicted Customer Lifetime Value
- Calibration vs. holdout performance analysis
- Customer value and churn segments
- Prioritised win-back target list
- Data visualisations supporting business decisions

## Business Value

The analysis demonstrates how probabilistic modelling can move customer analytics beyond historical reporting toward **predictive decision-making**.

Instead of treating all inactive customers equally, the model helps identify customers who may be worth re-engaging based on their expected future value and likelihood of churn.

This can help businesses:

- Prioritise retention spending
- Improve customer targeting
- Reduce inefficient blanket promotions
- Identify high-value customers at risk of churn
- Support data-driven CRM and marketing strategies

## Project Structure

```text
probabilistic-clv-r/
│
├── data/
│   └── transactions.csv
│
├── R/
│   ├── 01_data_preparation.R
│   ├── 02_bgnbd_model.R
│   ├── 03_gamma_gamma_model.R
│   ├── 04_clv_forecasting.R
│   ├── 05_model_validation.R
│   └── 06_winback_targeting.R
│
├── figures/
│   ├── calibration_holdout.png
│   ├── clv_distribution.png
│   └── winback_segments.png
│
├── results/
│   └── winback_targets.csv
│
├── report/
│   └── clv_analysis.qmd
│
└── README.md
```

## Validation Approach

The dataset is divided into two periods:

**Calibration period:** Used to estimate customer behaviour and fit the probabilistic models.

**Holdout period:** Contains future transactions that are not used during model fitting. Predictions are compared with these actual outcomes to assess model performance.

This approach provides a more realistic evaluation of predictive performance than evaluating the model only on the data used to train it.

## Win-Back Strategy

The final analysis combines customer value and churn risk to identify potential win-back opportunities.

A customer with **high predicted CLV and high churn probability** may represent a particularly valuable retention opportunity.

The resulting target list can be used by marketing or CRM teams to prioritise personalised re-engagement campaigns.

## Reproducibility

To reproduce the analysis:

1. Install R and the required packages.
2. Place the transaction dataset in the `data/` directory.
3. Run the scripts in the `R/` directory in sequence.
4. Review the generated results and visualisations.
5. Render the Quarto report in the `report/` directory.

## Skills Demonstrated

This project demonstrates practical skills in:

- Customer analytics
- Predictive modelling
- Probabilistic modelling
- Customer Lifetime Value estimation
- Statistical validation
- R programming
- Data manipulation with `dplyr`
- Data visualisation with `ggplot2`
- Customer segmentation
- Churn-risk analysis
- Marketing analytics
- Data-driven decision-making

## Conclusion

The project demonstrates an end-to-end approach to probabilistic CLV forecasting, from transaction-level data preparation through model fitting, validation, customer value estimation, and actionable win-back targeting.
