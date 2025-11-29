# Customer Segmentation for Online Retail

This project applies RFM-based customer segmentation to an online retail dataset and builds data-driven insights for marketing and strategy. The work is organised into four phases, from data cleaning to scenario analysis.

## Project Goal

The main goal is to group customers into meaningful segments based on their purchasing behaviour (Recency, Frequency, Monetary) and use these segments to support business decisions, such as targeting, retention and campaign design.

## Data

- Source: Online retail transaction data (anonymised)
- Level: Transaction-level (one row per invoice line)
- Key fields: transactionno, date, productno, productname, quantity, price, customerno, country
- Main derived variable: `totalprice = quantity × price`

## Methodology Overview

The analysis is structured into four phases:

### Raw Data → Cleaning → RFM Model → K-Means Segmentation → Cluster KPIs → Behavioral Insights → Scenario Simulation


### Phase 1 – Data Preparation & RFM Construction (`01_Data_Preparation.ipynb`)
- Cleaned the raw transaction data (removed missing IDs, invalid quantities/prices, non-positive values).
- Standardised column names and converted types (dates, numeric fields).
- Created a customer-level RFM table:
  - **Recency**: days since last purchase
  - **Frequency**: number of unique transactions
  - **Monetary**: total spend per customer
- Explored distributions, correlations and outliers for the RFM variables.

### Phase 2 – Customer Segmentation Modeling (`02_Clustering_Modeling.ipynb`)
- Applied log-transformation and standard scaling to RFM features.
- Tested different values of *k* using the Elbow method and Silhouette scores.
- Selected a 4-cluster K-Means model.
- Assigned each customer to a cluster and visualised segments using PCA.
- Saved the final RFM table with cluster labels for later phases.

### Phase 3 – Cluster Insights & Behaviour (`03_Cluster_Insights_and_Recommendations.ipynb`)
- Computed cluster-level KPIs (average recency, frequency, monetary, revenue share, order value).
- Labeled clusters with business-friendly names.
- Ran ANOVA (also on log-transformed RFM values) to confirm that clusters differ significantly.
- Visualised RFM distributions and pairwise relationships by cluster.
- Interpreted the segments in terms of customer behaviour and value.

### Phase 4 – Strategic Analysis & Scenarios (`04_Advanced_Customer_Segmentation_and_Strategy.ipynb`)
- Merged transaction-level data with cluster labels.
- Analysed monthly revenue and active customers per segment.
- Compared cluster performance across top countries.
- Built classical RFM scores and compared them with K-Means clusters.
- Computed a simple CLV-style proxy at cluster level. (CLV=RecencyFrequency×Monetary​)
- Simulated marketing scenarios with different conversion rates to estimate potential revenue uplift.
- Finalised descriptive labels for each segment:
  - **Cluster 2** – High-Value Loyal Customers  
  - **Cluster 3** – Mid-Value Regular Buyers  
  - **Cluster 0** – Occasional / Low-Value Buyers  
  - **Cluster 1** – Inactive / At-Risk Customers
 
## Business Impact

The segmentation enables:

Prioritised marketing spend

Segment-specific messaging

Predictive budgeting using scenario results

CLV-oriented targeting strategies

Country-focused campaign design

Opportunity identification for upsell/retention

## Repository Structure
data/
│   online_retail_clean.csv
│   rfm_with_clusters.csv
│
notebooks/
│   01_Data_Preparation.ipynb
│   02_Clustering_Modeling.ipynb
│   03_Cluster_Insights_and_Recommendations.ipynb
│   04_Advanced_Customer_Segmentation_and_Strategy.ipynb
│

    Figures and exported tables




## Summary

The project establishes a full pipeline from raw transaction data to clustering, interpretation and actionable marketing strategy.
The final segmentation is statistically valid, business-friendly, and supported by behavioural analytics across time and geography.
These insights form a foundation for targeted campaigns, retention efforts, CLV estimation and portfolio optimisation.

