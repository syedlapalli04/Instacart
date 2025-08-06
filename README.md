# Instacart User Segmentation (Notebook: instacart_user_segmentation_trans.ipynb)

This project analyzes Instacart user purchase behavior and segments users based on their order patterns using clustering techniques.

## Data Source
- obtained from kaggle: https://www.kaggle.com/datasets/yasserh/instacart-online-grocery-basket-analysis-dataset/data
- `aisles.csv`, `departments.csv`, `products.csv`: Product metadata
- `orders.csv`: User order history
- `order_products__prior.csv`, `order_products__train.csv`: Products in each order

## Analysis Workflow

1. **Data Loading & Feature Engineering**
   - Load all Instacart data files.
   - For each user, compute:
     - Total number of orders (`total_orders`)
     - Average lag (in days) between orders (`avg_days_between_orders`)
     - Average order size in products (`avg_order_size`)

2. **Exploratory Data Analysis**
   - Visualize distributions of total orders, average days between orders, and average order size using histograms.

3. **Feature Transformation**
   - Apply log and Box-Cox transformations to reduce skewness in `total_orders` and `avg_order_size`.
   - Visualize transformed features to assess distribution.

4. **Clustering**
   - Standardize features for clustering.
   - Use the elbow method to determine the optimal number of clusters.
   - Apply K-Means clustering (k=3 based on elbow plot).
   - Assign cluster labels to each user.

5. **Visualization & Interpretation**
   - Visualize clusters using PCA-reduced 2D scatter plots.
   - Create a "snake plot" (seaborn pointplot) to compare average feature values across clusters.
   - Summarize and interpret each cluster:
     - Cluster 0: Many, medium-sized purchases (loyal customers)
     - Cluster 1: Few, small purchases (infrequent/specific shoppers)
     - Cluster 2: Few, medium-sized purchases (moderate shoppers)

6. **(Optional) Further Analysis**
   - Consider silhouette score for cluster validation.
   - Suggest business actions for each segment.

## Requirements
- Python 3.x
- pandas, numpy, matplotlib, seaborn, scikit-learn, scipy

## How to Run
1. Place all Instacart CSV files in a `data/` directory.
2. Open `instacart_user_segmentation_trans.ipynb` in Jupyter or VS Code.
3. Run cells sequentially to reproduce the analysis and visualizations.

## Notes
- Feature transformations (log, Box-Cox) are used to address skewness in user behavior data.
- Clustering is performed on transformed and standardized features for best results.