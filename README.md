# fraud-detection
🛠 Task 1: Data Analysis and Preprocessing
1. Data Cleaning
Missing Values: Identified and handled null values to ensure data integrity.

Duplicates: Removed redundant records to prevent model bias.

Data Types: Converted signup_time and purchase_time into datetime objects for feature extraction.

2. Geolocation Integration
IP Transformation: Converted IP addresses from string format to integer format for compatibility with the lookup table.

Range-Based Merge: Performed a merge_asof between Fraud_Data.csv and IpAddress_to_Country.csv.

Validation: Applied a boundary check to ensure the IP address fell strictly within the lower_bound and upper_bound for each country.

3. Feature Engineering
We created several high-impact features to capture fraudulent behavior:

time_since_signup: The duration between account creation and first purchase. (Short durations are high-risk).

hour_of_day & day_of_week: Captured temporal patterns of transactions.

device_id_count & ip_count: Calculated transaction velocity to identify bots reusing hardware/IPs.

4. Data Transformation
Scaling: Applied StandardScaler to numerical features (purchase_value, age, etc.) so that features with larger ranges do not dominate the model.

Encoding: Used One-Hot Encoding for categorical variables including source, browser, sex, and country.

5. Handling Class Imbalance (SMOTE)
The initial dataset was highly imbalanced (~9% fraud).

Before SMOTE: 109,568 Legitimate | 11,321 Fraud

After SMOTE: 109,568 Legitimate | 109,568 Fraud

Justification: We chose SMOTE (Synthetic Minority Over-sampling Technique) over undersampling to avoid losing valuable information from the 100k+ legitimate transactions. SMOTE creates synthetic examples rather than duplicates, helping the model generalize better to unseen fraud patterns.