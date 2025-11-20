# Stock-Price-Prediction-Using-Pytorch

Here is your **ready-to-paste README.md**, with proper Markdown formatting only — no extra explanations.

---

# Stock Price Prediction Using PyTorch

This project demonstrates how to build, train, and evaluate an LSTM-based neural network to predict Amazon (AMZN) stock closing prices using historical data. The workflow includes data preprocessing, time-series feature engineering, model training, and visualization of predictions.

---

## 📂 Dataset

The project uses historical **AMZN** stock data containing:

* Date
* Open
* High
* Low
* Close
* Adj Close
* Volume

Only the **Date** and **Close** columns are used for modeling.

---

## 🔧 Requirements

Install the required packages:

```bash
pip install torch pandas numpy scikit-learn matplotlib
```

---

## 🧠 Model Architecture

* **Input size:** 1 (closing price)
* **Lookback window:** 7 days
* **Hidden size:** 4
* **LSTM layers:** 1
* **Output:** 1 future closing price
* **Loss:** MSELoss
* **Optimizer:** Adam (lr = 0.001)

---

## 🚀 Workflow

### 1. Data Preprocessing

* Parse `Date` as datetime
* Keep only `Date` and `Close`
* Create lag features:

  ```
  Close(t-1), Close(t-2), ..., Close(t-7)
  ```
* Remove NaN values
* Normalize values using MinMaxScaler in range `[-1, 1]`

### 2. Dataset Preparation

* Split dataset into **95% train** and **5% test**
* Reshape input for LSTM:

  ```
  (batch_size, sequence_length, features)
  ```
* Use PyTorch Dataset + DataLoader

### 3. Model Training

* Forward pass
* Compute loss
* Backpropagation
* Update weights
* Print loss every 100 batches
* Validate after each epoch

### 4. Prediction & Evaluation

* Predict on training and test sets
* Apply inverse-scaling to recover actual price values
* Visualize:

  * Actual vs Predicted (Train)
  * Actual vs Predicted (Test)

---

## 📈 Results

The LSTM model successfully learns the general patterns of AMZN’s price trend. Training and validation losses decrease across epochs, and predicted values closely follow actual prices on both train and test sets.

Graphs produced:

* Training predictions vs. actual prices
* Test predictions vs. actual prices

## ⚠️ Notes

* The model predicts **one day ahead** only.
* Only closing prices are used—adding technical indicators may improve performance.
* Predictions are for educational purposes only and not financial advice.
