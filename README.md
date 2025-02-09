Lung Cancer Prediction Project

📌 Overview

This project aims to predict lung cancer presence based on various clinical and lifestyle features. The dataset is processed, engineered, and used to train multiple machine learning models to optimize predictive performance.

📊 Dataset

Source: phenotype.txt

Number of Samples: 16,955

Number of Features: 66 → Reduced to 49 after feature selection

Target Variable: LUNG (Lung Cancer Presence)

🔹 Data Preprocessing

1️⃣ Handling Missing Values

Mean Imputation: SMOK_B, HT_B, WT_B, WAIST_B, SBP_B, DBP_B, CHO_B, LDL_B, TG_B, HDL_B, FBS_B, GOT_B, GPT_B, GGT_B, URIC_B, BIL, WBC, CREAT

Zero Imputation: PCAN80-89, FCAN80-89

Conditional Imputation for SMOKA_MOD_B based on SMOK_B level

2️⃣ Outlier Processing

IQR-based capping for WBC

3️⃣ Feature Selection

Removed Non-Lung Cancer Response Variables: STOMA, COLON, LIVER, PROST, THROI, BREAC, RECTM, CRC, SSTOMA, SCOLON, SLIVER, SPROST, STHROI, SBREAC, SRECTM, SCRC, SLUNG

🔹 Exploratory Data Analysis

Correlation Analysis between LUNG and other features

Chi-Square Test for categorical variables

🔹 Feature Engineering

New Variables Defined:

SMOK_INT = SMOK_B * SMOKA_MOD_B (Smoking Intensity)

ALCO_INT = ALCO_AMOUNT_B / ALCO_B (Alcohol Intensity)

BMI = WT_B / (HT_B/100)^2 (Body Mass Index)

FEV1_FVC = FEV1 / FVC (Airflow Obstruction)

Family History Score:

Selected PCAN80, PCAN89, FCAN80

Trained logistic regression to determine weights

Final Score: Cancer_History_Score = x*PCAN80 + y*PCAN89 + z*FCAN80

🔹 Model Training & Evaluation

1️⃣ Random Forest Classifier

AUC Score: 0.7849

Feature Importance: BMI, WBC, AGE_B, FEV1_FVC, ALCO_INT, SMOK_INT, Cancer_History_Score

2️⃣ Logistic Regression

AUC Score: 0.7601

ROC Curve Visualization

3️⃣ Stacking Ensemble Model

Base Models: RandomForest, XGBoost, LightGBM, SVC

Final Estimator: Logistic Regression

AUC Score: 0.8068

4️⃣ Voting Classifier

Soft Voting with Base Models

AUC Score: 0.8088

5️⃣ K-Means Clustering (Experimental Approach)

AUC Score: 0.5929

📈 ROC AUC Visualization

Plotted ROC Curve for Logistic Regression, Stacking Model, and Voting Classifier.

📝 Notes

Family history of thyroid cancer in close relatives has a stronger correlation with a patient's lung cancer status than a family history of lung cancer in distant relatives.

Hypothesis: ALCO_B, EXER_B, WT_B, FVC may also be relevant features for lung cancer prediction.

🚀 Conclusion

Stacking and Voting Classifiers achieved the best performance with an AUC score of ~0.81.

Feature engineering and preprocessing played a crucial role in performance improvement.

Further optimization and hyperparameter tuning could enhance results.

🔗 Contact & Contributions

For any inquiries or contributions, feel free to open an issue or submit a pull request! 🎯

