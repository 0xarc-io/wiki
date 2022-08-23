# Profit modeling

This section contains analysis on unit level and aggregate profitability for the system as it is configured in the Closed Beta.&#x20;

### Unit-level profitability

Here, we describe the net profit expected from an individual Borrower in the worst case liquidation scenario. Based on our vault design and risk parameters, we conclude that vault “C” is a risky vault whereby a liquidation can in fact yield a loss (assuming a Borrower with a 999 Score / 100% LTV loan, and the liquidation is executed by an external liquidator).

For the purposes of this analysis, we will first articulate the journey of a Borrower who reaches the most risky position of having debt with a LTV of 100% in WETH-C (i.e. the Borrower with the greatest chance of creating toxic debt in the system).

**Journey to 999 Credit Score**

1. All Borrowers begin with a Score between 0-300, depending on their historical borrow experience on third-party platforms, according to the Survival Score Reward.
2. New Borrowers have access to only the WETH-A vault, with a maximum possible LTV of 90%.
3. The Borrower grows their Score until they reach a score of 500, which unlocks WETH-B.
4. The Borrower enters WETH-B with a maximum LTV of 95% and continues to borrow until they reach a Score of 750.
5. The Borrower reaches a Score of 750 and unlocks WETH-C.
6. The Borrower enters WETH-C and borrows until they have reached a score of 999.

Throughout this journey, the Borrower will be earning the platform revenue from interest and borrow fees until the point at which the Borrower can create toxic debt in the system. The longer it takes the Borrower to reach this point, the more revenue will be generated (but the total loss will remain constant).

The net profit from a Borrower who starts with a DeFi Credit Score of 0 is determined by:

| Vault  | Earned from borrow fee | Minimum time in vault (days)  | Earned from interest rate              | Losses when they liquidate |
| ------ | ---------------------- | ----------------------------- | -------------------------------------- | -------------------------- |
| WETH-A | $$0.002d$$             | $$120/999\times500=60$$       | $$d(e^{\frac{0.025\times60}{365}}-1)$$ | None                       |
| WETH-B | $$0.002d$$             | $$120/999\times(750-500)=30$$ | $$d(e^{\frac{0.025\times30}{365}}-1)$$ | None                       |
| WETH-C | $$0.002d$$             | $$120/999\times(999-750)=30$$ | $$d(e^{\frac{0.025\times30}{365}}-1)$$ | $$-0.05d$$                 |

Note that even if the Borrower never repays in WETH-C and the interest is not paid out directly, the accrued interest is subtracted from the loss experienced. The liquidated debt is actually larger than the initial borrow amount removed from the pool, and thus the toxic debt is lessened.

Adding up these components we arrive to:

$$
\begin{aligned}
P&=3\times0.002\times d+d(e^{\frac{0.025\times60}{365}}+2e^{\frac{0.025\times30}{365}}-3) - 0.05\times d\\
P&\approx-0.0358d \rarr -3.58\%\text{ of debt}

\end{aligned}
$$

So, for this user, who starts with a score of 0 and is liquidated by an external liquidator, we can expect to make a loss of 3.58% of the value of their debt.

The expected loss is greater in the case of the Borrower who begins with a score of 300. The calculation is almost exactly the same, except the time spent in WETH-A is shorter (24 days instead of 60 days):

$$
\begin{aligned}
P&=3\times0.002\times d+d(e^{\frac{0.025\times24}{365}}+2e^{\frac{0.025\times30}{365}}-3) - 0.05\times d\\
P&\approx-0.0382d \rarr -3.82\% \text{ of debt}

\end{aligned}
$$

So in the very worst case scenario, where the highest-scoring Borrower who has borrowed optimally liquidates at an LTV of 100%, we will yield a maximum loss of $3.82\\%$ of the value of their borrowed amount in Vault “C”.

In conclusion, we cannot ensure positive unit-profitability with the current design in the worst case scenario.

**Notes:**

* If ARCx performs the liquidation using our own bot, then the profit is actually net positive, at $1.18% of the value of the debt.
* The dynamic credit limit is particularly important for Vault C as it effectively limits the quantum of loss in the event of a worst case liquidation.
* We have assumed the liquidation engine, DEXs, the application, contracts, data pipelines and score rules work as expected when they need to.
* The analysis does not consider extreme market events (e.g. crashes, de-pegging, chain congestion). Losses may be higher under extreme circumstances.

### Aggregate profitability

While the analysis above shows how the net profit of an individual Borrower may be negative in the worst case scenario, the aggregate profitability across many Borrowers may in fact be positive. The fundamental thesis of ARCx Credit is that, on average, the revenue we generate from Borrowers will outweigh the expected losses born through unprofitable liquidations. ARCx Credit is therefore an experiment, which will be validated by real-world usage and refined through continuous improvements in our risk parameters and unique control parameters.&#x20;

Underpinning our thesis about ARCx Credit are two key assumptions that will be validated through monitoring real-world usage:

Firstly, the benefit of improved capital efficiency will incentivize borrowers to maintain their DeFi Credit Scores by appropriately managing risk and avoiding liquidations. Borrowers will eventually be able to quantify the value of their on-chain reputation in financial terms, making it possible to understand the point at which repaying an accumulated toxic debt on an address is a rational decision if it means preserving a high DeFi Credit Score. In general, when toxic debt is created, there is no such incentive to motivate a Borrower to repay, as Borrowers can simply spin up a new wallet address with zero cost. The DeFi Credit Score and ARCx Credit on the other hand impose a real cost to dissuade this kind of behavior - specifically the time and effort required to substantiate your borrowing experience and to build your Score.  &#x20;

Secondly, the distribution of net profit by Borrower will naturally skew positive based on the control parameters we have established. This is based on the following assumptions, which will be monitored closely as part of our routine risk management efforts:

* Not all Borrowers will follow the shortest path to reach a DeFi Credit Score of 999, since managing position at the “optimal” borrow usage levels requires continuous monitoring and adjustments.
* Some Borrowers may not want to hold the “optimal” borrow usage level (e.g. they may be more risk averse, or risk prone, which decreases the speed at which the DeFi Credit Score grows).
* Not all Borrowers will want to hold borrow positions open for the amount of time required to build their score to 999.
* Not all Borrowers will avoid liquidations in the “A” and “B” vaults, which are lower risk (and more profitable) for ARCx Credit.

### Conclusion

The design of ARCx Credit and the DeFi Credit Score makes it very unlikely that borrowing under normal conditions will lead to loss for the protocol. Unlike other DeFi lending protocols, ARCx Credit does not actively ensure unit-level profitability through its risk parameters. However, loss from an individual Borrower will only occur in a specific sequence of events and will more than likely be compensated by revenues from other Borrowers.

As discussed, the effectiveness of our system in generating sustainable profit will be understood and refined through real-world usage. We have decided to take a conservative approach to begin, but over time we are confident that our assumptions will prove to be valid.

To understand how the experiment is progressing, please follow the journey on [Discord](https://discord.gg/arcx).&#x20;
