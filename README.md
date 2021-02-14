# Introduction

## **Background**

ARCx is a synthetic asset protocol that unlocks the liquidity of your interest earning assets through our native stable-coin STABLEx. 

Current stable coin designs generally fall within a couple of broad categories:

* **Centralised Services** such as USDC and USDT offer strong protection to users as tokens are backed 1:1 by USD. However risks include centralisation risk and intervention from governments or central governing bodies
* **Elastic Supply Coins** usually involve some form of rebasing mechanism \(ESD, Ampleforth\) however aren't collateral backed. There is the potential scenario for loss in confidence which means that peg is unable to be maintained. 
* **Over-collateralised Coins** such as MakerDAO and SNX create confidence in the coin however isn't a perfect scenario given it's inability to maintain a stable peg. Additionally over-collateralised coins are highly capital inefficient 

## **STABLEx**

STABLEx is a stable coin that takes the learnings from all of the various projects listed above to create a more efficient stable coin product that is able to maintain a tight peg. It has the following characteristics:

1. **Partial Collateral**: the system as a whole will be partially collateralised which will improve on the deficiencies of Elastic Supply Coins and provide confidence in maintaining the peg
2. **Governance Controlled Variables**: from algorithm stable coin experiments we have seen that a fully algorithmic coin does not maintain a tight peg yet. As such the design currently allows for governance to control and update the various levers. This will allow for faster learnings on how to maintain the peg

### Key Levers

More details will be outlined in the Core Concepts however at a high level the following are the levers governance has control over

1. **Savings Rate**: the amount of STABLEx that is created and sent to holders of STABLEx \(seignorage concept taken from ESD, Basis Cash etc\)
2. **Interest Rate**: the interest rate is how much minters will be paying on their debt \(concept from MakerDAO\)
3. **Collateral Ratio**: this is the amount of collateral that is required in the vault. The lower the number the higher leverage

Try the app on main-net at: [http://app.arcx.money](https://app.arcx.money)

