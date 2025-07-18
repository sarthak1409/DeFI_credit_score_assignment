
# 💳 DeFi Credit Scoring Model using Aave V2 Data

This project builds a **credit scoring system for DeFi wallets** using behavioral data from the Aave V2 protocol on the Polygon network. Wallets are clustered using unsupervised machine learning based on their transaction patterns, and a credit score between **200 and 1000** is assigned accordingly.

---

## 📌 Objective

To design a data-driven model that evaluates wallet behavior in decentralized finance (DeFi) and generates **credit scores** based on:
- Borrowing and repayment activity
- Liquidation history
- Transaction amounts and frequency

This scoring can be used by DeFi lenders or credit protocols for risk profiling.

---

## 📊 Method Chosen

The project uses an **unsupervised learning** approach:

- **KMeans Clustering** is applied to group wallets based on behavior.
- Features are extracted from historical on-chain transactions such as:
  - Deposit, borrow, repay, redeem, liquidation counts
  - Transaction volume statistics
- Credit scores are mapped to clusters based on risk level (e.g. low liquidation → high score).

---

## 🏗️ Architecture

```
Raw JSON Data (Aave V2) → Pandas DataFrame
        ↓
Feature Engineering (Grouped by Wallet)
        ↓
Standard Scaling → PCA (Dimensionality Reduction)
        ↓
KMeans Clustering (k=5)
        ↓
Cluster-to-Score Mapping (Based on Liquidation Rate)
        ↓
Credit Scores per Wallet
```

### 🔧 Tools & Libraries Used
- `Pandas`, `NumPy` – data manipulation
- `Scikit-learn` – clustering, scaling, PCA
- `Matplotlib`, `Seaborn` – visualizations

---

## 🔄 Processing Flow

1. **Data Ingestion**  
   Read a JSON file containing ~100K Aave V2 transaction records. Each row represents a DeFi transaction.

2. **Feature Engineering**  
   Group transactions by wallet address and compute:
   - Total transactions
   - Count of each action type (deposit, borrow, repay, etc.)
   - Total/average/std of amounts

3. **Data Scaling & Reduction**  
   - StandardScaler is used to normalize features.
   - PCA reduces dimensionality for better clustering.

4. **Clustering (KMeans)**  
   - Wallets are clustered into 5 groups based on behavior.
   - Each cluster represents a credit risk profile.

5. **Credit Score Assignment**  
   - Clusters with fewer liquidations are considered safer.
   - Scores are assigned: `200 (high risk)` → `1000 (low risk)`

6. **Outputs Generated**
   - `wallet_credit_scores.csv` – Credit score for each wallet
   - `wallet_cluster_stats.csv` – Full metrics + cluster label
   - `score_distribution.png` – Histogram of credit scores

---

## 📁 Folder Structure

```
internship_assignment/
│
├── data/                     # Folder containing input data (e.g., data.json)
│   └── (not uploaded due to size limits)
│
├── outputs/                  # Final outputs like CSVs and plots
│   ├── wallet_credit_scores.csv
│   ├── wallet_cluster_stats.csv
│   └── score_distribution.png
│
├── DeFi_credit_scoring.ipynb # Jupyter notebook containing full analysis
├──requirements.txt           # libraries required for download
├── analysis.md               # Markdown summary of your analysis steps
└──  readme.md                 # Project overview, architecture, and method
                    # This file
```

---

## 📌 Notes for Reviewers

> **Dataset is not included** due to size and confidentiality constraints (provided by the interviewer).  
> The code is complete and can be tested with any similar Aave V2 data containing user actions.

---

## 👨‍💻 Author

**Sarthak Maddi**  
Passionate about solving real-world problems using data science and machine learning.
