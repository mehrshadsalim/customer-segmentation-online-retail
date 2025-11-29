# Customer Segmentation for Online Retail  
A full analytical pipeline for behaviour-based customer segmentation using RFM modelling, K-Means clustering and strategic scenario analysis.  
The project is structured end-to-end from raw data cleaning to business-oriented insights.

---

## 1. Project Overview
This project applies a data-driven segmentation approach to an online retail dataset to understand customer behaviour, identify high-value groups, and inform marketing strategy.  
The workflow builds a complete pipeline:

**Raw Data → Cleaning → RFM → K-Means → Cluster Profiling → Behavioural Analysis → Strategic Scenarios**

---

## 2. Objectives
- Construct a robust RFM (Recency, Frequency, Monetary) model  
- Apply clustering to segment customers into meaningful behavioural groups  
- Validate cluster separation using statistical tests  
- Analyse segment behaviour over time and across countries  
- Compare classical RFM scoring with machine-learning segmentation  
- Build CLV-oriented performance indicators  
- Run scenario-based revenue simulations for marketing decisions  

---

## 3. Dataset
- **Source:** anonymised online retail transaction history  
- **Granularity:** one row per invoice line  
- **Key fields:**  
  `transactionno`, `date`, `productno`, `productname`, `quantity`, `price`,  
  `customerno`, `country`  
- **Derived variables:**  
  `totalprice = quantity × price` 

---

## 4. Methodology

### Phase 1 – Data Preparation & RFM Construction  
Notebook: [`01_Data_Preparation.ipynb`](notebooks/01_Data_Preparation.ipynb)  
- Cleaned invalid rows (missing customer IDs, negative quantities/prices)  
- Standardised column names and data types  
- Computed customer-level **RFM metrics**  
  - Recency = days since last purchase  
  - Frequency = number of transactions  
  - Monetary = total spend  
- Performed exploratory analysis on distribution, skewness, outliers  

---

### Phase 2 – Customer Segmentation Modelling  
Notebook: [`notebooks/02_Clustering_Modeling-fixed.ipynb`](notebooks/02_Clustering_Modeling-fixed.ipynb)  
- Applied log transformation + StandardScaler  
- Used **Elbow** and **Silhouette** criteria to evaluate cluster counts  
- Selected **K-Means (k=4)**  
- Visualised segment structure using PCA (2D space)  
- Exported final dataset: `rfm_with_clusters.csv`  

---

### Phase 3 – Cluster Insights & Behaviour  
Notebook: [`03_Customer_Cluster_Profiling_and_Insights.ipynb`](03_Customer_Cluster_Profiling_and_Insights.ipynb)  
- Computed cluster-level KPIs  
  - avg recency, avg frequency, avg monetary  
  - revenue share  
  - avg order value  
- Assigned business-friendly labels  
- Conducted **ANOVA** (raw + log-transformed) to confirm statistical separation  
- Visualised RFM distributions and pairwise relationships  
- Interpreted segment roles and value contribution  

---

### Phase 4 – Strategic Analysis & Scenario Simulation  
Notebook: [`04_Advanced_Customer_Segmentation_and_Strategy1.ipynb`](04_Advanced_Customer_Segmentation_and_Strategy1.ipynb)  
- Merged transactions with cluster labels  
- Analysed monthly revenue + active customers per segment  
- Performed country-level revenue decomposition for top markets  
- Built classical RFM score and compared with machine-learning clusters  
- Computed **CLV-style proxy:**  
  \[
  CLV \approx \frac{\text{Frequency} \times \text{Monetary}}{\text{Recency}}
  \]
- Simulated three marketing scenarios (1%, 5%, 10% conversion)  
- Identified highest-impact groups for targeted campaigns  

---

## 5. Final Segment Labels
| Cluster | Segment Name                       | Description |
|---------|-------------------------------------|-------------|
| **2**   | High-Value Loyal Customers          | Recent, frequent and high-spending; core value contributors |
| **3**   | Mid-Value Regular Buyers            | Stable activity, moderate spending; revenue backbone |
| **0**   | Occasional / Low-Value Buyers       | Low frequency and value; growth potential |
| **1**   | Inactive / At-Risk Customers        | Long recency periods, weak spend; win-back candidates |

---

## 6. Business Impact
The segmentation provides a practical foundation for:  
- Targeted and personalised marketing  
- Budget prioritisation toward high-value groups  
- CLV-oriented customer lifecycle management  
- Retention and upsell strategies  
- Country-specific campaign design  
- Revenue opportunity modelling under multiple scenarios  

---

## 7. Repository Structure
```
project/
│
├── data/
│   ├── online_retail_clean.csv
│   └── rfm_with_clusters.csv
│
├── notebooks/
│   ├── 01_Data_Preparation.ipynb
│   ├── 02_Clustering_Modeling.ipynb
│   ├── 03_Cluster_Insights_and_Recommendations.ipynb
│   └── 04_Advanced_Customer_Segmentation_and_Strategy.ipynb
│
└── reports/
    └── figures, tables and derived outputs
```

---

## 8. Summary
This project delivers an academically rigorous and industry-oriented customer segmentation framework.  
The results demonstrate that the K-Means model produces clear, statistically valid segments that align with business intuition and classical RFM scoring.  
The combined behavioural, geographic and scenario-based analyses provide actionable insights for targeted marketing, CLV estimation and commercial strategy development.

