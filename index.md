---
layout: page
title: Overview
permalink: /
---

# Retention Radar: Customer Churn Data Prep

![Cancellation Rate]({{ site.baseurl }}/assets/images/cancellation_rate.png)

## Key Insights  
- Customers who received a discount exhibit a significantly higher cancellation rate than those who didn’t.  
- This suggests discount-driven sign-ups may lack long-term commitment, pointing to a need for targeted retention strategies.

## Context  
An online streaming service has experienced a worrying uptick in customer cancellations over the past quarter. Leadership suspects hidden patterns in subscription behavior and listening habits are driving churn—and they want a data-driven diagnosis before building any prediction models.

## Scope  
Identify customers at high risk of canceling their subscription based on their streaming activity and account status over the past three months.

## Objective  
1. Scope the churn-analysis project end to end  
2. Ingest customer and listening-history data into Python  
3. Clean and standardize all fields, resolve data issues, and derive new columns  
4. Explore and visualize key churn drivers both independently and after joining tables  
5. Deliver a final, non-null, numeric DataFrame with engineered features ready for modeling

## Process  
1. Project scoping & stakeholder alignment  
   - Reviewed goals with Customer Care to confirm data sources and churn definition  
   - Clarified deliverables: analysis-ready dataset + exploratory visuals  
2. Data ingestion  
   - Loaded customer profiles and streaming-history CSVs using Pandas  
   - Verified schema, identified missing or invalid entries, then dropped irreparable rows  
3. Data cleaning & feature derivation  
   - Harmonized date fields (subscription start, cancellation) to datetime  
   - Imputed or removed missing values in key columns (subscription rate , subscription plan)  
   - Engineered new features: tenure_days, avg_listens_per_day, last_month_play_count, genre_diversity_score  
4. Exploratory analysis  
   - Discount vs. churn  
     • Only 7 customers received a discount, and around 86% of them canceled—compared to about 30% churn among non-discount users.  
   - Distribution of Listening Sessions  
   ![Distribution of Listening Sessions per Customer]({{ site.baseurl }}/assets/images/listening_sessions_distribution.png)  
      • We counted how many separate listening sessions each user had over three months. Most people fell between 1–5 sessions, suggesting a sizable low-engagement group.  

   - Genre Popularity  
   | Genre      | Count |
   |------------|------:|
   | Pop        |   267 |
   | Hip Hop    |    88 |
   | Country    |    68 |
   | Jazz       |    48 |
   | Comedy     |    19 |
   | True Crime |    15 |

      • Pop dominates with more than three times the listens of the next genre. Understanding whether fans of particular genres churn at different rates could uncover new retention levers.

5. Final DataFrame prep  
   - Isolated numeric predictors with no nulls  
   - Scaled features and flagged high-risk segments (e.g., low-engagement, free-trial users)  
   - Produced a feature-correlation heatmap against churn

## Output  
- A clean, feature-rich Pandas DataFrame primed for machine learning  
- A Jupyter notebook showcasing EDA visualizations 
- A concise slide deck summarizing top churn drivers and recommended next steps for modeling

## Design Principles  
- Alignment & Proximity: Grouped related metrics (engagement vs. tenure) for intuitive comparison  
- Enclosure: Used distinct chart backgrounds to separate analyses before and after table join  
- Colour & Hue: Applied a diverging palette to highlight positive vs. negative churn correlations