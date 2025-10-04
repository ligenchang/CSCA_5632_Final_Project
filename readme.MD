# E-Commerce Customer Analytics & Prediction

## Project Overview
E-commerce businesses face three major challenges:

1. **Segmentation**: Identifying meaningful customer groups from complex transaction data  
2. **Recommendations**: Delivering personalized cross-sell/upsell suggestions  
3. **Prediction**: Accurately forecasting future purchases for marketing and inventory planning  

This project addresses these challenges using multiple unsupervised machine learning approaches:

- Customer segmentation with **RFM analysis + clustering**  
- Personalized recommendations via **collaborative filtering**  
- Purchase prediction using **Non-negative Matrix Factorization (NMF) + temporal modeling**

---

## Dataset

- **Source**: UCI Online Retail Dataset  
- **Business Context**: UK-based gift retailer specializing in unique all-occasion gifts  
- **Time Period**: December 2010 - December 2011  

**Dataset Statistics**

| Metric | Value |
|--------|-------|
| Original Transactions | 541,909 |
| After Cleaning | 417,364 (23.7% reduction) |
| Customers | 4,268 unique |
| Products | 4,444 distinct |
| Key Attributes | InvoiceNo, StockCode, Description, Quantity, InvoiceDate, UnitPrice, CustomerID, Country |

**Data Quality Improvements**

- Removed cancellations and invalid transactions  
- Handled missing CustomerIDs  
- Outlier treatment (removed top 1% monetary extremes)  
- Log transformation for skewed features  
- StandardScaler normalization  

---

## Methodology

### 1. Data Processing Pipeline
**RFM Feature Engineering**

- **Recency**: Days since last purchase  
- **Frequency**: Number of transactions per customer  
- **Monetary**: Total spending per customer  

**Transformations**

- Log transformation  
- StandardScaler normalization  

**Dimensionality Reduction**

- PCA (3D → 2D, 89.6% variance retained)  

### 2. Customer Segmentation
**Algorithms Tested**

| Algorithm | Params | Silhouette Score |
|-----------|--------|-----------------|
| K-Means | k=3 | 0.390 |
| Hierarchical | Ward linkage | 0.410 |

**Customer Segments Identified**

- **Occasional Customers : Moderate purchasing behavior  
- **High-Value Loyal : Frequent, high-spending customers  
- **Inactive/At-Risk : Low engagement, low purchasing

### 3. Recommendation System
**Collaborative Filtering Approaches**

- **User-Based CF**: Find similar customers using cosine similarity  
- **Item-Based CF**: Recommend products similar to purchased items  

**Benefits**

- Handles sparse customer-product matrices effectively  
- Generates personalized recommendations for cross-sell/upsell  

### 4. Purchase Prediction
**NMF-Based Forecasting**

- Construct **3D tensor** (products × customers × months)  
- **NMF decomposition** with 15 latent factors  
- **Linear trend forecasting** of latent factors  
- Binary purchase prediction with threshold application  

---

## Results

### Customer Segmentation Performance

| Algorithm | Silhouette Score | Cluster Distribution | Strengths |
|-----------|-----------------|-------------------|-----------|
| K-Means | 0.390 | 21.8% / 36.8% / 41.4% | Fast, balanced clusters |
| Hierarchical | 0.410 | 48.9% / 25.7% / 25.4% | Reveals relationships |

**Business Impact**

- 1,085 at-risk customers identified for re-engagement campaigns  
- 1,097 high-value customers for premium retention strategies  
- Personalized recommendations enable targeted cross-sell/upsell  
- Predictive insights support proactive inventory and marketing planning  

---

## Key Takeaways

1. **Customer segmentation drives targeted action**  
   - 25.4% of customers are at churn risk and need immediate re-engagement  
   - 25.7% are high-value loyal customers requiring premium treatment  

2. **Collaborative filtering enables personalized recommendations**  
   - Dual approach system generates targeted product suggestions using both customer similarity and item relationships  

3. **Predictive modeling transforms business planning**  
   - NMF forecasting predicts future purchase probabilities, enabling proactive inventory management and revenue planning
