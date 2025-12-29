Task 3 Report: Model Explainability & Business Insights
Project: E-commerce Fraud Detection for Adey Innovations Inc.

1. Feature Importance Comparison
Built-in Importance: The XGBoost model identified num__device_id_count as the most critical feature, followed by num__day_of_week and cat__country_United States.

SHAP Global Importance: The SHAP Summary Plot confirmed that num__device_id_count has the highest impact on model output, but also highlighted that very low num__time_since_signup values (represented by the blue dots pushing right) are significant fraud drivers.

2. Key Fraud Drivers (Top 5)
Device ID Count: High counts (multiple users on one device) are the strongest predictors of fraud.

Time Since Signup: Transactions occurring almost immediately after account creation are highly likely to be fraudulent.

Country (United States): Transactions originating from the US show a distinct influence on the model’s risk scoring in this dataset.

Day of Week: Transaction patterns vary by day, with certain days showing higher risk concentrations.

Purchase Value: Outlier transaction amounts (very high or very low) contribute to the model's decision-making.

3. Prediction Explanations (Local Interpretability)
True Positive Example: In the force plot, we observed that cat__country_Unknown and low time_since_signup pushed the prediction towards fraud (f(x) = 1.47).

False Positive Example: A legitimate transaction was flagged primarily because it originated from the United States, even though other features like device_id_count were normal.

4. Actionable Business Recommendations
MFA for New Accounts: Implement mandatory Multi-Factor Authentication (MFA) for any transaction occurring within the first 24 hours of account creation.

Device Fingerprinting: Flag any device_id associated with 3 or more unique user accounts for manual review by the fraud team.

Adaptive Geolocation Scoring: Increase the fraud-scoring threshold for transactions originating from high-risk countries or "Unknown" locations identified in the SHAP analysis.