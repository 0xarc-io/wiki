---
description: A work in progress for directly interacting with ARC contracts via Etherscan
---

# Direct Contract Interaction

## Get Exact Debt and Balance

Read Contract - **getPosition\(\)**   
  
Response:

```
  tuple :  Address
  val1
  val2
  val3
  Collateral Amount
  val5
  Debt Amount
```

## Open / Borrow / Repay / Liquidate 

1. Get Exact Debt and Balance from above instructions.
2. Get Vault\_ID from "My Positions" page "Position \#" column.   
3. Write as Proxy - **2. operateAction\(\)**
   1. This takes fields \(operation, params\). 
      1. See below for how they are defined.
      2. Make sure assets have been approved in UI for now  \(etherscan instructions to come\)

```bash
operation values:
    0 : Open Position
    1 : Borrow
    2 : Repay
    3 : Liquidate
    
params:
    [Vault_ID,Amount1,Amount2]
        // Must be in square brackts
        // No spaces
        // All numbers in quotes
        // Vault ID normal size, not in WEI
        // Both amounts in WEI
```



> Repay Example:   
>     operateAction\(2, \[Vault Number, Repay Amount, Withdraw Amount\]\)
>
> Borrow Example:   
>     operateAction\(1, \[Vault Number, Deposit Amount, Borrow Amount\]\)
>
> With Values Example for Repay 1 LINK-USD, Withdraw 1 LINK:  
>     operation: 2  
>     params: \["99999","1000000000000000","1000000000000000"\]







