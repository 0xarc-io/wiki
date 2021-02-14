# Risks

## Liquidation Risk

If the price of an stablecoin drops, you will most likely be liquidated by a liquidator bot. Depending on the collateral type you're using the penalty for this liquidation will be variable. For yield bearing stablecoins, this penalty is set at 2%.   
  
All prices are retrieved from Chainlink and by using the ARCx platform you are relying on the security of Chainlink's nodes. 

## Leverage Risk

STABLEx is a coin used to provide leverage, we recommend you exercise caution when using the platform and using leverage as the risks are still unknown. The price of STABLEx will most likely fluctuate based on the supply/demand for leverage. 

## Impermanent Loss

As the price of STABLEx fluctuates, when becoming a LP you may end up with a different composition of STABLEx or USDC. While the values of both tokens should be $1 there may always be variance.

## Contract Bugs

While we've done extensive testing, audits and reviews of the contracts there may always be a bug in the contracts that hasn't been found. Please do not deploy more than you can lose inside these contracts. 

V1 of ARCx was audited by Quantstamp: [https://github.com/arcxmoney/audits/blob/master/202009B4-d22c805-final%20-%20Report.pdf](https://github.com/arcxmoney/audits/blob/master/202009B4-d22c805-final%20-%20Report.pdf). The V1 contracts have successfully held over $2m over the course of 4 months with no exploits.  
  
V2 of ARCx was informally reviewed by Quanstamp as the V2 contracts build on the V1 contracts. The informal review will be linked here shortly. 

## Admin Key Risk

The ARCx team holds the admin key for the contracts which gives complete control of the contracts in order to pause the contracts or fix any issues that may arise. We plan to transition to governance when the platform becomes more mature/stable.



