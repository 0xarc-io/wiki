# ARCx Credit Introduction

### What is ARCx Credit?

ARCx Credit is a decentralized liquidity market on Polygon that offers the safest and most capital-efficient borrowing experience in DeFi through the use of the DeFi Credit Score. Unlike traditional borrowing protocols, ARCx Credit rewards Borrowers who demonstrate effective risk management practices by granting them progressively higher maximum loan-to-value (LTV) ratios on their loans. The primary objective for ARCx Credit is to profitably improve capital efficiency in DeFi lending markets through measuring and rewarding responsible borrowing behavior.

### How does ARCx Credit work?

1. We use the DeFi Credit Score to continuously analyze on-chain behavior and to evaluate the credit risk of individual wallet addresses in DeFi.
2. We offer personalized maximum LTV ratios to borrowers based on their DeFi Credit Score, where the higher the score, the higher the maximum LTV (i.e. capital efficiency).
3. We continuously manage risk to ensure protocol profitability, generating revenue through fees and minimizing losses through a variety of control mechanisms.

### What is the DeFi Credit Score?

The [DeFi Credit Score](application/defi-credit-score/) is a numeric value (between 0 and 999) that describes the credit risk of an individual address based on their on-chain borrowing activity. The score calculation is based on the experience each borrower has in managing risk and avoiding liquidation over a period of time. Scores are calculated off-chain and then published on-chain via our custom oracle [infrastructure](risk-and-infrastructure/infrastructure/).

### Why credit score-based borrowing?

Conventional DeFi lending protocols navigate the risks associated with servicing pseudo-anonymous borrowers with volatile and illiquid collateral by imposing high collateral requirements on loans. This means that for an asset like ETH, borrowers may only take on $0.80 worth of debt for every $1 in collateral before their positions are subject to liquidation. Moreover, these protocols offer the same terms to all borrowers, regardless of their experience or credit worthiness. We believe that strict enforcement of these rules does not incentivize responsible borrowing behavior, contributing to excessive risk exposure and inefficient capital allocation across the industry.

### How do I build my DeFi Credit Score?

You can build your DeFi Credit Score by borrowing on ARCx or on a selection of third-party platforms. Your DeFi Credit Score is determined by three main components - the Daily Score Reward, the Survival Score Reward, and the Liquidation Penalty

* ****[**Daily Score Reward**](application/defi-credit-score/daily-score-reward.md) - The Daily Score Reward evaluates borrow usage on ARCx Credit over the past 120 days relative to an “optimal” borrower archetype and rewards points along the “Rewards Curve” on a daily basis. Borrowing at the optimal point maximizes the speed at which the DeFi Credit Score grows. Borrowing above or below this point continues to grow the Score, but at a slower rate.
* ****[**Survival Score Reward**](application/defi-credit-score/survival-score-reward.md) - The Survival Score Reward evaluates a borrower’s ability to avoid liquidations relative to the rest of the market, rewarding points (or subtracting points if liquidated) proportional to the market’s “liquidation density” on a given day. By looking at how well a borrower has “survived” periods of high volatility, we can calculate a propensity for them to avoid liquidation in the future. A Borrower who has demonstrated they can survive market downturns will score higher.
* ****[**Liquidation Penalty**](application/defi-credit-score/liquidation-penalty.md) - The Liquidation Penalty subtracts a fixed number of points for every day in which a liquidation occurs.

The Survival Score reward is a value between 0 and 300, while the Daily Score Reward allows borrowers to earn up to 8 points per day (if they borrow at the “optimal” point). The three components are added together, and the sum of these values equals your DeFi Credit Score.&#x20;

For more information, see [Credit score](application/defi-credit-score/).&#x20;

### How does my credit score relate to borrow usage?

You can build your DeFi Credit Score by [borrowing on ARCx Credit](application/defi-credit-score/daily-score-reward.md) or on a [selection of third-party platforms](application/defi-credit-score/data-sources.md). The speed at which the [Daily Score Reward](application/defi-credit-score/daily-score-reward.md) component of your DeFi Credit Score grows is directly related to Borrow Usage across your active positions on ARCx. Borrow Usage represents the amount you have borrowed relative to your available credit, which is determined by the amount of collateral you have deposited and the maximum LTV you are offered.

![Position summary card showing a Borrower with slow Credit Score growth](<.gitbook/assets/Position Summary.png>)

### Can my DeFi Credit Score go down?

Your DeFi Credit Score may lose points in two ways.

* Firstly, your score will eventually trend downward if your Daily Score Reward equals 0. This will happen if you stop borrowing entirely (and your borrow usage is 0%), or if you borrow in excess of the “critical point” (i.e. your borrow usage is greater than 90%). This is because we calculate your Daily Score Reward using on-chain data from the past 120 days. Only values within the window of time are considered when calculating the score.
* Secondly, your score will diminish if any of your active positions are liquidated. Currently, a penalty of -250 points per liquidation per day is imposed. After 120 days, the penalty is removed and the liquidation event is no longer considered.

### What is the “optimal” borrow usage to grow my credit score?

We believe that what defines “optimal” borrowing can be informed by borrowers themselves. By taking a “community consensus” of borrowers on Compound who borrowed against Ethereum collateral, we arrived at our current optimal Borrow Usage of 60%. As we gather more data on borrower behavior, we plan to make this optimal value a dynamic variable based on the real-world actions of borrowers with the highest credit scores.

For more information, see [Daily Score Reward](application/defi-credit-score/daily-score-reward.md).

### Which third-party borrowing platforms are currently indexed?

In addition to using borrowing activity from ARCx to construct the DeFi Credit Score, we also index data from third-party platforms (e.g. Aave and Compound). The process of indexing a third-party platform takes time, but we are constantly adding more. Our ultimate goal is to build the reference credit score used across DeFi. If you would like us to start indexing a particular platform or protocol, please let us know by joining our [Discord](http://discord.gg/arcx) and speaking with our team.

For a list of third-party borrowing platforms currently indexed, see [Data Sources](application/defi-credit-score/data-sources.md).

### How do I interact with ARCx Credit?

In order to interact with ARCx Credit, you will first need to deposit collateral into one of our vaults (e.g. WETH-A). After depositing, you will be allowed to borrow up to your maximum loan-to-value (LTV) ratio. In order to maximize the speed at which your DeFi Credit Score grows, you can choose to borrow at the “optimal” Borrow Usage level. Once a borrow position is active, you can then view and manage your position over time, including depositing, borrowing, repaying, or withdrawing. Finally, since your DeFi Credit Score grows over time, you can revisit the app to see how your improved Score corresponds to a higher maximum LTV (and thus greater capital efficiency).

### Why are there multiple vaults for the same collateral type?

ARCx Credit has implemented a three-tiered vault design, with each collateral asset having three distinct vault options distinguished by the range of max LTVs offered, the minimum Score required to access the vault (i.e. the "Score Threshold"), and the maximum credit limit a borrower can access (regardless of their deposited collateral).&#x20;

![Borrow vaults table showing the score threshold and maximum LTV ratio offered for each vault](<.gitbook/assets/Borrow vaults mini.png>)

The three-tiered vault design was selected to balance the user experience requirement of progressively and frictionlessly unlocking greater capital efficiency while borrowing, with the financial and risk requirement of minimizing losses through unprofitable liquidations. The design provides ARCx Credit with the ability to fine-tune a variety of risk controls at the individual vault-level (such as max-LTV ranges, score thresholds, and credit limits), helping to maximize net profit across our loan book. Additionally, since Lenders are able to supply funds to Borrowers with specific Score ranges (e.g. over 500 only), we create the conditions necessary for the market to determine a true credit spread between different Borrowers based on the DeFi Credit Score.&#x20;

For more information, see [profit model](risk-and-infrastructure/risk-management/) and [vault design and credit limits](application/borrowing/vault-design-and-credit-limits.md).

### What costs are associated with borrowing on ARCx Credit?

ARCx Credit charges borrowers an interest rate on outstanding loans, a borrow initiation fee, and a penalty for liquidations.&#x20;

For more information, see [fee structure](application/borrowing/fee-structure.md).&#x20;

### How frequently is my DeFi Credit Score updated?

The DeFi Credit Score is updated on-chain with a 48-hour time delay. This delay is a security feature, which will be shortened over time.&#x20;

For more information, see [infrastructure](risk-and-infrastructure/infrastructure/).

### What risks are involved?

By offering greater capital efficiency to borrowers with high Scores, ARCx Credit exposes itself to the risk that liquidations create ‘toxic debt’ for lenders (i.e. where the value of the sold collateral is lower than the debt borrowed). We control these losses through a variety of mechanisms, including our three-tiered vault design, dynamic credit limits, self-managed liquidations and revenue inflows which offset losses.&#x20;

For more information, see [profit model](risk-and-infrastructure/risk-management/).

Besides this, ARCx Credit is also exposed to smart contract risk (i.e. the risk that a bug within the protocol code can be exploited). ARCx Credit is a new protocol that has been in development for over 12 months. Our contracts are scheduled to be audited by Trail of Bits in October 2022.

### What is the ARCX Governance Token?

The ARCx Governance Token is the primary governance mechanism for the ARCx protocol. The token is used to vote and decide on the outcome of ARCx Improvement Proposals (AIPs).&#x20;

For more information, see [ARCX Token](protocol/arcx-token.md).

### Who is behind ARCx?

We are a team of product builders who believe that on-chain reputation will transform decentralized economies for the better. Come join us on [Discord](https://discord.gg/arcx) to learn more.

***
