# Liquidation Penalty

### Introduction

The Liquidation Penalty defines the number of points taken away from the DeFi Credit Score if the Borrower is liquidated on their position. This penalty is currently set to $$-250$$ points per liquidation per day per vault.

### Score Impact

The Liquidation Penalty subtracts 250 points for every day and every vault in which a liquidation occurs. The penalty only applies for 120 days, similar to the [Daily Score Reward](daily-score-reward.md). After this period, the penalty is removed from the Borrower’s score.
