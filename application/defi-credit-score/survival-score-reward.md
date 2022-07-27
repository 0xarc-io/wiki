# Survival Score Reward

### Introduction

The Survival Score Reward evaluates a borrower’s ability to avoid liquidations relative to the rest of the market, rewarding or subtracting points proportional to the “liquidation density” on a given day. Unlike the Daily Score Reward, which looks only at the previous 120 days of borrowing experience, the Survival Score Reward considers the borrowing experience of a wallet address over its entire lifetime. A borrower with previous experience on a selection of third party borrowing platforms will have a DeFi Credit Score between 0 and 300 based on this Score component alone. The Survival Score Reward therefore establishes the minimum bound for the DeFi Credit Score, where the only way a borrower can reach 999 is to borrow on ARCx (by virtue of the Daily Score Reward).

### **Score design principles**

{% hint style="info" %}
By looking at how well a borrower “survives” periods of high volatility, we can calculate a propensity for them to avoid liquidation in the future. A borrower who has demonstrated they can survive market downturns will score higher
{% endhint %}

The rules of the Survival Score Reward should reflect the following:

* A **good borrower** is one who:
  * Avoids liquidations during periods of high volatility.
  * Recognizes that their position may be in danger and reacts appropriately to avoid liquidation.
* A **bad borrower** is one who:
  * Does not avoid liquidation during periods of high volatility.
  * Does not recognize that their position is in danger and fails to act in a timely manner to avoid liquidation.

Additionally, the following points are taken into consideration:

* A borrower who has been liquidated previously should not score as high as a borrower who has never been liquidated. The top reward should be given to the borrower who has never been liquidated.
* The impact of a liquidation is dependent on the market. We want to reward borrowers who avoid liquidation in uncertain markets more than borrowers who avoid liquidation in strong markets. This is almost counter-intuitive, since sudden market crashes catch borrowers off-guard, while liquidating in a bull market seems like a borrower being careless. However, we want to recognize borrowers who avoided liquidation when many others did not. This means weighing liquidations in falling markets more heavily than liquidations in strong markets.
* A borrower must have been borrowing to be awarded any points. Hence, top scoring borrowers are guaranteed to have been borrowing the longest. This works to reward experience.

### Liquidation density

{% hint style="info" %}
“Liquidation density” is a key metric used to calculate the Survival Score Reward, and is based on the amount of liquidations that occur on a given day.
{% endhint %}

The liquidation density is defined as follows:

First, we calculate the number of liquidations on each day over the history of a given 3rd party platform (in the example below we show Aave V2 liquidations on Ethereum).

![](<../../.gitbook/assets/Active borrowers and liquidations.png>)

We can now define “liquidation density” using a centered moving sum of the liquidation count over 7 days. It is centered to account for eminently approaching liquidations and reward users who risk-adjust prior to a market downturn. These values are normalized to the range \[0, 1].

![](<../../.gitbook/assets/Liquidation density.png>)

The liquidation density is defined separately for each 3rd party data source.

### Reward Calculation

This liquidation density can be used to construct a points system. On any day, a Borrower is rewarded with points proportional to the liquidation density if they **do not** get liquidated, and lose points proportional to the liquidation density if they **do** get liquidated on that day.

Mathematically, the reward is constructed as follows.

Define the “**liquidation density**”, $$L(t)$$, at any point in time, $$t$$, as a value between \[0, 1]. Let $$i$$ be an index denoting the date. So, $$i=0$$ corresponds to the starting date of the calculation ($$t_0 = t_{i=0} = 17/12/2020$$ in the figure above). So, $$L_i=L(t_i)$$ is the liquidation density on the date $$t_i$$.

Next, we define a “**liquidation index**” as a Boolean value for whether the borrower was liquidated on the date $$t_i$$:

$$
\lambda_i=   \left\{\begin{array}{ll}      1  & \text{borrower liquidated at } t_i \\   
\\   0  & \text{borrower not liquidated at } t_i \\\end{array} \right.
$$

Similarly, we define an “**eligibility index**”, as a Boolean showing whether the borrower was borrowing sufficient amounts of debt on day $$t_i$$. The threshold for this is set to $500:

$$
\sigma_i=   \left\{\begin{array}{ll}      1  & \text{debt} \ge \$500\text{ at } t_i \\   
\\   0  & \text{debt} \lt \$500\text{ at } t_i \\\end{array} \right.
$$

Then we calculate the **daily impact**, $$I_i$$, as:

$$
I_i = \sigma_i L_i - 2\omega \lambda_i (L_i+\epsilon)
$$

The first term is the “positive” impact the borrower receives for borrowing on day $$i$$. The second term is the “negative” impact the borrower receives for being liquidated on day $$i$$.

In the above equation, $$\epsilon$$ is a a scalar added to the liquidation density in the negative component. This ensures the borrower will always be penalized for a liquidation, even when there has been no other liquidations in the market. We are using $$\epsilon=0.5$$.

The constant $$\omega$$ represents the width of the rolling window used in the sum of liquidation counts. In the present case, $$\omega=7$$.

The figure below may be helpful in understanding the magnitudes of the two components in the above equation (note the different y axis scales of the two panels).

![](<../../.gitbook/assets/Scoring system.png>)

We then compute the sum of the daily impact over all days in the past

$$
S=\sum_i I_i
$$

This method satisfies the following:

* A more experienced borrower (held debt for longer) has the potential to grow a higher score.
* Liquidations negatively impact the total. The larger the density of liquidations at the time of liquidation, the larger the impact of that liquidation. Conversely, avoiding a liquidation during these periods rewards the borrower more.
* The more “liquidation peaks” the borrow survives, the higher their score will be. A borrower who only survives one peak will score lower than a borrower who survives two, and so on.

A borrower receives a separate score for each 3rd party lending platform they have borrowed on. This is limited to platforms we have so far indexed. So to compute their final Survival Score, we combine the individual scores to a value between 0 and 300. This Survival Score is then added into the DeFi Credit Score.

### Data sources

{% hint style="info" %}
The Survival Score Reward uses borrowing data from third party platforms
{% endhint %}

For information on which third-party lending platforms and assets we index, see [data sources](survival-score-reward.md#data-sources).
