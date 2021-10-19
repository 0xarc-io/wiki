# How the Credit Score is Used

#### Example Relating Credit Score to Lending Collateral Ratios

The moving pieces involved in utilizing the DeFi Passport Credit Score are best visualized (below) with a concrete example: consider a single collateralized account, called here a ‘vault,’ with a dynamic collateral ratio set by the vault owner’s DeFi Passport Credit Score. In this case, the **Vault **(which contains collateral + user’s holdings), passes a set of numbers to a smart contract 'assessor.' The **Assessor **will request the user’s credit risk on a scale from 0 - 999 from the Credit Score. This score will then be 'mapped' onto a continuous distribution relevant for modifying the Vault conditions through a function called the **Mapper**. The result is then returned to the Vault in order to return the user’s specific collateral ratio.&#x20;

![Visual of DeFi Passport Credit Score Components](https://lh5.googleusercontent.com/DVHivm1XDI5My\_wzlzUwWPBC5AYkJiYDfgkDT9Kx5VBRSrLCmKKTzq9KFTt0aAvgs1mp\_OX01L1inTzIvfEuuChnVd3A8LMVq238ClLWB\_Nxu\_HLu0VhPSY2oRLmx5uZm-EiqNi4)

Note the DeFi Passport Credit Score is not a frozen number; it can be updated as needed to provide the most relevant information and a dynamic collateral ratio. This example demonstrates how the DeFi Passport Credit Score in particular adds value to on-chain lending protocols, but this process  can be generalized to be integrated with any range of DeFi protocols and their relevant parameters.
