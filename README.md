# Retail Customer Churn Prediction

End-to-end machine learning pipeline for predicting customer churn in a retail dataset.

## Project Structure

```
Retail_Customer/
├── data/
│   ├── customers.csv              # 5,000 customers
│   ├── transactions.csv           # 32,295 transactions
│   ├── interactions.csv           # 100,000 interactions
│   ├── support_tickets.csv        # 3,000 tickets
│   ├── customer_reviews_complete.csv  # 1,108 reviews
│   ├── campaigns.csv              # 200 campaigns
│   └── processed/
│       └── final_ml_dataset.csv   # Processed ML dataset
├── models/
│   └── retail_churn_pipeline.joblib  # Serialized model
├── Assignment4_Retail_ML.ipynb           # Original notebook
├── Assignment4_Retail_ML_CORRECTED.ipynb # Corrected notebook (all requirements)
├── app.py                         # Streamlit deployment app
└── requirements.txt               # Python dependencies
```

## Requirements

1. Load and inspect all datasets
2. Check primary key uniqueness
3. Identify parent-child relationships
4. LEFT JOIN merge strategy with documentation
5. Merge row-count validation
6. Unmatched key detection
7. Missing values from JOIN documented
8. Feature engineering (RFM, engagement, support, review)
9. Temporal cutoff to prevent data leakage
10. Temporal leakage audit on support tickets
11. Churn target variable creation
12. Preprocessing pipeline (impute, encode, scale)
13. Train/test split (80/20, stratified)
14. Feature selection (SelectKBest, multiple k values)
15. 4 ML models trained
16. 5-Fold Stratified CV + GridSearchCV
17. Model evaluation (accuracy, precision, recall, F1, ROC-AUC)
18. Error analysis with FP/FN comparison
19. Model deployment (joblib + Streamlit app + README)

## How to Run

1. Install dependencies:
   ```
   pip install -r requirements.txt
   ```

2. Run the corrected notebook:
   ```
   jupyter notebook Assignment4_Retail_ML_CORRECTED.ipynb
   ```

3. Run the Streamlit app:
   ```
   streamlit run app.py
   ```

## Data Lineage

- Raw CSVs -> Date conversion -> Temporal cutoff -> Feature engineering -> LEFT JOIN -> Missing value handling -> Preprocessing -> Feature selection -> Model training -> Evaluation -> Deployment
