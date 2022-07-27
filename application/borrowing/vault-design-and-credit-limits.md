# Vault design and credit limits

### Introduction

ARCx Credit allows Borrowers to realize better capital efficiency in DeFi through serving dynamic maximum LTV ratios based on the DeFi Credit Score. We have implemented a three-tiered vault design, with each collateral asset having three distinct vault options distinguished by the range of max LTVs offered, the minimum Score required to access the vault, and the maximum credit limit a borrower can access (regardless of their deposited collateral).

In this section, we explain the concepts introduced here in more detail.

### Vaults

Every collateral type on ARCx (e.g. Wrapped Ethereum) is split into three different vaults. The key difference between these vaults is the amount of capital efficiency that can be realized, or in other words, the maximum loan-to-value which can be used before liquidation.&#x20;

![Borrow vaults table showing WETH vaults A, B and C.](<../../.gitbook/assets/Vaults table.png>)

Capital efficiency is unlocked by mapping the DeFi Credit Score with a range of maximum LTV values for a given vault. A borrower with a Score of 0 can only reach a max-LTV at the lower bound for the vault. A borrower with a score of 999 can reach a max-LTV at the upper bound of the vault. So for example, a borrower with a score of 0 will have their position in the WETH-A vault liquidated at a max-LTV of 80%, while a score of 999 will only be liquidated at a max-LTV of 90%.

### Score threshold

Access to vaults are determined by the DeFi Credit Score, with a “Score Threshold” showing what score is required before a vault will become available to use. As borrowers build their Score, the higher-tiered vaults will become available (or become unavailable in the case of a Borrower’s DeFi Credit Score going down below the Score Threshold). By default, everyone has access to the “A” vault, as it has a score threshold of 0+.

Should a borrower’s Score fall below the score threshold, they will be unable to borrow more until their score returns to the required level. In this situation, borrowers will be limited to deposit, withdraw or repay functionality from that vault.

### Credit limits

The credit limit is the maximum amount of debt a borrower can take, regardless of their DeFi Credit Score. The system decomposes the global credit limit into multiple individual, independent credit limits that are applied on a vault-by-vault basis. Each vault is issued a credit limit, and is entirely independent of the others.

The reason for introducing a credit limit (rather than allowing a borrower to simply take as much debt on as is allowed by their collateral value and maximum LTV) is to limit the losses born through unprofitable liquidations. This system allows us to offer borrowers flexibility in how they structure their loans while providing ARCx a higher degree of freedom in exposing ourselves to different types and sources of risk.

Beyond the beta, vaults will have a dynamic credit limit which will change as the borrowing history and DeFi Credit Score change. However, for the Beta Release, we have implemented a static credit limit of $10,000 for the WETH-A vault, $10,000 for WETH-B and $1,000 for WETH-C.

For more information, see [Profit model](../../risk-and-infrastructure/risk-management/).
