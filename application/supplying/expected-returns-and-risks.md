# Expected returns and risks

### Fees

In return for supplying assets to Borrowers, Lenders will receive a portion of fees generated on the platform. Currently, 90% of the interest and borrow fees are returned to Lenders, while 10% goes to ARCx to fund further development and growth.

### Risks

The profit earned from a Borrower is equal to the net revenue earned from that Borrower minus the losses they incur from unprofitable liquidations. Revenue is earned from interest, borrow fees and liquidations, while losses are sourced purely from liquidations.

For LTV values close to or above 100% (e.g. for a user with a Score of 999 borrowing in the WETH-C vault), a liquidation event may result in toxic debt (i.e. where the value of the sold collateral is less than the debt outstanding). The liquidation mechanism must always compensate the liquidator for performing the liquidation. Usually this compensation comes out of the Borrower’s excess collateral in the case of an over-collateralized loan. If there is not excess collateral to cover both the debt and the liquidators compensation, then the offset is taken from the pool, representing toxic debt.

Note that in the case of a 100% LTV liquidation, value is removed from the supply pool and sent to the ARCx fee collector. However, ARCx can return the liquidated funds to the pool to cover the loss in value, and thus the system as a whole may break even.
