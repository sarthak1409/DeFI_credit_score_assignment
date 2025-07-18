# DeFi Credit Scoring Model

This project uses transaction-level data from the Aave V2 protocol to generate credit scores (0–1000) for wallets based on their behavior.

## 🧠 Approach
- **Input**: JSON file of DeFi transactions (100K records)
- **Feature Engineering**: 
  - Count of actions (deposit, borrow, repay, liquidation)
  - Total amounts involved
  - Ratios: repay/borrow, liquidation/borrow
- **Model**: KMeans clustering
- **Output**: Credit score between 300 and 800

## 🛠️ How It Works
1. Read the data and extract transaction features per wallet.
2. Normalize feature values.
3. Cluster users into behavior groups.
4. Assign credit scores based on cluster behavior.

## 📤 Output
- `wallet_credit_scores.csv` – credit score for each wallet
- `analysis.md` – score distribution & behavioral insights

## 📈 Libraries Used
- Pandas, NumPy
- Scikit-learn (KMeans, MinMaxScaler)
- Matplotlib, Seaborn

## ✅ How to Run
```bash
python credit_scoring_notebook.ipynb  # or run in Jupyter
```
