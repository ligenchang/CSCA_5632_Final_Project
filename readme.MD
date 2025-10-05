# Customer Segmentation and Recommendation Systems

This is my coursework project for CSCA 5632 Unsupervised Algorithms. I applied unsupervised machine learning techniques to analyze e-commerce data and build customer insights.

## Project Overview

The project focuses on three main areas:
- Customer segmentation using clustering algorithms
- Product recommendation using collaborative filtering
- Sales forecasting using matrix factorization

## Dataset

I used the UCI Online Retail Dataset which contains transactions from a UK-based online retailer specializing in gifts.

- **Source**: https://archive.ics.uci.edu/dataset/352/online+retail
- **Time period**: December 2010 - December 2011
- **Size**: 541,909 transactions with 8 attributes
- **Customers**: 4,312 unique customers after cleaning
- **Products**: 4,444 unique products

## Data Processing

The raw data required extensive cleaning:
- Removed cancelled orders (invoices starting with 'C')
- Filtered out negative quantities and prices
- Dropped missing customer IDs
- Removed duplicates
- Final dataset: ~75% of original data retained

## Methods Used

### Customer Segmentation
- **RFM Analysis**: Analyzed Recency, Frequency, and Monetary value
- **PCA**: Reduced dimensionality to 2 components (explained 78% variance)
- **Clustering**: Applied both K-Means and Agglomerative clustering
- **Results**: Found 3 optimal clusters representing high-value, medium-value, and low-value customers

### Recommendation System
- **Collaborative Filtering**: Implemented both user-based and item-based approaches
- **Challenge**: 98.5% data sparsity made recommendations difficult
- **Performance**: User-based CF (RMSE: 2.02) outperformed item-based CF (RMSE: 19.83)

### Sales Forecasting
- **NMF**: Applied Non-negative Matrix Factorization on customer-product-time tensor
- **Approach**: Used linear forecasting on latent factors
- **Hyperparameter tuning**: Tested 5-40 components, chose 20 for balance

## Key Findings

1. **Customer Segments**: Three clear groups emerged
   - High-value customers: Recent purchases, high frequency, high spending
   - Medium-value customers: Moderate activity across all dimensions
   - Low-value customers: Infrequent purchases, low spending

2. **Algorithm Performance**:
   - Agglomerative clustering (silhouette score: 0.41) slightly better than K-Means (0.39)
   - User-based collaborative filtering much more effective than item-based

3. **Data Quality**: Real-world e-commerce data is messy - extensive cleaning was crucial

## Technologies Used

- Python
- pandas, numpy for data processing
- scikit-learn for machine learning
- matplotlib, seaborn for visualization
- Jupyter Notebook for analysis

## Files Structure

- `main.ipynb` - Complete analysis notebook with all code and results
- Contains data loading, cleaning, EDA, clustering, recommendations, and forecasting

## What I Learned

The real word data is quite messy. The biggest challenge was handling the high sparsity in the recommendation system. I learned that:
- Data preprocessing is more important than I initially thought
- Different clustering algorithms can reveal different patterns
- Visualization is crucial for understanding algorithm behavior
- Real-world datasets require lots of cleaning before analysis

## Next Steps

- Explore tensor factorization techniques for better forecasting
- Try different similarity metrics for collaborative filtering
- Experiment with hybrid recommendation approaches
- Optimize threshold selection for NMF predictions

## Reference

Based on the NMF forecasting approach from: https://www.jstage.jst.go.jp/article/ipsjjip/27/0/27_752/_pdf