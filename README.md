Title: California-Wildfire-Severity 

Student Name: Kritika Pantha 

Student ID: PA3221350

Abstract: Predicting and classifying California Wildfire Severity using Random Forest Model
Table Of Content:

Problem: Predicting magnitude of wildfire severity using: Area_Burned (Acres), Estimated_Financial_loss (Million $)
         Classification of severity class like low, medium, high and extreme.
         
Data Understanding: The data set that I used for this project is extracted from Kaggle website, 

                    url:  kaggle.com/datasets/vivekattri/california-wildfire-damage-2014-feb2025?select=California+Wildfire+Damage.csv 
                    
The data set contains 101 rows and 11 columns.
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

Data Preparation: 
First the data is loaded into pandas dataframe, then data is cleaned like standardizing clumn names to make it more consistent, then feature scaling, temporal features in Date Columns like Year, month, dayofyear, season and many more. Then used a severity classification label like low (<10,000), Medium (10,000–24,999), High (25,000–39,999) and Extreme (≥40,000). Then predicted the Area_Burned_Acres and Estimated_Financial_Loss_Million. Then, used a RF model for futher classification.

Modeling: Random Forest modelling is used for this project. Itcreates a large collection of decision trees and merges their outputs, allowing the model to deliver predictions that are more reliable and consistent than any single tree could provide.
rf_class = RandomForestClassifier(
    n_estimators=300, # creates 300 decision trees, more tree implies more stable predictions.
    max_depth=15, # Limits how deep each decision tree can grow, preventing overfitting.
    class_weight="balanced", # Automatically adjusts weights based on how many samples each severity class has, ensuring the model doesn’t favor the more common classes and treats all severity levels fairly.
    random_state=42 # Sets a fixed seed so the model produces the same results every time, ensuring full reproducibility of your experiments.
)


Evaluation: Area Burned, Fianancial Loss and Confusion mtrix-severity classification
Area Burned Prediction:
RMSE: 28140.754820335176
R²: -4.023705408619031
Financial Loss Prediction:
RMSE: 26518.393607799142
R²: -3.461152861357899

Confusion Matrix - Severity Classification

    precision    recall  f1-score   support

     Extreme       0.00      0.00      0.00         3
        High       0.12      0.17      0.14         6
         Low       0.00      0.00      0.00         3
      Medium       0.38      0.38      0.38         8

     accuracy                           0.20        20
    macro avg       0.12      0.14      0.13        20
 weighted avg       0.19      0.20      0.19        20

References:

Retrieved from 
kaggle.com/datasets/vivekattri/california-wildfire-damage-2014-feb2025?select=California+Wildfire+Damage.csv, 
on Sunday, 12/21/2025 at 3 pm.



















