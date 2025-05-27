# 🧠 Financial Portfolio Prediction using Big Data and Sentiment Analysis

This project combines **financial news sentiment analysis** using FinBERT with **stock return data** to generate actionable trading signals (Buy / Hold / Sell). Built using **PySpark**, it demonstrates how large-scale data processing and natural language processing (NLP) can be leveraged for portfolio prediction and strategy evaluation.

---

## 📌 Table of Contents
- [Problem Statement](#problem-statement)
- [Project Architecture](#project-architecture)
- [Technologies Used](#technologies-used)
- [Data Sources](#data-sources)
- [Approach](#approach)
- [Results](#results)
- [How to Run](#how-to-run)
- [Future Scope](#future-scope)
- [License](#license)

---

## ❓ Problem Statement

Can financial news sentiment, when combined with market and stock data, help predict profitable trading signals?

This project explores the use of **FinBERT**, a pre-trained financial language model, to label news headlines and combines them with stock/benchmark data to train machine learning models for signal prediction.

---

## 🏗️ Project Architecture

Raw News + Stock Tickers
       │
       ▼
Sentiment Analysis via FinBERT
       │
       ▼
Join with Stock Prices + SPY Returns
       │
       ▼
Label Generation (Buy / Hold / Sell via Information Ratio)
       │
       ▼
Model Training in PySpark (Logistic Regression, RF, etc.)
       │
       ▼
Performance Evaluation & Backtesting


---

## 🛠️ Technologies Used
- Apache Spark / PySpark
- FinBERT (Financial BERT model from HuggingFace)
- Google Cloud / Databricks
- Scikit-learn, Pandas, Matplotlib
- Information Ratio for performance labeling

---

## 📊 Data Sources
- Financial news articles (title, date, ticker)
- Daily stock price and volume data
- SPY ETF (benchmark) for excess return calculation

---

## 🚀 Approach

1. **Preprocessing**
   - Clean news and stock datasets
   - Align headlines with tickers and dates

2. **Sentiment Analysis**
   - Use FinBERT to classify each headline as `positive`, `neutral`, or `negative`

3. **Feature Engineering**
   - Merge sentiment with stock returns
   - Compute Information Ratio to label data:
     - IR > threshold → `Buy`
     - IR < -threshold → `Sell`
     - Otherwise → `Hold`

4. **Model Training**
   - Train ML models using PySpark MLlib
   - Evaluate using F1-score, accuracy, confusion matrix

5. **Backtesting**
   - Simulate investment strategy using model predictions
   - Compare with SPY benchmark returns


## 📈 Results

- FinBERT effectively captured sentiment trends from financial text
- Best ML model achieved **F1-score of 0.82**
- Backtesting showed improved returns using predicted signals over baseline strategies

![Performance Metrics](reports/performance_metrics.png)

---

## ⚙️ How to Run

### Requirements
- Python 3.8+
- PySpark
- `transformers` (HuggingFace)
- Jupyter Notebook

### Steps

# Clone repository
git clone https://github.com/yourusername/Financial-Portfolio-Prediction.git
cd Financial-Portfolio-Prediction

# Install packages
pip install -r requirements.txt

# Run notebook
jupyter notebook notebooks/01_preprocessing.ipynb


