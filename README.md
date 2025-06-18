# Decision Support System for Predicting Blood Pressure Disorders

This project presents a Decision Support System (DSS) that leverages machine learning algorithms to predict blood pressure disorders (hypertension and hypotension) based on clinical and demographic variables.

## Abstract

Blood pressure issues—particularly hypertension—are prevalent not only among the elderly but are increasingly affecting younger adults due to stress, poor lifestyle habits, and genetic predispositions. Many individuals may not exhibit any symptoms, which leads to late diagnoses.

This study aims to build a machine learning–based DSS that predicts blood pressure disorders using the following features:
- Age
- Sex
- Body Mass Index (BMI)
- Cholesterol Level
- Heart Rate
- Glucose Level

The system applies Random Forest, Decision Tree, and XGBoost classifiers. Among them, the Random Forest algorithm showed the highest accuracy of **85.81%** using 10-fold cross-validation.

## Dataset

- **Source:** Framingham Heart Study (available on Kaggle)
- **Records:** 4,896 samples
- **Features:** 11 selected features after preprocessing
- **Target:** Binary classification (0 = Normal, 1 = Disorder)

### Feature Engineering
- Blood pressure disorder was derived using systolic and diastolic blood pressure:
  - Hypertension: `sysBP ≥ 140` or `diaBP ≥ 90`
  - Hypotension: `sysBP < 90` and `diaBP < 60`

### Data Preprocessing Steps
- Missing values imputed or dropped
- Outliers retained (as they may indicate valid risk)
- Highly correlated variables (e.g., smoking status and cigs per day) removed
- Feature scaling applied via **Min-Max Normalization**
- Class imbalance addressed via **oversampling**

## Exploratory Data Analysis

Correlation and boxplot visualizations were used to understand relationships:
- Strong correlation between systolic & diastolic pressure (r = 0.78)
- Prevalent hypertension correlated with higher BP values
- Glucose had moderate correlation with diabetes status
- Age correlated with increased hypertension prevalence
- Gender-based analysis showed males had wider BP variation

## Machine Learning Models

| Algorithm       | Accuracy | Recall  | Precision | F1-Score |
|----------------|----------|---------|-----------|----------|
| Random Forest  | 82.86%   | 86.55%  | 81.02%    | 83.69%   |
| XGBoost        | 80.20%   | 86.95%  | 77.05%    | 81.70%   |
| Decision Tree  | 79.39%   | 87.75%  | 75.61%    | 81.23%   |

- **Best Performing Model:** Random Forest + 10-Fold Cross-Validation → **85.81% Accuracy**

## Technologies Used

- Python (Pandas, NumPy, Matplotlib, Seaborn, Scikit-Learn, XGBoost)
- Jupyter Notebook
- Dataset: Framingham Heart Study (Kaggle)

## File Structure

```
📂 blood-pressure-dss/
├── 📄 README.md
├── 📄 dss_model.ipynb         # Model implementation
├── 📊 figures/
│   ├── correlation_heatmap.png
│   ├── systolic_distribution.png
│   └── ...
└── 📂 data/
    └── framingham.csv
```

## Conclusion

This DSS demonstrates how machine learning can assist in the early detection of blood pressure disorders. By identifying individuals at risk, proactive monitoring and treatment can reduce long-term health complications and healthcare costs.

## 🚀 Future Work

- Integration with real-time IoT monitoring devices
- Expansion of features (e.g., ECG data, lifestyle habits)
- Deployment as a clinical web application
