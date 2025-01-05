Evaluation metrics are crucial in assessing how well a machine learning model performs, especially on unseen data. Different metrics are used depending on the type of problem, such as regression, classification, or ranking. Here’s a breakdown of common evaluation metrics by task:

### 1. Classification Metrics

These are used when the target variable is categorical (e.g., binary or multi-class classification).

- **Accuracy**: The proportion of correct predictions out of all predictions. Useful for balanced datasets but less informative for imbalanced datasets.
    
- **Precision**: The proportion of true positive predictions out of all positive predictions (e.g., in binary classification, the proportion of correctly identified "positives" among all identified as positive).
    
- **Recall (Sensitivity)**: The proportion of true positive predictions out of all actual positive instances, indicating how well the model captures actual positives.
    
- **F1 Score**: The harmonic mean of precision and recall, providing a balance between the two, especially useful for imbalanced datasets.
    
- **AUC-ROC (Area Under the Receiver Operating Characteristic Curve)**: Measures the model's ability to distinguish between classes. AUC-ROC closer to 1 indicates better performance.
    
- **Confusion Matrix**: A table that shows the counts of true positives, false positives, true negatives, and false negatives, useful for understanding the types of errors the model makes.
    
- **Log Loss (Cross-Entropy Loss)**: Used in probabilistic classification, penalizing the model for confident but incorrect predictions. Lower values indicate better models.
    
- **Top-k Accuracy**: For multi-class classification, top-k accuracy checks if the true label is among the top k predictions made by the model.
    

### 2. Regression Metrics

These are used when the target variable is continuous.

- **Mean Absolute Error (MAE)**: The average absolute difference between predicted and actual values. MAE is easy to interpret but does not penalize large errors as strongly.
    
- **Mean Squared Error (MSE)**: The average squared difference between predicted and actual values. Squaring amplifies large errors, making MSE sensitive to outliers.
    
- **Root Mean Squared Error (RMSE)**: The square root of MSE, which brings the metric back to the original units of the target variable.
    
- **R² (Coefficient of Determination)**: Measures how well the model explains the variance in the target variable, with 1 indicating perfect prediction and values closer to 0 indicating poor performance.
    
- **Mean Absolute Percentage Error (MAPE)**: Represents the mean absolute error as a percentage, useful when comparing performance across datasets with different scales.
    

### 3. Ranking and Information Retrieval Metrics

These metrics are used for problems where the output is a ranked list (e.g., search engines, recommendation systems).

- **Mean Average Precision (MAP)**: The mean of the average precision scores for all queries in a dataset, often used for ranked retrieval tasks.
    
- **Mean Reciprocal Rank (MRR)**: Measures the average rank at which the first relevant item appears. Higher values indicate relevant items appearing earlier.
    
- **Discounted Cumulative Gain (DCG) / Normalized DCG (NDCG)**: Evaluates the relevance of ranked predictions, giving higher scores for relevant items appearing earlier in the ranking. NDCG is a normalized version, comparing DCG to the best possible score.
    

### 4. Clustering Metrics

These metrics assess the quality of clustering in unsupervised learning.

- **Silhouette Score**: Measures how similar an instance is to its own cluster compared to other clusters, with values closer to 1 indicating well-defined clusters.
    
- **Adjusted Rand Index (ARI)**: Compares the similarity between predicted and true cluster assignments, with adjustments for chance.
    
- **Homogeneity, Completeness, and V-Measure**: Homogeneity measures whether each cluster contains only members of a single class, completeness checks if all members of a given class are assigned to the same cluster, and V-measure is the harmonic mean of both.
    

### 5. Time Series Forecasting Metrics

These are used when evaluating time series predictions.

- **Mean Absolute Scaled Error (MASE)**: Compares forecast errors to those of a simple baseline model, helping evaluate the forecast’s effectiveness relative to a benchmark.
    
- **Symmetric Mean Absolute Percentage Error (sMAPE)**: A variant of MAPE, specifically adapted to time series, that treats over- and under-forecasts symmetrically.
    
- **Mean Squared Logarithmic Error (MSLE)**: Useful when dealing with data with exponential growth, as it penalizes large errors proportionally to the scale of the target values.
    

### Choosing Evaluation Metrics

The choice of metric depends on:

- **Problem Type**: Classification, regression, clustering, ranking, or time series forecasting.
- **Dataset Characteristics**: For imbalanced datasets, accuracy may be misleading, so metrics like F1-score, AUC-ROC, or precision/recall are often better.
- **Business Objectives**: The metric should align with business goals, such as optimizing for precision in fraud detection (to avoid false positives) or recall in medical diagnosis (to capture as many true cases as possible).

These metrics provide insights into different aspects of model performance and help in selecting, tuning, and evaluating models effectively.