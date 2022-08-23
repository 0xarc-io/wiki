# DeFi Credit Score

The DeFi Credit Score is a numeric value (between 0 and 999) that describes the credit risk of an individual address based on their on-chain borrowing activity. The Score is constructed from three main components - the Daily Score Reward, the Survival Score Reward, and the Liquidation Penalty. These three components are combined to derive the final DeFi Credit Score.

* The **Daily Score Reward** evaluates your borrow usage (i.e. current LTV as a percentage of max LTV) on ARCx Credit vaults over the prior 120 days relative to a “responsible” borrower archetype and rewards points according to a “Rewards Curve” on a daily basis.
* The **Survival Score Reward** evaluates a borrower’s ability to avoid liquidations on any indexed third-party platform relative to the rest of the market, rewarding or subtracting points proportional to the “liquidation density” on a given day.
* The **Liquidation Penalty** subtracts a fixed number of points for every day in which a liquidation occurs. The penalty only applies for 120 days, similar to the Daily Score Reward. After this period, the penalty is removed from the Borrower’s score.

Through managing a risk-adjusted position over a period of time while avoiding liquidations, borrowers can unlock greater capital efficiency in DeFi through borrowing on the ARCx Credit.

This section covers:

1. [Background & Opportunity](background-and-opportunity.md)
2. [Daily Score Reward](daily-score-reward.md)
3. [Survival Score Reward](survival-score-reward.md)
4. [Liquidation Penalty](liquidation-penalty.md)
5. [Data Sources](data-sources.md)
