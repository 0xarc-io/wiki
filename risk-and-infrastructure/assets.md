# Assets

ARCx offers the following options for collateral and debt assets

### Collateral

| Vault name | Credit Score Entry Threshold | Asset            | Lower max-LTV bound | Upper max-LTV bound | Credit limit     | Liquidation discount | Interest rate | Borrow fee |
| ---------- | ---------------------------- | ---------------- | ------------------- | ------------------- | ---------------- | -------------------- | ------------- | ---------- |
| WETH-A     | 0                            | Wrapped Ethereum | 80%                 | 90%                 | Static ($10,000) | 10%                  | 2.5%          | 0.2%       |
| WETH-B     | 500 (temp)                   | Wrapped Ethereum | 85% (temp)          | 90% (temp)          | TBD              | TBD                  | TBD           | TBD        |
| WETH-C     | 750 (temp)                   | Wrapped Ethereum | 90% (temp)          | 100% (temp)         | TBD              | TBD                  | TBD           | TBD        |

### Debt

| Pool name | Supplied by ARCx |
| --------- | ---------------- |
| Pool A    | $80,000          |
| Pool B    | $15,000          |
| Pool C    | $5,000           |

Note, the A, B and C Pools correspond with the collateral vaults of the same name. Therefore, supplying to Pool A will lend assets to borrowers from Vault A (e.g. WETH-A)
