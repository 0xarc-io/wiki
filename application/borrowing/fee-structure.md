# Fee Structure



| Collateral | Borrow fee | Interest rate | Liquidation fee |
| ---------- | ---------- | ------------- | --------------- |
| WETH       | 0.2%       | 2.5%          | 10%             |

**Definitions**

* The borrow fee is a pro rata fee taken at each borrow event. The fee is added to the outstanding debt and is paid off when the Borrower makes their first repayment.
* The interest rate is the annualized percent your debt will increase each year compounded continuously. Some of the interest paid is returned to the supply pool (90%) while the rest is kept by ARCx.
* The liquidation fee is the discount liquidators get when purchasing collateral flagged for liquidation. The liquidation revenue is split between the liquidator and ARCx according to the _liquidationArcFee_. In the case of self-managed liquidations, 100% of revenue is kept by ARCx. This revenue is then fed back into the supply pool to benefit suppliers.
