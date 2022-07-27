# DeFi Credit Score

The DeFi Credit Score is a numeric value (between 0 and 999) that describes the credit risk of an individual address based on their on-chain borrowing activity. The Score is constructed from three main components - the Daily Score Reward, the Survival Score Reward, and the Liquidation Penalty. These three components are combined to derive the final DeFi Credit Score.

* The **Daily Score Reward** evaluates borrow usage over the past 120 days relative to an “optimal” borrower archetype and rewards points along the “Rewards Curve” on a daily basis.
* The **Survival Score Reward** evaluates a borrower’s ability to avoid liquidations relative to the rest of the market, rewarding points (or subtracting points if liquidated) proportional to the market’s “liquidation density” on a given day.
* The **Liquidation Penalty** subtracts a fixed number of points for every day in which a liquidation occurs.

Through managing a risk-adjusted position over a period of time while avoiding liquidations, borrowers can unlock greater capital efficiency in DeFi through borrowing on the ARCx Credit platform.

This section covers:

1. [Background](background.md)
2. [Daily Score Reward](daily-score-reward.md)
3. [Survival Score Reward](survival-score-reward.md)
4. [Liquidation Penalty](liquidation-penalty.md)
5. [Data Sources](data-sources.md)
