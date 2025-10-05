# Assignment: CSCA 5632 Unsupervised Algorithms for Customer Segmentation and Recommendation Systems

## Introduction

E-commerce businesses generate vast amounts of transaction data, but extracting meaningful insights from this data remains challenging. Key business goals include understanding customer behavior, providing personalized product recommendations, and predicting future purchases. Addressing these challenges can improve marketing effectiveness, increase customer retention, and boost sales.

In this assignment, I focus on applying unsupervised machine learning techniques to analyze real-world e-commerce data. The main objectives are:

1. Customer segmentation to identify distinct groups of customers based on their purchasing behavior.  
2. Product recommendation to suggest relevant items to customers to enhance cross-selling and upselling opportunities.  

By exploring these patterns, I aim to demonstrate how data-driven insights can inform better business decisions in online retail.

---

## Dataset Description

- Dataset: UCI Online Retail Dataset  
- Source: https://archive.ics.uci.edu/dataset/352/online+retail  
- Business Context: Transactions from a UK-based online retailer specializing in gifts, including both individual and wholesale customers.  
- Timeframe: December 2010 – December 2011  
- Size: 541,909 transactions, 8 attributes  
- Customers: 4,312 unique customers after cleaning  
- Products: 4,444 unique products  

This dataset provides a realistic snapshot of e-commerce operations, capturing diverse purchasing behaviors across a range of products.

---

## Problem Definition

E-commerce businesses collect large volumes of transaction data, but turning this data into actionable insights is not straightforward. Two key challenges are particularly important: understanding different customer groups and making personalized product recommendations.

Without effective segmentation, marketing campaigns tend to be generic, leading to low engagement and wasted advertising budgets. Similarly, poor recommendation systems can result in missed cross-selling opportunities, fewer repeat purchases, and higher customer churn.

In this project, I aim to use unsupervised learning methods, such as clustering based on purchase history and customer behavior, to identify meaningful customer segments. I expect that understanding these segments will help deliver better recommendations, improve customer lifetime value, reduce churn, and increase sales.

---

## Why I Chose This Dataset

I chose this dataset because it represents real-world e-commerce data, rather than a simplified or synthetic dataset. This means it includes imperfections, inconsistencies, and missing values, which provide an opportunity to practice data cleaning, transformation, and exploratory analysis in a realistic context.

Its richness and complexity make it well-suited for unsupervised learning techniques such as clustering, dimensionality reduction, collaborative filtering, and matrix factorization. These methods can uncover hidden patterns in customer behavior, purchasing preferences, and product relationships. Working with this dataset allows me to extract practical insights that closely mirror real business scenarios and challenges.

---

## Data Processing

The raw data required extensive cleaning:

- Removed cancelled orders (invoices starting with 'C')  
- Filtered out negative quantities and prices  
- Dropped missing customer IDs  
- Removed duplicates  
- Final dataset retained ~75% of original data  

---

## Methods Used

### Customer Segmentation

- RFM Analysis: Analyzed Recency, Frequency, and Monetary value  
- PCA: Reduced dimensionality to 2 components (explained 78% variance)  
- Clustering: Applied K-Means and Agglomerative clustering  
- Results: Identified 3 optimal clusters representing high-value, medium-value, and low-value customers  

### Recommendation System

- Collaborative Filtering: Implemented both user-based and item-based approaches  
- Challenge: 98.5% data sparsity made recommendations difficult  
- Performance: User-based CF (RMSE: 2.02) outperformed item-based CF (RMSE: 19.83)  

### Sales Forecasting

- NMF: Applied Non-negative Matrix Factorization on customer-product-time tensor  
- Approach: Used linear forecasting on latent factors  
- Hyperparameter Tuning: Tested 5-40 components, chose 20 for balance  

---

## Key Findings

1. Customer Segments:  
   - High-value customers: Recent purchases, high frequency, high spending  
   - Medium-value customers: Moderate activity across all dimensions  
   - Low-value customers: Infrequent purchases, low spending  

2. Algorithm Performance:  
   - Agglomerative clustering (silhouette score: 0.41) slightly better than K-Means (0.39)  
   - User-based collaborative filtering much more effective than item-based  

3. Data Quality: Real-world e-commerce data is messy; extensive cleaning was crucial  

---

## Technologies Used

- Python  
- pandas, numpy for data processing  
- scikit-learn for machine learning  
- matplotlib, seaborn for visualization  
- Jupyter Notebook for analysis  

---

## File Structure

- `main.ipynb` - Complete analysis notebook with all code and results, including data loading, cleaning, exploratory analysis, clustering, recommendations, and forecasting  

---

## What I Learned

Working with real-world data revealed several challenges:

- Data preprocessing is critical and often more complex than expected  
- Different clustering algorithms can uncover different customer patterns  
- Visualization is essential for understanding algorithm behavior  
- Handling high sparsity in recommendation systems is a major challenge  

---

## Next Steps

- Explore tensor factorization techniques for improved forecasting  
- Try different similarity metrics for collaborative filtering  
- Experiment with hybrid recommendation approaches  
- Optimize threshold selection for NMF predictions  

---

## Reference

- Based on the NMF forecasting approach from: https://www.jstage.jst.go.jp/article/ipsjjip/27/0/27_752/_pdf
