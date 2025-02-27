# stroke_ml_prediction
Stroke Prediction Analysis
1. Introduction
1.1 Context
Stroke is one of the leading causes of death worldwide, responsible for approximately 11% of total deaths according to the World Health Organization (WHO). The ability to predict stroke occurrences using health and demographic factors can assist medical professionals in early diagnosis and preventive care.
1.2 Objective
The goal of this analysis is to build a predictive model that can determine whether a patient is at risk of stroke based on various features such as age, medical conditions, and lifestyle factors.
1.3 Dataset Overview
This dataset consists of patient health records, containing demographic details and medical history. The main attributes include:
id: Unique identifier for each patient.
gender: Male, Female, or Other.
age: Continuous numerical value.
hypertension: Binary variable (0 = No, 1 = Yes).
heart_disease: Binary variable (0 = No, 1 = Yes).
ever_married: Categorical (Yes/No).
work_type: Work classification (Private, Govt Job, Self-employed, Children, Never worked).
Residence_type: Categorical (Rural or Urban).
avg_glucose_level: Continuous value.
bmi: Continuous value representing Body Mass Index.
smoking_status: Categorical (Formerly smoked, Never smoked, Smokes, Unknown).
stroke: Target variable (1 = Stroke, 0 = No Stroke).
2. Exploratory Data Analysis (EDA)
2.1 Data Inspection
The dataset is loaded using Pandas, and an overview of the structure is obtained using .info() and .describe().
Missing values are checked and visualized using missingno.
2.2 Data Visualization
Several visualization techniques are applied:
Histograms & Boxplots: Used for age, BMI, and glucose level distributions.
Bar Plots: Compare stroke vs. no stroke cases.
Correlation Matrix: Determines relationships between features.
2.3 Insights from EDA
The dataset is highly imbalanced, with very few stroke cases.
Older individuals have a higher incidence of stroke.
Higher glucose levels and BMI are potential risk factors for stroke.
3. Data Preprocessing & Feature Engineering
3.1 Handling Missing Values
The BMI column contains missing values, which are handled using mean imputation with SimpleImputer.
3.2 Encoding Categorical Variables
One-hot encoding is applied to gender, work_type, Residence_type, and smoking_status.
Label encoding is applied where necessary.
3.3 Feature Scaling
Standardization (StandardScaler) is applied to age, avg_glucose_level, and bmi.
3.4 Addressing Imbalanced Data
SMOTE (Synthetic Minority Over-sampling Technique) is used to oversample the minority class (stroke=1).
4. Model Training & Evaluation
4.1 Train-Test Split
The dataset is split into 80% training and 20% testing using train_test_split().
4.2 Machine Learning Models
Several models are trained and evaluated:
4.2.1 Baseline Model: Dummy Classifier
A Dummy Classifier is used as a baseline to compare real model performance against random predictions.
4.2.2 Logistic Regression
A Logistic Regression model is trained and evaluated for binary classification.
4.2.3 Support Vector Machine (SVM)
An SVM classifier with an RBF kernel is used for improved decision boundary separation.
4.2.4 K-Nearest Neighbors (KNN)
KNN classifier is implemented with different values of K.
4.3 Cross-Validation
Stratified K-Fold Cross-Validation ensures that each fold maintains the proportion of stroke vs. no stroke cases.
RepeatedStratifiedKFold is used for additional model validation.
4.4 Performance Metric
Given the severe class imbalance in the dataset, AUC (Area Under the ROC Curve) is the primary evaluation metric, as it provides a balanced view of the model's ability to distinguish between classes.
5. Results & Discussion
5.1 Model Comparisons
Logistic Regression and SVM performed better than KNN in this dataset.
SMOTE significantly improved AUC, making stroke detection more reliable.
KNN struggled with high-dimensional data and imbalanced classes.
5.2 Key Takeaways
Age, glucose levels, and BMI are strong stroke predictors.
Class imbalance must be handled carefully to avoid biased models.
SVM and Logistic Regression showed the best performance for stroke prediction.
6. Conclusion & Future Work
6.1 Conclusion
This study successfully implemented multiple machine learning models to predict stroke occurrences using patient data. Handling imbalanced data was crucial for improving model effectiveness.
6.2 Future Improvements
Feature Engineering: Incorporate polynomial features or feature selection techniques.
Hyperparameter Tuning: Use GridSearchCV for optimizing model parameters.
Deep Learning: Experiment with Neural Networks for improved performance.
Additional Data: Collect more diverse datasets for better generalization.

