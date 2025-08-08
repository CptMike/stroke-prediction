# Stroke Prediction: Machine Learning Report

## 1. Introduction
This project aims to predict the likelihood of a stroke based on a patient's data.

The project contains 4 categories
1. Import Data
2. EDA
3. Feature Engineering
4. Model Training

Each category contains sub-categories to keep the code clean.
(encodings, different models etc.)

## 2. Dataset Overview
The dataset contains over 5000 of unique patients with features such as 
gender,	age, hypertension, heart_disease, ever_married, work_type, Residence_type,	avg_glucose_level, bmi, smoking_status and stroke status.

## 3. Exploratory Data Analysis (EDA)
After plotting and checking the different values for each column, 3 things were decided:
1. Residence type has almost the same number of rows and stroke percentage. So the column will not be needed.
2. There were 2 cases of children having a stroke. This is a rare medical disease. They will be considered outliers and therefore removed from the dataset.
3. There is one instance of the gender "Other" among 5000.  This will be considered outliers and therefore removed from the dataset.

## 4. Feature Engineering
1.Removing the Residence_type column
2.Removing outliers
3. Filling the empty values for bmi column. The approach used is to firstly look at the different bmis for different genders. Then seperate them into age groups. 
4. Using vector encoding to gender, work_type, smoking_status and ever_married. The different values are not that many and we don't want a hierarchy to affect the model.

## 5. Model Training
First attempt was with a Logistic Regression. 
Due to extreme class imbalance, despite a 95% accuracy, the model failed to correctly predict any stroke cases. 
Second attempt was with Random Forest. Same results.
Third attempt was to do cross-validation with logistic regression and random forest. Same results
Fourth and final attempt was to use SMOTE, to create synthetic data of the minority of stroke cases to match the number of non-stroke cases.
Then, Logistic regression and random forest were used.

## 6. Evaluation
Before SMOTE:
F1-score (Logistic Regression): 0.49
F1-score (Random Forest): 0.49

No stroke cases were predicted correctly.

After SMOTE:
Logistic Regression:

Macro F1-score: 0.78
Accuracy: 78%

Random Forest:

Macro F1-score: 0.97
Accuracy: 97%

## 7. Conclusion
Balancing the dataset using SMOTE significantly improved the model’s ability to predict strokes, especially for the minority class. Random Forest outperformed Logistic Regression with a macro F1-score of 0.97, demonstrating strong potential for stroke prediction in healthcare datasets.
