
#### Project Overview

Financial institutions face significant losses due to loan defaults. This project uses machine learning to predict whether a customer will default on a loan based on demographic and financial features, enabling better risk assessment and proactive intervention.

---

#### Problem Statement

Predict whether a customer will default on a loan (`Default = 1`) or not (`Default = 0`) using customer financial and demographic data.

---

#### Dataset

The dataset contains over 255,000 loan records with features such as:

* Age, Income, Loan Amount
* Credit Score, Interest Rate, Debt-to-Income Ratio
* Employment Type, Education Level, Loan Purpose
* Mortgage, Dependents, Co-signer information

The target variable is **Default**.

---

####  Methodology

* Data cleaning and preprocessing
* Exploratory Data Analysis (EDA)
* Feature engineering (e.g. Income-to-Loan Ratio)
* Categorical variable encoding
* Train-test split with class stratification
* Model training and comparison:

  * Logistic Regression
  * Decision Tree
  * Random Forest

---

#### Model Evaluation

Due to class imbalance, model performance was evaluated using:

* Precision
* Recall
* F1-score
* Confusion Matrix

**Random Forest** achieved the best balance between precision and recall, making it the final selected model.

---

#### Key Insights

* Interest rate and credit score were among the most important predictors of loan default.
* Higher loan burden relative to income significantly increased default risk.
* Ensemble methods outperformed single-model approaches.

---

#### Conclusion

The Random Forest model effectively identifies high-risk borrowers while maintaining a reasonable balance between false positives and missed defaulters. This approach can support financial institutions in making data-driven lending decisions.


