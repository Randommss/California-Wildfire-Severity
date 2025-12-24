California Wildfire Severity Prediction with Machine Learning
---

Student Name: Kritika Pantha
Student ID: PA3221350

---

Abstract: Predicting and classifying California Wildfire Severity using Random Forest Model

---

Table of Content

Problem
Data Understanding
Data Preparation
Modeling
Evaluation
References

---

Problem

California experiences frequent and increasingly severe wildfires that cause large-scale environmental damage, economic loss, and human casualties.
1. Predicting magnitude of wildfire severity using: Area_Burned (Acres) and Estimated_Financial_loss (Million $)
2. Classification of severity class like low, medium, high and extreme.
         
---

Challenges to Overcome

- **Small dataset size:** Only 101 wildfire records
- **Highly skewed target variables:** Area burned and financial loss vary significantly
- **Class imbalance:** Extreme wildfire events are rare
- **Non-linear relationships:** Severity depends on multiple interacting factors
- **Temporal patterns:** Seasonal and yearly variations in wildfire occurrence
- **Mixed feature types:** Numerical, categorical, and temporal variables

---

Data Understanding

The data set that I used for this project is extracted from Kaggle website.

url:  kaggle.com/datasets/vivekattri/california-wildfire-damage-2014-feb2025?select=California+Wildfire+Damage.csv 
                    
The data set contains 101 rows and 11 columns.

Incident_ID: The unique ID of the particular incident
Date: The calendar date on which the wildfire occurred or was reported.
Location: The county or region where the wildfire took place.
Area_Burnt: Total land area burned by the wildfire, measured in acres.
Homes_Destroyed: Number of residential homes completely destroyed by the fire.
Businesses_Destroyed: Number of commercial buildings lost due to the wildfire.
Vehicles_Damaged: Count of vehicles damaged or destroyed during the incident.
Injuries: Number of people injured as a result of the wildfire.
Fatalities: Number of deaths caused by the wildfire.
Estimated_Financial_Loss (Million $): Total estimated economic loss caused by the wildfire, expressed in millions of dollars.
Cause: The identified or suspected cause of the wildfire (e.g., Lightning, Human Activity, Unknown).

---

Data Preparation

- Loaded data into a Pandas DataFrame
- Standardized column names for consistency
- Extracted temporal features from the `Date` column:
- `year`, `month`, `day_of_year`, `season`
- Performed feature scaling for numerical stability
- Created wildfire **severity labels** based on area burned:
- **Low:** &lt; 10,000 acres
- **Medium:** 10,000 – 24,999 acres
- **High:** 25,000 – 39,999 acres
- **Extreme:** ≥ 40,000 acres
- Prepared datasets for:
- **Regression:** Area burned and financial loss
- **Classification:** Wildfire severity class

---

Modeling

Random Forest modelling is used for this project. Itcreates a large collection of decision trees and merges their outputs, allowing the model to deliver predictions that are more reliable and consistent than any single tree could provide.
rf_class = RandomForestClassifier(
    n_estimators=300, # creates 300 decision trees, more tree implies more stable predictions.
    max_depth=15, # Limits how deep each decision tree can grow, preventing overfitting.
    class_weight="balanced", # Automatically adjusts weights based on how many samples each severity class has, ensuring the model doesn’t favor the more common classes and treats all severity levels fairly.
    random_state=42 # Sets a fixed seed so the model produces the same results every time, ensuring full reproducibility of your experiments.
)

---

Evaluation

### Area Burned Prediction (Regression)

- **RMSE:** 28,140.75
- **R²:** -4.02

### Financial Loss Prediction (Regression)

- **RMSE:** 26,518.39
- **R²:** -3.46

---

Confusion Matrix - Severity Classification

    precision    recall  f1-score   support

     Extreme       0.00      0.00      0.00         3
        High       0.12      0.17      0.14         6
         Low       0.00      0.00      0.00         3
      Medium       0.38      0.38      0.38         8

     accuracy                           0.20        20
    macro avg       0.12      0.14      0.13        20
 weighted avg       0.19      0.20      0.19        20

Reference:

Retrieved from 
kaggle.com/datasets/vivekattri/california-wildfire-damage-2014-feb2025?select=California+Wildfire+Damage.csv, 
on Sunday, 12/21/2025 at 3 pm.



















