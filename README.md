# Stroke Prediction Analysis - Comprehensive Report

## 1. Introduction

### 1.1 Context
Stroke is one of the leading causes of death worldwide, responsible for approximately **11% of total deaths** according to the **World Health Organization (WHO)**. Predicting stroke occurrences using health and demographic factors can assist medical professionals in **early diagnosis** and **preventive care**.

### 1.2 Objective
The goal of this analysis is to build a **predictive model** that determines whether a patient is at risk of stroke based on factors like **age, medical conditions, and lifestyle choices**.

### 1.3 Dataset Overview
The dataset consists of patient health records with the following key features:

- **`id`**: Unique identifier for each patient.
- **`gender`**: Male, Female, or Other.
- **`age`**: Patient’s age (numerical).
- **`hypertension`**: 0 = No, 1 = Yes.
- **`heart_disease`**: 0 = No, 1 = Yes.
- **`ever_married`**: Yes/No.
- **`work_type`**: Private, Govt Job, Self-employed, Children, Never worked.
- **`Residence_type`**: Rural or Urban.
- **`avg_glucose_level`**: Average glucose level.
- **`bmi`**: Body Mass Index.
- **`smoking_status`**: Formerly smoked, Never smoked, Smokes, Unknown.
- **`stroke`** (Target variable): 1 = Stroke, 0 = No Stroke.

---

## 2. Exploratory Data Analysis (EDA)

### 2.1 Data Inspection
- Data is loaded using **Pandas**.
- Overview using `.info()` and `.describe()`.
- Missing values checked using **`missingno`**.

### 2.2 Data Visualization
- **Histograms & Boxplots**: Age, BMI, and glucose level distributions.
- **Bar Plots**: Stroke vs. No Stroke cases.
- **Correlation Matrix**: Relationship between features.

### 2.3 Key Findings
- Older individuals have a higher stroke risk.  
- Higher glucose levels & BMI are strong predictors.  
- Dataset is highly imbalanced with very few stroke cases.  

---

## 3. Data Preprocessing & Feature Engineering

### 3.1 Handling Missing Values
- BMI missing values are handled using **mean imputation** (`SimpleImputer`).

### 3.2 Encoding Categorical Variables
- **One-hot encoding** applied to `gender`, `work_type`, `Residence_type`, and `smoking_status`.
- **Label encoding** used where necessary.

### 3.3 Feature Scaling
- Standardized (`StandardScaler`) **age, avg_glucose_level, and BMI**.

### 3.4 Addressing Class Imbalance
- **SMOTE (Synthetic Minority Over-sampling Technique)** used to balance `stroke=1`.

---

## 4. Model Training & Evaluation

### 4.1 Train-Test Split
- **80% Training / 20% Testing** using `train_test_split()`.

### 4.2 Machine Learning Models
#### Baseline Model: Dummy Classifier
- Used to compare performance against random predictions.

#### Logistic Regression
- Used for binary classification.

#### Support Vector Machine (SVM)
- Trained with **RBF kernel** for better decision boundaries.

#### K-Nearest Neighbors (KNN)
- Evaluated with different values of **K**.

### 4.3 Cross-Validation
- **Stratified K-Fold Cross-Validation** ensures balanced training.
- **RepeatedStratifiedKFold** improves generalization.

### 4.4 Performance Metric
> **Given severe class imbalance, AUC (Area Under the ROC Curve) is the primary evaluation metric.**  
> It provides a balanced view of how well the model distinguishes between stroke and non-stroke cases.

---

## 5. Results & Discussion

### 5.1 Model Comparisons
- Logistic Regression and SVM performed best.  
- SMOTE significantly improved AUC, making stroke detection more reliable.  
- KNN struggled with high-dimensional imbalanced data.  

### 5.2 Key Takeaways
- Age, glucose levels, and BMI are top stroke predictors.  
- Class imbalance must be carefully handled to avoid biased predictions.  
- SVM and Logistic Regression performed best.  

---

## 6. Conclusion & Future Work

### 6.1 Conclusion
This study successfully implemented **multiple machine learning models** to predict stroke occurrences using patient data. **Handling imbalanced data** was crucial for improving predictions.

### 6.2 Future Improvements
- **Feature Engineering**: Try polynomial features or feature selection techniques.  
- **Hyperparameter Tuning**: Use `GridSearchCV` to optimize models.  
- **Deep Learning**: Experiment with **Neural Networks** for better accuracy.  
- **Collect More Data**: More diverse datasets could improve generalization.

---
