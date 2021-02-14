---
description: An overview of how liquidations work in ARCx
---

# Liquidations

With the ARCx smart contracts, liquidations are simply the result of the protocol recalling any outstanding debt another user owes the protocol. Let's take a simple example:

1. The price of ETH is $100
2. Bob deposits 1 ETH into ARCx. The minimum c-ratio is 200%.
3. Bob then mints 20 STABLEx \($100/20 = 500% c-Ratio\)

Now, if the price of ETH drops to $40 then Bob's c-ratio is at the boundary of 200%. Below this point his collateral will need to be sold in order to cover for the debt which he owes the protocol. 

Let's supposed the price of ETH now drops to $30 meaning his c-ratio is 150% \($30/20\). The system will require:  
  
a\) Bob to add more collateral so the 200% c-ratio is maintained  
b\) Bob to repay his STABLEx debt to be in-line with his c-ratio  
c\) A liquidator to repay his STABLEx debt and in return acquire his collateral at a discount

In the case of a liquidator coming in, the following things will occur:

1. The liquidator will be able to acquire the user's collateral at a discount to the current price on-chain
2. ARCx will sell the collateral \(priced at discount\) to cover the user's outstanding debt and also sell a bit extra to make sure that there is a safety buffer before more liquidations occur
3. A certain portion of the **profit** from liquidation proceeds will go the the ARCx protocol

Only the portion of debt that is underwater is sold for collateral, the entire position will not be liquidated.

If you'd like to plug in your own numbers about how liquidations work, you can copy this spreadsheet and plug in your own numbers: [https://docs.google.com/spreadsheets/d/1S3eiNFz2JXqxI6pxUoFhjkucLdp7ySDj9B-kbnrniAU/edit?usp=sharing](https://docs.google.com/spreadsheets/d/1S3eiNFz2JXqxI6pxUoFhjkucLdp7ySDj9B-kbnrniAU/edit?usp=sharing)



