# Inflows and outflows

### Inflows

ARCx Credit is a lending platform, where users can deposit collateral and borrow stablecoins from a lending pool. In return for facilitating this transaction, Borrowers are charged fees on their debt (an interest rate and a borrow fee). A portion of these fees are added back into the lending pool, increasing the value of the Lender’s contribution, while another portion is kept by ARCx Credit, generating revenue which is used to fund development and growth.

The table below summarizes the revenue sources of ARCx Credit

| Revenue source  | Description                                                                                                                                                                                                                                                      | Beta parameters |
| --------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------- |
| Interest rate   | The main source of revenue for ARCx Credit is the interest rate on loans. ARCx Credit facilitates the lending of debt to Borrowers who lock up collateral in our vaults, and in return, Borrowers must pay interest on their debts, much as they would in TradFi | 2.50%           |
| Borrow fee      | The borrow fee is a pro rata fee taken at each borrow event. The fee is added to the debt and is only paid back when the Borrower repays for the first time                                                                                                      | 0.20%           |
| Liquidation fee | During a liquidation event, the Borrower’s collateral is sold at a discount to a liquidator in return for repaying a Borrower’s debt                                                                                                                             | 10.00%          |

The table below summarizes how revenue is shared between ARCx Credit, the Lenders and the Liquidator

| Revenue source  | Retained by ARCx Credit | Retained by lenders | Retained by liquidator |
| --------------- | ----------------------- | ------------------- | ---------------------- |
| Interest rate   | 10%                     | 90%                 | n/a                    |
| Borrow fee      | 10%                     | 90%                 | n/a                    |
| Liquidation fee | 50%                     | n/a                 | 50%                    |

### Outflows

Liquidations can be a source of both revenue and loss depending on the LTV ratio of the position at the time of liquidation. When the LTV is sufficiently below 100%, the liquidation yields revenue without loss, with value extracted from the Borrower and paid to the liquidator and the protocol.

For LTV values close to or above 100% (i.e. the outstanding debt is similar in value to the collateral backing it), losses can be incurred to the protocol through the accumulation of toxic debt. The liquidation mechanism must always compensate the liquidator for performing the liquidation. Usually this compensation comes out of the Borrower’s excess collateral in the case of an over-collateralized loan. If there is not excess collateral to cover both the debt and the liquidators compensation, then the offset is taken from the pool, representing toxic debt.
