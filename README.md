# Aave V2 DeFi Wallet Credit Scoring System

This project builds a machine learning credit scoring model (0–1000 scale) for wallets interacting with the Aave V2 protocol. The goal is to identify trustworthy, responsible DeFi users by analyzing their historical transaction behavior (deposit, borrow, repay, etc.).

# Objective of the model

To build a scoring system based  on user behavior and historical activity across DeFi actions in Aave V2

# Features

| Feature | Description |
| `total_deposit` | Total ETH-equivalent deposited by the wallet |
| `total_borrow` | Total borrow volume |
| `total_repay` | Total repayments made |
| `total_redeem` | Total assets withdrawn |
| `repay_to_borrow` | Ratio of repay to borrow (measures repayment discipline) |
| `borrow_to_deposit` | Ratio of borrow to deposit (measures leverage) |
| `liquidation_count` | Number of liquidation events |
| `tx_per_day` | Average number of transactions per day |
| `action_diversity` | Number of unique action types performed |

---

# Scoring Strategy

A rule-based scoring system is used:

- Each feature is scaled using Min-Max Normalization
- Weights are assigned to each feature:
    - Positive weights for good behavior (repayments, deposits)
    - Negative weights for risky behavior (liquidations, high leverage)
- Final score is scaled to the 0–1000 range

Formula:

```text
credit_score = Scaled_Feature_Vector · Weights
