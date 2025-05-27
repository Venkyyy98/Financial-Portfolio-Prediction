# 🧠 Financial Portfolio Prediction using Big Data and Sentiment Analysis

This project combines **financial news sentiment analysis** using FinBERT with **stock return data** to generate actionable trading signals (Buy / Hold / Sell). Built using **PySpark on Google Cloud Dataproc clusters**, it demonstrates how large-scale data processing and NLP can be leveraged for portfolio prediction and backtesting.

📓 View the full notebook here → [notebooks/trading_signal.ipynb](notebooks/trading_signal.ipynb)

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
- **Apache Spark / PySpark** – Distributed processing
- **Google Cloud Platform (GCP)** – Dataproc clusters for large-scale execution
- **FinBERT** – Financial sentiment classifier (HuggingFace Transformers)
- **Scikit-learn**, **Pandas**, **Matplotlib** – ML and visualization
- **Information Ratio** – Labeling logic for signal prediction

---

## 📊 Data Sources
- Financial news articles (title, date, ticker)
- Daily stock price and volume data
- SPY ETF (benchmark) for excess return calculation

---

## 🚀 Approach

1. **Preprocessing**
   - Clean and align news headlines with tickers and timestamps
   - Read data directly from **Google Cloud Storage (GCS)** into PySpark

2. **Sentiment Analysis**
   - Use **FinBERT** to classify each headline as `positive`, `neutral`, or `negative`

3. **Feature Engineering**
   - Merge sentiment scores with stock return data
   - Compute **Information Ratio (IR)** between stock and benchmark (SPY)

4. **Labeling**
   - IR > threshold → **Buy (1)**
   - IR < -threshold → **Sell (-1)**
   - Otherwise → **Hold (0)**

5. **Model Training**
   - Use PySpark MLlib (e.g., Logistic Regression, Random Forest)
   - Train models on labeled features and evaluate performance

6. **Backtesting**
   - Simulate trading strategies based on model predictions
   - Compare returns vs. benchmark performance

---

## 📈 Results

- FinBERT captured sentiment trends accurately from financial text
- Best model achieved an **F1-score of 0.82** in classifying signals
- Backtesting indicated potential alpha generation over passive holding

![Performance Metrics](reports/performance_metrics.png)

---

## ⚙️ How to Run

### Requirements
- Python 3.8+
- PySpark
- `transformers` (HuggingFace)
- Jupyter Notebook

### Steps

```bash
# Clone repository
git clone https://github.com/yourusername/Financial-Portfolio-Prediction.git
cd Financial-Portfolio-Prediction

# Install dependencies
pip install -r requirements.txt

# Run notebook
jupyter notebook notebooks/trading_signal.ipynb
```

📂 Or view it directly on GitHub:
notebooks/trading_signal.ipynb

⚠️ Note: In production, this was run on Google Cloud Dataproc clusters using PySpark for distributed data processing.
🔮 Future Scope

Use future returns for more robust labeling
Add technical indicators like RSI, MACD, and moving averages
Expand sentiment input using Reddit, Twitter, and earnings call transcripts
Deploy real-time pipeline with Spark Streaming + Kafka
Explore deep learning and transformer-based classification models
📄 License

This project is licensed under the MIT License.
See the LICENSE file for full details.

👨‍💻 Author

Venkatesh Mudaliar
🎓 Master’s in Data Science | Stevens Institute of Technology
🔗 www.linkedin.com/in/venkateshcmudaliar
📧 vmudalia@stevens.edu
