# Loan Default Prediction

Predicting which borrowers will default on a loan, using 255,000+ loan records with demographic and financial features.

## The problem

Only about 12% of borrowers default, so a model that predicts "no default" for everyone is 88% accurate and useless. The goal here is to catch as many real defaulters as possible without flagging everybody.

## Data

255,347 loan records with 16 features, including age, income, loan amount, credit score, interest rate, DTI ratio, months employed, employment type, education, loan purpose and co-signer status. Target: `Default` (1 = defaulted).

## Approach

1. Cleaning and EDA
2. Feature engineering: `Income_to_Loan_Ratio`
3. Encoding: Yes/No columns mapped to 1/0, one-hot encoding for the rest
4. Stratified 80/20 train-test split
5. Three models, all with `class_weight='balanced'` to handle the imbalance

## Results (test set, 51,070 loans)

| Model | Accuracy | Default recall | Default precision | Default F1 |
| --- | --- | --- | --- | --- |
| Logistic Regression | 0.68 | 0.70 | 0.22 | 0.33 |
| Decision Tree (depth 5) | 0.66 | 0.68 | 0.21 | 0.32 |
| Random Forest (200 trees, depth 10) | 0.74 | 0.62 | 0.25 | 0.35 |

Random Forest gave the best F1 and far fewer false alarms (11,282 vs 14,691 for Logistic Regression). Logistic Regression caught the most defaulters (70%). Which one to use depends on what a missed default costs compared with a wrongly rejected customer.

## Key insights

- The strongest predictors were age (0.26), interest rate (0.18) and income-to-loan ratio (0.16), followed by months employed and income.
- Credit score mattered less than expected (0.04).
- The engineered income-to-loan ratio ranked third, ahead of raw income and loan amount.

## Limitations and next steps

- Precision on defaulters is low (about 1 in 4 flagged loans really defaults). Next step is tuning the decision threshold and trying gradient boosting.
- No cross-validation yet, only a single split.

## Run it

```bash
pip install pandas scikit-learn matplotlib seaborn jupyter
jupyter notebook main.ipynb
```

**Stack:** Python, Pandas, scikit-learn, Matplotlib, Seaborn
