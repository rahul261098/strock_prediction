# strock_prediction
#Stroke_Prediction_Analysis
Project Overview
This project aims to develop and evaluate machine learning models for predicting stroke based on various health-related attributes. The goal is to identify individuals at high risk of stroke, which can aid in early intervention and preventive strategies. This analysis covers data loading, preprocessing, model training, hyperparameter tuning, and performance evaluation of several classification algorithms.

Dataset
The dataset used for this analysis is the 'Healthcare Dataset Stroke Data', which contains information about patients including gender, age, presence of hypertension, heart disease, marital status, work type, residence type, average glucose level, BMI, smoking status, and stroke history.

Key Steps and Methodologies
Data Loading and Initial Exploration: The dataset was loaded using pandas, and an initial inspection was performed to understand its structure and identify missing values.

Data Preprocessing and Cleaning:

Missing Values: Missing values in the 'bmi' column were imputed using the median value of the column.
Categorical Encoding: Categorical features (gender, ever_married, work_type, Residence_type, smoking_status) were converted into numerical representations using LabelEncoder.
Feature Scaling: Numerical features were scaled using StandardScaler to normalize their ranges, which is crucial for models sensitive to feature scales.
Data Splitting: The dataset was split into training (80%) and testing (20%) sets to evaluate model performance on unseen data.

Model Training and Evaluation: We trained and evaluated three different machine learning classification models:

RandomForestClassifier:

Initially, the RandomForest model struggled with predicting the minority class (stroke) due to severe class imbalance.
Hyperparameter Tuning: GridSearchCV was employed to find the optimal hyperparameters for the RandomForest model. Crucially, class_weight='balanced' was used during tuning to address the class imbalance, giving more importance to the minority class during training.
Evaluation: After balancing, the model showed improved recall for the stroke class, demonstrating its ability to detect these rare events.
Logistic Regression:

A linear model that provides probability estimates.
Evaluation: This model consistently showed strong performance, achieving the highest ROC AUC score.
XGBoost Classifier:

A powerful gradient boosting algorithm known for its performance.
Evaluation: Performed well in terms of accuracy, though its ROC AUC was slightly lower than Logistic Regression and the balanced RandomForest.
Model Comparison: All models were compared based on accuracy, ROC AUC score, classification reports (precision, recall, f1-score), and confusion matrices. ROC curves were plotted to visually compare their discriminatory power.

Feature Importance Analysis: For the best-performing model (Logistic Regression), feature importances were derived from the absolute values of its coefficients. This helped identify which features have the most significant impact on stroke prediction.

Key Findings
Class Imbalance: The dataset exhibited significant class imbalance, with a very small percentage of stroke cases. Addressing this with class_weight='balanced' was crucial for the RandomForest model to effectively predict strokes.
Model Performance:
Logistic Regression emerged as the top performer with an ROC AUC of 0.8514 and an accuracy of 93.93%.
The Balanced RandomForest Model significantly improved its ability to detect stroke cases, achieving a recall of 0.18 for the stroke class (up from 0.00) and an ROC AUC of 0.8433.
XGBoost showed an accuracy of 93.74% and an ROC AUC of 0.7964.
Feature Importance: Age was identified as the most significant predictor of stroke according to the Logistic Regression model, followed by avg_glucose_level and ever_married. Features like bmi and gender had comparatively less influence.
Conclusion
The analysis successfully developed and evaluated several models for stroke prediction. The Logistic Regression model demonstrated the best overall performance, while the hyperparameter-tuned and class-balanced RandomForest model proved effective in handling the imbalanced nature of the stroke data, making it a viable option when recall for the minority class is a priority. The insights from feature importance highlight the critical role of age and glucose levels in stroke risk assessment.
