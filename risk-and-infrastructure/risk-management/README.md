# Risk management

Lending money in DeFi is inherently risky, particularly when Borrowers are anonymous and suffer no real-world consequences to defaulting on their loans. To navigate this risk, conventional DeFi lending platforms generally require all loans to be over-collateralized regardless of who the Borrower is. In doing so, Borrowers are incentivized to repay, or else the collateral will be sold on their behalf with a penalty. ARCx Credit, on the other hand, treats every Borrower as an individual, and extends personalized collateralization requirements based on the DeFi Credit Score.

As Borrowers improve their DeFi Credit Score and borrow at increasingly higher LTV ratios, ARCx Credit exposes itself to a greater chance of losses from unprofitable liquidations. It is important to note that even over-collateralized positions (i.e. where LTV is less than 100%) can still become under-collateralized by the time of liquidation due to a rapidly falling collateral price, the delay of the liquidator, and slippage. In developing the ARCx Credit product, it was therefore important to appropriately model and manage risk in order to control for losses born through unprofitable liquidations.

This section covers:&#x20;

1. [Inflows and outflows](inflows-and-outflows.md)
2. [Design considerations](design-considerations.md)
3. [Control parameters](design-considerations.md)
4. [Profit modeling](control-parameters.md)
