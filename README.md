# Retail Customer Churn Prediction

A machine learning project for predicting customer churn in a retail business using multiple data sources including customer profiles, transactions, interactions, support tickets, and reviews.

## Group Members

1. Adili S. Edward
2. Joseph M. Nzije
3. Carol F. Kika
4. Frank L. Mlyakalamu
5. Athanas J. Kayombo
6. Mathias B. Ngilangwa

## Project Structure

```
customer-prediction/
├── Assignment4_Retail_ML.ipynb   # Main ML notebook
├── data/
│   ├── customers.csv             # Customer profiles (5,000 records)
│   ├── transactions.csv          # Transaction history
│   ├── interactions.csv          # Customer interactions
│   ├── support_tickets.csv       # Support tickets
│   ├── customer_reviews_complete.csv # Customer reviews
│   ├── campaigns.csv             # Marketing campaigns
│   ├── processed/
│   │   └── final_ml_dataset.csv  # Processed ML dataset
│   ├── app.py                    # FastAPI deployment
│   └── form.html                 # Prediction form
├── models/
│   └── final_churn_model.joblib  # Trained model
└── .gitignore
```

## Datasets

| Dataset | Description | Key Fields |
|---------|-------------|------------|
| **Customers** | 5,000 customer records | customer_id, full_name, age, gender, city, state |
| **Transactions** | Purchase history | transaction_id, customer_id, amount, date |
| **Interactions** | Customer touchpoints | interaction_id, customer_id, channel, type |
| **Support Tickets** | Customer support records | ticket_id, customer_id, status, priority |
| **Reviews** | Customer feedback | review_id, customer_id, rating, sentiment |
| **Campaigns** | Marketing campaigns | campaign_id, name, budget, ROI |

## ML Pipeline

### Data Processing
- Data inspection and quality assessment
- Primary/foreign key identification
- Merge strategy using LEFT JOINs
- Missing value handling
- Duplicate detection

### Feature Engineering
- Customer-level aggregation from all source tables
- Transaction features (total spend, frequency, recency)
- Interaction features (engagement metrics)
- Support ticket features (resolution rates, satisfaction)
- Review features (average rating, sentiment scores)

### Target Variable
- **Churn**: Binary classification (1 = churned, 0 = active)
- Based on transaction activity within a defined cutoff period

### Models Trained
1. **Logistic Regression** - Baseline linear model
2. **Random Forest** - Ensemble tree-based model
3. **Gradient Boosting** - Sequential ensemble method
4. **Hist Gradient Boosting** - Optimized gradient boosting

### Model Evaluation
- Cross-validation with hyperparameter tuning
- Feature selection for optimal performance
- Final model saved as `final_churn_model.joblib`

## Deployment

The project includes a FastAPI-based REST API for serving predictions.

### Run the API

```bash
cd data
uvicorn app:app --reload
```

### Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/` | GET | Prediction form |
| `/health` | GET | Health check |
| `/predict` | POST | Customer churn prediction |

### Sample Request

```json
POST /predict
{
  "age": 35,
  "gender": "Male",
  "total_transactions": 15,
  "total_spend": 2500.00,
  ...
}
```

## Requirements

```bash
pip install pandas numpy matplotlib seaborn scikit-learn fastapi uvicorn joblib
```

## Usage

1. Open `Assignment4_Retail_ML.ipynb` in Jupyter Notebook/Lab
2. Run all cells to execute the full ML pipeline
3. Access the API at `http://localhost:8000` for predictions

## License

Educational project - Group Assignment 4
