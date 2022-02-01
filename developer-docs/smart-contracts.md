---
description: Using ARCx scores to make data-driven decisions on-chain.
---

# 🤖 Smart Contracts

### Introduction

The ARCx infrastructure is built on [Merkle trees](https://www.investopedia.com/terms/m/merkle-tree.asp) to maintain proper security and scalability standards. For those who are new to Merkle trees/Hash trees, here's a refresher on a few important terms:

* **Merkle leaf:** The leaf of a Merkle Tree. Leaves are hashed together to create a Markle tree. In our context, each leaf represents a score and has the following format:

```
{
    "account": "0x123...456",
    "protocol": "0x617...000",
    "score": "175",
}
```

| Property   | Description                                                                                                                                                                                   |
| ---------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `account`  | The wallet address associated with this score.                                                                                                                                                |
| `protocol` | The byte32 encoded representation of the score name. This format is enforced for memory efficiency. The `protocol` in simply the `byte32` encoded value of a score name, e.g. `arcx.loyalty`. |
| `score`    | The quantification of this score. This must be a non-negative value within the scope of a [BigNumber](https://docs.ethers.io/v5/api/utils/bignumber/).                                        |

* **Merkle root:** Is the combined hash of all the elements in a Merkle tree. Our contracts continuously update their roots as new scores and addresses are added.&#x20;
* **Merkle proof**: An array of hashes that when combined with a Merkle leaf, verifies the integrity  said leaf. If combining the leaf and proof corresponds to the root published on-chain, the leaf is considered legitimate and ready for on-chain use.

### Using a Score in a Smart Contract

To verify a score, fetch the Score Proof you want from [our API](verifying-passports.md#get-scores-address-score-score-proof)\*.

_\*Drop the `metadata` attribute if its included\*_

Example of a Score Proof:

```
{
    "account": "0x123...456",
    "score": "175",
    "protocol": "0x617...000",
    "merkleProof": [
        "0x111...111",
        "0x222...222",
        "0x333...333",
        ...
    ]
}
```



Pass your Score Proof to any smart contract to verify and use it on-chain. Here's an example on how to handle an `arcx.loyalty` score over `50`:

_\*Developer tip: Feel free to import our_ [_npm package_](https://www.npmjs.com/package/@arcxgame/contracts) _to easily manage ABI's_

```
...

import { ISapphirePassportScores } from "@arcxgame/contracts/contracts/sapphire/ISapphirePassportScores.sol";
import { SapphireTypes } from "@arcxgame/contracts/contracts/sapphire/SapphireTypes.sol";

...

contract ExampleContract {

    ...
    
    // Address of ARCx SapphirePassportScores contract
    ISapphirePassportScores public passportScores; 

    // Score that is required, e.g. 'arcx.loyalty' encoded into bytes32 
    bytes32 private magicProtocol = 0x617263782e6c6f79616c74790000000000000000000000000000000000000000
    ...

    constructor(address _passportScoresAddress) {
        passportScores = _passportScoresAddress;
    }

    ...
    
    function doSomeMagic(SapphireTypes.ScoreProof _scoreProof){
    
        require (
            _scoreProof.protocol == magicProtocol,
            "This score is not an arcx.loyalty score!"
        );
    
        // Returns true if valid, reverts when invalid
        passportScores.verify(_scoreProof); 
        
        if (_scoreProof.score > 50) {
            // Do something magical knowing score is greater than 50!
        }
    }
    
    ...
}
```

### Help

If you have any questions or suggestions, we'd love your input on our [discord server](https://discord.com/invite/skwz6je).\
\
Happy building! ノ
