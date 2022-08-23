# Vault design

We have implemented a three-tiered vault design, with each collateral asset having three distinct vault options distinguished by the range of max LTVs offered (”capital efficiency”), the minimum Score required to access the vault (”score threshold”), and the maximum amount of debt a borrower can access (”credit limit”).

### Vault A, B and C

Each collateral type has three associated vaults, named “A”, “B” and “C”.

* The “A” vault is available to every Borrower, and the range of max LTV values are set conservatively. For example, WETH-A offers between 80% and 90% max LTV, where a Score of 0 = 80%, and a Score of 999 = 90%.
* The “B” and “C” vaults offer comparatively higher max LTV values. For example, the WETH-B vault offers up to 95% LTV, and WETH-C up to 100% LTV.

![Borrow vaults table showing WETH vaults A, B and C.](<../../.gitbook/assets/Vaults table.png>)

### Capital efficiency

Capital efficiency describes the range of max LTV ratios that the vault offers depending on the user’s DeFi Credit Score. For example, a borrower with a score of 0 will have their position in the WETH-A vault liquidated at a max-LTV of 80%, while a borrower with a score of 999 will be liquidated in the same vault at a max-LTV of 90%. Because the DeFi Credit Score changes daily, so too will a borrower’s maximum LTV offered across different vaults. Additionally, while the “optimal” borrow usage for growing the DeFi Credit Score stays constant across vaults, the specific LTV that this borrow usage represents increases in higher tiered vaults.

### Score threshold

Score thresholds prevent access to higher-tiered (i.e. more capital efficient) vaults until the borrower achieves the minimum DeFi Credit Score required. By default, everyone has access to the “A” vault, as it has a score threshold of 0. Vaults “B” and “C” offer comparatively higher maximum LTV ratios, and are gated to lower risk borrowers who achieve Credit Scores above the thresholds set. Should a borrower’s Score fall below the threshold, they will be unable to borrow more until their score returns to the required level. In this situation, borrowers will be limited to deposit, withdraw or repay functionality from that vault.

### Credit limits

Credit limits create a ceiling to the amount of debt that an individual can borrow from a specific vault. Rather than allowing an unlimited borrow amount, the credit limit provides a way to limit the quantum of losses born through unprofitable liquidations, particularly for higher tiered vaults. This system allows us to offer borrowers flexibility in how they structure their loans while providing us a higher degree of freedom in exposing ourselves to different types and sources of risk.

To more explicitly tie borrower behavior with the amount of debt we feel comfortable extending, credit limits for an individual vault can be determined dynamically based on the amount a user has borrowed in other vaults. The current implementation of ARCx Credit imposes a static credit limit of $10,000 for the WETH-A vault, $10,000 for WETH-B and $1,000 for WETH-C. However, we are actively working to implement dynamic limits into the product shortly.&#x20;
