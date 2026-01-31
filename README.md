# SQL Project – Sales Analysis 

## Overview
Analysis of customer behavior, retention patterns, and lifetime value to optimize revenue growth and drive higher customer retention, using an e-commerce Contoso dataset

## Questions

1. **Customer Segmentation**: Who are the most valuable customers and how much do they contribute to the revenue?
2. **Cohort Analysis**: How have contributions evolved over time?
3. **Retention Analysis**: What is the churn rate, which customers haven't purchased recently?

## Technical Details
- **Database**: PostgreSQL
- **Analysis Tools**: DBeaver, Visual Studio Code
- **Visualization**: Power BI

## Analysis

### Data preparation
**Query**: [0_view_creation.sql](/Scripts/0_view_creation.sql)
- Segmented customers into cohort years based on first year of purchase
- Created view combining customer and sales details
---
### 1. Customer Segmentation

- Assigned customers to low-, mid-, and high-value sections based on total lifetime value (LTV) contributed
- Calculated the total revenue for each segment

**Query**: [1_customer_segmentation.sql](/Scripts/q1_customer_segmentation.sql)

![Customer LTV Distribution](/Visuals/q1.png)

**Key Findings**:
- Low-value segment (25% of customers) generates only 2% of the revenue
- Mid-value segment (50%  of customers) contributes to 32% of the revenue
- High-value segment (25% of customers) accounts for 66% of the revenue

**Proposal**:
- Low-value segment: Maximize re-engagement and create price-sensitive promotions to boost purchase frequency
- Mid-value segment: Aim to upgrade members to the high-value segment through personalized promotions, unlocking a potential revenue increase from $66M to $136M
- High-value segment: Introduce a premium membership program for this group, since losing even one customer substantially affects revenue
---
### 2. Cohort Analysis
- Older cohorts have more time to accumulate revenue
- Further analysis ([2.0_cohort_analysis.sql](/Scripts/q2.0_cohort_analysis.sql)) reveals that 62% of a customer’s lifetime spending occurs on the first purchase day
- To account for the time discrepancy between the cohorts, only first-day spending is used for revenue calculations
---
- Analyzed average customer revenue per cohort years

**Query**: [2.1_cohort_analysis.sql](/Scripts/q2.1_cohort_analysis.sql)

![Customer Revenue by First Purchase Year](/Visuals/q2.1.png)

**Key Findings**:
- Average customer spending is decreasing, older cohort members spent around $3,000, later cohorts spent only around $2,000
- Trend line shows an intensifying downward trend
---
- Diving deeper, analyzed monthly total net revenue and customer count on a 3 month rolling average basis

**Query**: [2.2_cohort_analysis.sql](/Scripts/q2.2_cohort_analysis.sql)

![Revenue and Customers](/Visuals/q2.2.png)

**Key Findings**:
- Net revenue and customer count peaked in 2022 / early 2023, both metrics are trending downward since
- Generally, more customers meant more revenue, but starting in late 2022, customers spent considerably less
- The high volatility in revenue and customer count implies retention challenges

**Proposal**:
- Implement previous strategies from higher-spending cohorts (2015–2019) to newer cohorts to maximize revenue potential
- Smooth revenue and customer count volatility by implementing loyalty programs or subscription models to promote consistent customer spending
- Target recent cohorts (2022–2024) with personalized promotions to boost retention and prevent churn
---
### 3. Customer Retention
- Analyzed purchase patterns
- Segmented customers into active (purchased within the last 6 months) and churned groups

**Query**: [3_customer_retention.sql](/Scripts/q3_retention_analysis.sql)

![Customer Retention by Cohort Year](/Visuals/q3.png)

**Key Findings**:
- Retention rates are consistently low across all cohort years at 9-10%, implying systemic retention problems 
- Without changes, future cohorts will likely exhibit similarly low retention rates

**Proposal**:
- Create targeted re-engagement campaigns towards the most valuable customers to prevent long-term churn
- Anticipate churn by tracking personalized risk indicators and intervening proactively to retain at-risk users
- Focus on the early customer lifecycle by deploying onboarding benefits, engagement perks, and customized offers to increase long-term retention

