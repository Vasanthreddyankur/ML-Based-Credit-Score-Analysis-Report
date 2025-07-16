**Credit Scoring Engine for Aave V2 Wallets (with Machine Learning)**

**This project computes a credit score (0--1000) for each DeFi wallet
based on its historical interactions with the Aave V2 protocol. The
scoring logic is powered by unsupervised machine learning (KMeans
clustering) to identify wallet behavior patterns.**

**Objective**

**Build a transparent, extensible ML-based credit scoring system that:**

-   **Analyzes raw DeFi transactions**

-   **Extracts behavioural wallet features**

-   **Scores users with a clustering-based method**

**Dataset**

-   **File: user-wallet-transactions.json.zip**

-   **Content: 100K transaction-level records from Aave V2**

-   **Fields: wallet address, timestamp, action (deposit, borrow, repay,
    redeem, liquidation), token info**

**Architecture**

**Raw JSON Zip File**

**⬇️**

**Unzip + Load JSON**

**⬇️**

**Feature Engineering (per wallet)**

**⬇️**

**Normalize Features (StandardScaler)**

**⬇️**

**KMeans Clustering (5 clusters)**

**⬇️**

**Map cluster → credit score**

**⬇️**

**Save results as wallet_credit_scores.csv**

**🔍 Feature Engineering**

**For each wallet, we compute:**

  -----------------------------------------------------------------------
  **Feature**                    **Description**
  ------------------------------ ----------------------------------------
  **num_deposits**               **Number of deposits**

  **total_deposit_usd**          **Total value of deposits in USD**

  **num_borrows**                **Number of borrows**

  **total_borrow_usd**           **Value of borrows in USD**

  **num_repays**                 **Number of repayments**

  **total_repay_usd**            **Value of repayments in USD**

  **repay_to_borrow_ratio**      **Repaid / Borrowed ratio**

  **num_liquidations**           **Liquidation events count**

  **num_redeems**                **Redeems made**

  **total_redeem_usd**           **Redeem amount in USD**

  **avg_txn_interval_days**      **Avg time between transactions**

  **active_days**                **Unique number of active days**

  **asset_diversity**            **Number of distinct assets used**

  **total_tx_count**             **Total transaction count**
  -----------------------------------------------------------------------

**Machine Learning Model**

**We use KMeans clustering to group wallet behaviors into 5 clusters.
Features are normalized using StandardScaler. Each cluster is then
mapped to a fixed credit score:**

  -----------------------------------------------------------------------
  **Cluster ID**         **Assigned Credit Score**
  ---------------------- ------------------------------------------------
  **0**                  **200**

  **1**                  **400**

  **2**                  **600**

  **3**                  **800**

  **4**                  **1000**
  -----------------------------------------------------------------------

**This creates a fully automated, data-driven wallet scoring system.**

**Output**

-   **wallet_credit_scores.csv contains:**

    -   **All extracted features**

    -   **cluster column**

    -   **credit_score column (scaled 0--1000)**

**📂 Files**

-   **wallet_credit_score.py -- Main script (unzips, extracts features,
    clusters, scores)**

-   **wallet_credit_scores.csv -- Output scores for all wallets**

-   **README.md -- Documentation of method and pipeline**

-   **analysis.md -- Behavioural summary by score range**
