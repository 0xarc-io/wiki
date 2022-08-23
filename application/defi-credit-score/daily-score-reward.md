# Daily Score Reward

The Daily Score Reward evaluates your “borrow usage” (current LTV as a percentage of max LTV) on ARCx Credit vaults over the prior 120 days relative to a “responsible” borrower archetype and rewards points according to a “Rewards Curve” on a daily basis. In our current iteration, the number of points earned each day peaks when a position is held at 60% borrow usage, and tapers off toward the lower (more conservative) or higher (more aggressive) ranges of the risk curve. By aligning the growth of the Credit Score with borrow usage, we aim to discourage excessive risk exposure, and by extension, mitigate the risk to the protocol and to lenders.

![Position Summary card showing a borrower with an “optimal” position.](<../../.gitbook/assets/Position Summary Card.png>)

The design of the Daily Score Reward aims to satisfy the following outcomes:

* Users who borrow too close to their limit (borrow usage close to 100%) are risky and should not given a high score.
* Users who borrow only a small fraction of their capacity (low borrow usage) are not borrowing efficiently and should not be rewarded with a high score.
* Users who borrow efficiently, but maintain appropriate risk levels are the ideal borrowers. These users should maximize their score.

To explain this further, let’s break down the Daily Score Reward.

### **"Borrow usage"**

Borrow usage refers to your current LTV as a percentage of maximum LTV, where 100% triggers a liquidation event for a position.

Borrow usage is shown prominently in the application. Firstly, the Position Summary card shows aggregate borrow usage across all active vaults. Secondly, the Borrow Vaults table shows borrow usage for each individual active vault.

![Borrow dashboard with two active vaults. The Position Summary card shows aggregate borrow usage across the two vaults, and the Borrow Vaults table shows the individual vault-level borrow usage values.](../../.gitbook/assets/Dashboard.png)

### **"Optimal borrower"**

{% hint style="info" %}
ARCx defines the “optimal borrower” as someone who maintains 60% borrow usage across their active positions.
{% endhint %}

The shape of the Rewards Curve, including the optimal borrow usage and the amount of drop-off left or right of the optimal point, are parameters set by the Risk function. In our current iteration, the choice of 60% was based on an analysis of experienced stablecoin borrowers on Compound Finance who use ETH as collateral (i.e. it represents a position that balances efficiency with risk exposure given the volatility of ETH)

In this analysis, we found those holding over $1K in debt tend to manage between 50% and 60% of their maximum loan-to-value (LTV). This was further explained through user research, where we found that experienced borrowers with larger loans viewed this range as representing a balanced “safety buffer” for their collateral.

![](<../../.gitbook/assets/Untitled (1).png>)

ARCx asserts that a borrow usage of 60% reflects someone who borrows efficiently, but maintains appropriate risk levels. To implement this assertion we reward points to users based on a defined “Rewards Curve”.

### **"Rewards Curve"**

{% hint style="info" %}
The Rewards Curve determines the number of points allocated at different borrow usage levels
{% endhint %}

The Daily Score Reward is calculated by mapping the borrow usage to a score impact. The mapping is performed using the “Rewards Curve” shown below

![Rewards Curve showing borrow usage (%) across the x-axis and the points multiplier on the y-axis. ](<../../.gitbook/assets/Borrow usage multiplier.png>)

The Rewards Curve is defined using the following base equation:

$$
kxe^{-kx^2}
$$

Specifically, the equation for the shape of the curve is:

$$
F=\left\{\begin{array}{ll}      \frac{\beta-x}{\beta- P}e^{-\frac{1}{2}(\frac{\beta-x}{\beta-P})^{2}+\frac{1}{2}}  & x\le\beta \\   
\\   0 & x>\beta \\\end{array} \right.
$$

Where

* $$x$$ is the borrow usage value (0-1)
* $$\beta$$ is the borrow usage value at which the multiplier becomes zero (90% in the above), this is the “Critical Point”.
* $$P$$ is the borrow usage value of the peak (60% in the above), called the “Optimum Point”.

This relation is clipped at 0 for borrow usage values above $$\beta$$. This means that a user with a position above this value will not gain daily improvements to their credit score.

The relationship between borrow usage and Credit Score growth is surfaced prominently in the application itself.

![Credit Score and Position Summary cards showing the relationship between borrow usage and the growth of the DeFi Credit Score.](<../../.gitbook/assets/Score + Summary.png>)

On the Position Summary card, borrowers can see their borrow usage and how quickly their credit score is expected to grow. A personalized suggestion below the borrow usage bar will display a message guiding the borrower to optimize their position to maximize the growth of their credit score. To action this suggestion, the borrower would need to adjust their debt (either repay or borrow), or their collateral (either deposit or withdraw). On the Credit Score card, borrowers can see their current Credit Score, and the daily score impact over the past 24 hours. A line chart behind the Credit Score card shows how a borrower’s Score has changed over time.

To illustrate the connection between Borrow Usage and the growth of your DeFi Credit Score, the borrow usage bar is broken into 5 segments that denote how their borrowing position will impact the growth of their Credit Score. The segments and their proportions are as follows: “Not growing” (0%), “Slow” (>0% - 25%), “Moderate” (25% - 50%), “Optimal” (50% - 70%), “Slow” (70% - 90%), and “Not growing” (90% - 100%).

### **"Past 120 days"**

{% hint style="info" %}
Only borrowing experience within the last 120 days are considered when calculating the Daily Score Reward component
{% endhint %}

The Daily Score Reward only consider borrowing behavior within the last 120 days. This means a Borrower has to continually borrow or their score will go down over time. However, the Daily Score Reward is designed to allow good Borrowers who maintain the optimal borrow usage to reach the top score of 999 within 120 days, even if they start with a score of 0.

The selection of 120 days is based on the following considerations:

* The mark of a reliable Borrower is how well they manage debt through tough market conditions. Historically, the price of Ethereum has never made it more than approximately 2 months without undergoing a crash of more than 10%. As such, we want to ensure that all borrowers who have reached the top score have experienced at least some market volatility in order to gauge how well they borrow.
* We aim for a compromise between building an engaging Credit Score that the user can grow in a reasonable amount of time, and a score which is not too volatile so a borrower can expect their Score not to change too much day to day.

With these considerations, we find a 120 day window to be appropriate. In our current implementation, we define the Score such that the optimum borrower reaches a score of 999 exactly within the window (from a starting Score of 0), and so the optimal daily impact is $$999/120=8.325$$ points per day.

### **"Daily basis"**

{% hint style="info" %}
The daily score reward is calculated by assessing borrow usage at the end of each hour, and it is updated on-chain daily.
{% endhint %}

Hourly granularity was chosen because it allows us to measure the borrowers behavior across a day. We award points to the credit score every hour and sum those points over each day to calculate the daily impact.
