# 🛡️ Fraud Detection with Machine Learning

This project demonstrates how to build a fraud detection system using a **Random Forest Classifier**. It covers the entire pipeline from data loading and feature engineering to model training and evaluation.

## 📌 Objective

Detect fraudulent credit card transactions using behavioral and time-based features.

---

## 📁 Dataset

- Format: `.pkl` files (each file = 1 day's transactions)
- Fields include:
  - `TX_AMOUNT`, `TX_DATETIME`, `CUSTOMER_ID`, `TERMINAL_ID`, `TX_FRAUD`
- Combined into one large DataFrame of shape **(1,754,155 rows × 9 columns)**

---

## 🛠️ Feature Engineering

Features created to capture temporal and behavioral patterns:

- `TX_DAY`, `TX_HOUR`, `TX_WEEKDAY` from datetime
- `CUSTOMER_AVG_AMOUNT_5`: Rolling 5-txn average
- `TX_UNIX`: UNIX timestamp for time operations
- `CUSTOMER_TX_COUNT_1D`: Customer transactions in last 24h
- `TERMINAL_FRAUD_COUNT_28D`: Terminal-level frauds in last 28 days

---

## 🤖 Model Training

- **Model Used**: `RandomForestClassifier (n_estimators=100)`
- **Features**:
  ```python
  ['TX_AMOUNT', 'TX_DAY', 'TX_HOUR', 'TX_WEEKDAY',
   'CUSTOMER_AVG_AMOUNT_5', 'CUSTOMER_TX_COUNT_1D',
   'TERMINAL_FRAUD_COUNT_28D']
  ```
- Train-Test Split: 80/20 stratified

---

## 📊 Evaluation

- **Confusion Matrix**:
  ```
  [[347074    821]
   [ 1137   1799]]
  ```

- **Classification Report**:
  ```
              precision    recall  f1-score   support
     0         1.00        1.00      1.00     347895
     1         0.69        0.61      0.65       2936
  ```

- **Accuracy**: **99.44%**

---

## ✅ Conclusion

- High accuracy shows strong potential for real-world deployment.
- Temporal and behavioral features significantly enhance fraud detection.
- This can be expanded into a real-time fraud monitoring system.
