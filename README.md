# Customer Churn Analysis — Python

## Project Overview
Exploratory data analysis of credit card customer churn using Python,
identifying key behavioral and demographic patterns that distinguish
churned customers from retained customers in a financial services context.

## Business Question
Which customer characteristics and behaviors are most predictive
of credit card churn, and what early warning signals should trigger
retention interventions?

## Dataset
- Source: Kaggle — Credit Card Customers
- Records: 10,127 customers
- Features: 20 variables after cleaning
- Churn Rate: 16.07% (1,627 churned vs 8,500 retained)

## Tools Used
- Python 3.13
- pandas (data manipulation)
- matplotlib (visualization)
- seaborn (statistical visualization)
- Jupyter Notebook in VS Code
- GitHub (version control)

## Data Preparation
- Removed CLIENTNUM (non-analytical identifier)
- Removed two pre-built Naive Bayes score columns to avoid
  bias in independent analysis
- Confirmed zero missing values across all variables
- Dataset is moderately imbalanced — 84% retained vs 16% churned.
  A model predicting no churn for all customers would achieve
  84% accuracy but zero predictive value — noted as modeling
  consideration

## Key Findings

### 1. Overall Churn Rate
16.07% of customers churned — consistent with industry benchmarks
of 15-20% for credit card products

### 2. Transaction Activity — Strongest Signal
Churned customers show dramatically lower transaction activity:
- Total transaction amount: $3,095 vs $4,655 (33% lower)
- Total transaction count: 45 vs 69 (35% lower)
- The gap is consistent across the full distribution — 75% of
  churned customers spend less than $2,772 while 75% of retained
  customers spend more than $2,385

### 3. Inactivity Duration — Strong Early Warning Signal
Churn rate rises significantly with inactivity duration:
- 1 month inactive:  4.48%
- 2 months inactive: 15.39%
- 3 months inactive: 21.48%
- 4 months inactive: 29.89%
3 months inactivity = early warning threshold
4 months inactivity = urgent intervention point

### 4. Income — U-Shaped Churn Pattern
Churn is highest at income extremes:
- Less than $40K: 17.19% (affordability-driven churn)
- $120K+:         17.33% (competitive alternatives-driven churn)
- $60K-$80K:      13.48% (lowest churn — most stable segment)
This suggests two distinct churn risk profiles requiring
different retention strategies

### 5. Gender
Female customers churn at 17.36% vs 14.62% for male customers —
a 2.74 percentage point gap suggesting gender as a relevant
retention campaign segmentation variable

### 6. Age
Minimal variation across age groups (13.28% to 16.64%) —
age alone is not a meaningful churn predictor

### 7. Credit Limit
Modest difference between churned ($8,136) and retained ($8,727)
customers — credit limit is not a strong standalone churn signal

### 8. Correlation Insights
- Transaction amount and count are highly correlated (0.81) —
  measuring the same underlying engagement behavior
- Credit limit and average open-to-buy are nearly identical (0.99) —
  redundant variables for modeling purposes
- More product relationships correlate with lower transaction
  amounts (-0.35) — multi-product customers spread spending
  across products

## Business Recommendations

1. **Build retention triggers around transaction activity decline**
   rather than demographic profiles — transaction behavior is the
   strongest and most actionable churn signal

2. **Implement a 3-month inactivity alert** — customers reaching
   3 consecutive inactive months should trigger proactive outreach

3. **Segment retention campaigns by income:**
   - Low income (<$40K): affordability focused offers
   - High income ($120K+): premium value and competitive positioning

4. **Monitor female customer engagement** — slightly elevated churn
   rate warrants segment-specific retention analysis

## Relevance to Financial Services
This analysis reflects real-world churn modeling approaches applied
during prior roles at M&T Bank and Homesite Insurance, where customer
retention analytics informed product and marketing strategy decisions.
