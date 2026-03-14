# Credit Card Default Prediction with Random Forest

This project uses a **Random Forest classifier** to predict whether a credit card customer is likely to default in the next payment period.

## Project Overview

The project is based on the **Default of Credit Card Clients (Taiwan)** dataset from the UCI Machine Learning Repository. It applies machine learning to a credit risk problem by using historical repayment behavior and customer-related variables to classify future default risk.

## Dataset

- Source: UCI Machine Learning Repository
- Dataset: Default of Credit Card Clients (Taiwan)
- Approximate sample size: 30,000 records
- Target label:
  - `Y = 1`: default next month
  - `Y = 0`: no default next month

The raw dataset file is stored at:

```bash
data/raw/default_of_credit_card_clients.xls
